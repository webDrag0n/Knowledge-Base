## 从生成机制到未来认知架构的理论分析

过去数年，大语言模型的发展几乎完全建立在自回归（Autoregressive, AR）Transformer 这一统一范式之上。无论是 OpenAI 的 GPT 系列、Anthropic 的 Claude 系列，还是 Google DeepMind 的 Gemini 系列，其核心生成机制本质上都建立在同一个概率分解公式之上：

$$P(x)=\prod_{t=1}^{T}P(x_t\mid x_{<t})$$

即模型通过 next-token prediction 的方式，一个 token 接一个 token 地展开文本。过去几年，整个行业几乎默认接受这样一种隐含前提：语言智能的本质，就是足够大规模的序列预测；只要参数量足够大、数据足够多、上下文足够长，自回归 Transformer 就能够不断逼近通用智能。

然而，2025 至 2026 年间，以  Inception Labs Mercury 系列为代表的一系列扩散语言模型（Diffusion Language Model, dLLM）开始重新打开语言模型的架构空间。其真正重要之处，并不仅仅在于“生成速度提升”，而在于：语言模型的生成动力学（generation dynamics）第一次开始脱离严格的 token rollout 机制，从“顺序生成”转向“全局状态优化”。

传统自回归生成过程本质上是一条单向时间链：

$$x_1 \rightarrow x_2 \rightarrow x_3 \rightarrow \cdots$$

而扩散语言模型则更接近：

$$x_T \rightarrow x_{T-1} \rightarrow \cdots \rightarrow x_0$$

即从高熵状态开始，通过不断 refinement（精炼、去噪），逐渐收敛到最终文本状态。它不再强调“下一个 token 是什么”，而是强调“整个序列如何逐渐变得合理”。

这一变化表面上只是生成机制变化，但其深层意义其实是：语言模型开始从“序列生成器”转向“状态优化器”。

但也正是在这里，一个被媒体与市场宣传普遍忽略的问题开始出现：扩散模型虽然具备并行生成优势，但它几乎无法像自回归模型一样使用 KV Cache。而 KV Cache 恰恰是现代大语言模型能够实现高效长上下文推理与持续在线运行的核心基础设施之一。

事实上，如果不理解 KV Cache，就无法真正理解为什么自回归模型在工程上远比表面看起来更强。

Transformer attention 的计算本质上依赖 Query-Key 匹配：

$$QK^T$$

若每次生成一个 token 都重新计算整个历史上下文，那么生成长度为 n 的序列时，其复杂度会达到：

$$O(n^2)$$

甚至更高。然而 KV Cache 的出现彻底改变了这一问题。由于历史 token 的 Key 与 Value 在 autoregressive decode 中不会变化，因此模型可以缓存所有过去的 KV 状态。生成新 token 时，仅需计算新的 Query，并与历史 KV 做 attention，而无需重新计算过去 token 的 attention、MLP 与 hidden states。

因此，现代 AR LLM 在推理时并不是“每生成一个 token 就重新生成整个句子”，而更接近于“在已有认知状态上做增量更新”。这使得 AR 模型在长上下文场景中拥有极其重要的渐进优势。随着上下文增长，新增 token 的计算成本并不会线性重算整个历史，而只是增量扩展已有状态。

这一点实际上具有极深刻的认知架构意义。

因为 KV Cache 本质上不仅是工程优化，它实际上等价于一种“低成本持续工作记忆（persistent working memory）”。模型能够在时间轴上维持稳定的内部状态，并不断推进认知过程。这使自回归模型天然适合：
- 长链推理；
- 持续对话；
- Agent 循环；
- 工具调用；
- 长期记忆注入；
- 在线认知状态演化。
  
  而扩散模型在这里则面临一个结构性问题。
  
  扩散模型的生成过程并不是：
  
  $$x_t \rightarrow x_{t+1}$$
  
  而是：
- **“整个序列在不断变化”。**
  
  例如，第五步 refinement 的文本可能是：
  
  “the cat sits on the mat”
  
  第六步 refinement 则可能变成：
  
  “a cat was sitting on the mat”
  
  即 token identity 本身会不断变化。因此，过去步骤的 attention 状态无法稳定复用，因为：
- token 会改变；
- attention graph 会改变；
- hidden representation 会改变。
  
  于是，扩散模型很难天然建立类似 AR 的稳定 KV Cache。
  
  这一点意味着：扩散模型在每一步 refinement 中，更接近于对整个序列重新计算 attention。假设序列长度为 n，扩散步数为 k，则其理论复杂度更接近：
  
  $$O(kn^2)$$
  
  而 AR + KV Cache 在工程优化后，其实际 decode 复杂度更接近于低常数项的增量计算。
  
  这意味着，扩散模型虽然在 token/s 指标上可能非常惊艳，但这种指标本身具有很强误导性。因为 diffusion 往往一次 refinement 同时更新多个 token，因此“token/s”并不等价于“长期认知状态维护效率”。
  
  真正的问题在于：当 context length 持续增长时，会发生什么？
  
  对于自回归模型而言，长上下文虽然增加 attention 成本，但历史状态本身大体被冻结。模型只是在已有状态基础上不断推进，因此其认知过程具有“时间连续性”。
  
  而 diffusion 则更接近：
- **每一步都在重新优化整个状态场。**
  
  当 context 达到：
- 32k；
- 128k；
- 1M；
  
  甚至未来 agent 的长期 memory graph 时，diffusion 可能需要不断对整个认知状态重新 refinement。此时其计算量可能急剧膨胀。
  
  而这恰恰与未来 AI 的真实发展方向形成冲突。
  
  因为未来真正重要的 AI 场景并不是一次性问答，而是：
- 持续运行的 Agent；
- 长时间存在的 AI Companion；
- 机器人；
- 自动驾驶；
- 游戏 NPC；
- 科学研究 Agent；
- 长期自治系统。
  
  这些系统最重要的能力并不是“一次生成一段文本”，而是：
- **长时间维持连续认知状态。**
  
  换句话说，未来高级智能体更像：
  
  $$S_t \rightarrow S_{t+1}$$
  
  其中：
- memory；
- tools；
- goals；
- world model；
- plans；
- environment；
  
  共同演化内部状态。
  
  而这实际上更接近“状态推进系统（state transition system）”，而不是“一次性全局去噪”。
  
  这也解释了为什么自回归模型虽然理论上存在串行瓶颈，但在长期 cognition 场景中却仍然极具优势。因为 AR 的 hidden state 天然形成了一个时间连续的工作空间。它本质上更接近：
- RNN；
- 状态机；
- 工作记忆系统；
- 图灵机纸带推进。
  
  因此它天然适合：
- Chain-of-Thought；
- Recursive Reasoning；
- Tool Interaction；
- Agentic Planning；
- Sequential Execution。
  
  而 diffusion 更像一种：
- # **constraint satisfaction system。**
  
  它的目标更接近：
  
  $$x^*=\arg\max_x P(x)$$
  
  即直接寻找“整体合理状态”。
  
  这使它天然适合：
- 全局一致性优化；
- 多模态状态 refinement；
- 结构化生成；
- 并行候选生成；
- 高吞吐实时生成。
  
  但未必适合：
- 长链搜索；
- DFS/BFS；
- theorem proving；
- 持续 memory evolution；
- 长期在线 cognition。
  
  因此，目前越来越明显的一点是：未来 AI 很可能不会是“Diffusion 替代 AR”，而是形成一种分层混合认知架构。
  
  其中，自回归系统负责：
- 持续工作记忆；
- 顺序执行；
- 长链 reasoning；
- online cognition；
- tool loop；
- recursive state transition。
  
  而 diffusion 系统负责：
- 全局规划；
- latent workspace refinement；
- 多模态世界状态优化；
- 并行候选生成；
- 高层结构修正。
  
  换句话说：
- **AR 更像“认知轨迹”**
- **Diffusion 更像“认知场”。**
  
  这一点其实与人类高级认知非常相似。
  
  人类在做复杂工作时，并不是纯粹 token-by-token 思考。例如写论文时，人类会：
- 先形成模糊整体结构；
- 再不断修改；
- 调整章节；
- 重写局部；
- 全局优化一致性。
  
  这一过程非常像 diffusion refinement。
  
  但与此同时，人类在执行数学推导、代码调试、逻辑证明时，又会进入严格 sequential reasoning 模式。这更接近 autoregressive computation。
  
  因此，真正高级认知系统可能本来就同时包含：
- sequential cognition；
- global refinement cognition。
  
  从这个角度看，扩散语言模型真正重要的意义，也许并不在于“替代 GPT”，而在于：
- **它重新打开了认知架构空间。**
  
  过去几年，行业几乎默认：
  
  Transformer + AR + Scaling
  
  就是唯一道路。
  
  但 diffusion 的出现意味着：
- **智能未必必须建立在 token rollout 上。**
  
  未来的高级智能体，可能不是单向语言流，而是一个持续演化的动态认知状态系统。而在这个系统中：
- AR 负责时间连续性；
- Diffusion 负责全局状态优化；
- Memory System 负责长期人格与经验积累；
- World Model 负责环境预测；
- Symbolic Verifier 负责逻辑一致性。
  
  这可能才是真正接近“持续认知”的人工智能架构。
-
- ## 为什么资本趋之若鹜
- 真正让资本市场对  Inception Labs 感兴趣的，并不是“扩散模型可以生成文本”这件事本身。学术界过去几年已经有大量 Diffusion LM 工作，真正关键的是：它第一次让产业界看到了一种可能性——在未来 AI 的主要成本从“训练”转向“持续推理”之后，现有 autoregressive 架构可能会在经济性上逐渐触顶。
  
  过去几年整个行业的默认假设是：只要模型足够强，推理成本总可以通过工程优化解决。但现在越来越明显的一件事是，未来真正消耗资源的不是单轮 Chat，而是持续运行的智能体系统。Agent 不再是“输入一句话，输出一句话”，而是会持续运行几十秒、几分钟，甚至长期在线存在。它会不断：
- 更新内部状态；
- 检索记忆；
- 调用工具；
- 修改计划；
- 反思；
- 自我验证；
- 与环境交互；
- 与其他 agent 通信。
  
  这意味着未来 AI 的核心资源消耗，不再是“单次生成”，而是：
- **持续闭环推理。**
  
  而一旦进入这种模式，KV Cache 的优势会开始下降。
  
  很多人会误以为 KV Cache 是一种“永久有效”的加速机制，但实际上它成立有一个重要前提：
- **历史 token 不发生变化。**
  
  传统聊天场景中，这个前提成立。因为用户输入后，模型只是在尾部继续生成 token，过去上下文被冻结，因此：
- past key/value 可复用；
- hidden states 可缓存；
- attention 不需要重算。
  
  但真正的长期智能体并不是这样工作的。
  
  未来高级 agent 的内部状态很可能不是一个静态 token 序列，而是一个持续变化的认知状态空间。例如：
- 长期记忆会动态压缩；
- 工作记忆会不断重组；
- 历史推理链会被修改；
- 世界模型会更新；
- 计划树会重排；
- 多候选方案会被筛选；
- latent workspace 会持续 refinement。
  
  此时，“过去状态被冻结”这一假设开始失效。
  
  也就是说，真正复杂的 agent cognition 并不是：
  
  x_1 \rightarrow x_2 \rightarrow x_3
  
  而更像：
  
  S_t \rightarrow S_t'
  
  其中整个内部状态都在变化。
  
  一旦系统开始频繁修改历史状态，KV Cache 就会逐渐失去意义，因为 cache consistency 被破坏。过去缓存的 KV 已经对应不上新的状态结构。
  
  这是一个极其重要但目前行业讨论还不够充分的问题。
  
  实际上，长期运行 agent 的内部状态管理，很可能天然更接近 diffusion 的“整体状态 refinement”，而不是 autoregressive 的“时间推进”。
  
  这也是为什么 Inception 会引起资本市场高度关注。资本真正下注的不是“文本扩散”，而是：
- **后 KV-cache 时代的推理架构。**
  
  因为整个行业已经逐渐意识到，未来 AI 市场的决定因素不是：
- benchmark 分数；
- 参数量；
- pretraining scaling。
  
  而是：**inference economics。**
  
  谁能以最低成本维持最长时间、最多 agent、最大规模的持续认知系统，谁就拥有未来 AI 基础设施的话语权。
  
  这一点会直接改变市场格局。
  
  过去几年 OpenAI 的成功，本质上建立在：
- scaling law；
- GPU 集群；
- 大规模预训练。
  
  但未来智能体时代的核心竞争力可能变成：
- 推理成本；
- latency；
- 持续 cognition efficiency；
- memory update efficiency；
- online reasoning throughput。
  
  这是完全不同的竞争方向。
  
  资本市场对 Inception 感兴趣，根本原因是它第一次让人看到：
- **“推理层”本身也可能发生架构革命。**
  
  这意味着什么？
  
  意味着未来 AI 的护城河可能不再只是：
- 谁能训练最大的模型；
  
  而是：
- 谁能最低成本地运行百万级 agent；
- 谁能维持持续在线 cognition；
- 谁能支持实时世界状态更新；
- 谁能支撑长时间自治系统。
  
  而这恰恰是微软、xAI、英伟达这些公司真正焦虑的问题。
  
  因为现在行业已经开始发现一个现实：
- **GPT 类模型越来越像“高性能计算器”，**
- **但不太像“持续存在的认知系统”。**
  
  当前 autoregressive LLM 的核心优化方向，本质上仍然是：
- 单轮 response quality；
- benchmark；
- reasoning trace；
- instruction following。
  
  但未来 agent 需要的其实是：
- 长时间稳定运行；
- 持续内部状态更新；
- memory consolidation；
- 多任务调度；
- 世界模型维护；
- 自主循环。
  
  而一旦系统进入这种“动态内部状态持续修改”的模式，传统 KV Cache 会逐渐失效。
  
  这意味着什么？
  
  意味着现在 AR LLM 最大的工程优势，可能并不一定能延续到下一代认知系统。
  
  这也是为什么 diffusion LM 的意义不能只看“今天替代 GPT 没有”。真正的问题是：
- **当未来 agent 的内部状态不再是静态 token 序列时，**
- **AR 的核心工程优势是否还成立？**
  
  如果不成立，那么 diffusion 的并行优势会被重新放大。
  
  因为 diffusion 最大优势从来不是：
- 理论 FLOPs 更低；
  
  而是：
- **当无法有效 cache 时，**
- **diffusion 的并行 refinement 更适合 GPU。**
  
  这一点非常关键。
  
  现代 GPU 的真正优势是：
- 大矩阵；
- 高并行度；
- SIMD；
- batch refinement。
  
  而 autoregressive decode 恰恰是 GPU 最不喜欢的：
- 小 batch；
- 串行 token rollout；
- 高频 memory access；
- KV cache bandwidth bottleneck。
  
  所以今天 AR 的成功，很大程度上是依赖 KV Cache 在“静态历史上下文”条件下成立。一旦 agent 的 cognition 开始不断重写内部状态，这个条件就会逐渐崩塌。
  
  因此，未来智能体架构很可能会出现一个重要分化：
  
  对于：
- 静态长上下文；
- 普通聊天；
- 文档生成；
  
  AR + KV Cache 仍然极强。
  
  但对于：
- 动态 memory graph；
- 持续 cognition；
- 自主 agent；
- 多状态 workspace；
- 世界模型维护；
  
  diffusion 或其他 state refinement architecture 的优势可能开始显现。
  
  这里真正重要的一点是：
- **未来 AI 的核心单位可能不再是“token”，而是“状态”。**
  
  一旦认知系统的核心对象从 token sequence 变成 dynamic state field，很多今天围绕 autoregressive LLM 建立的工程假设都会失效。
  
  这对科研课题组意味着什么？
  
  意味着这是一个非常少见的窗口期。
  
  因为当前整个行业虽然已经意识到：
- AI 正在从 ChatBot 转向 Agent；
- AI 正在从单轮生成转向持续 cognition；
  
  但：**下一代认知架构还没有收敛。**
  
  这是最重要的机会。
  
  过去几年做基础模型，中小团队几乎没有机会，因为 scaling war 已经结束。但 diffusion reasoning、state-based cognition、agentic architecture 这些方向还远远没有定型。
  
  对于课题组而言，真正值得投入的并不是“训练一个自己的 Mercury”，而是：
- **研究未来认知系统中：****状态如何持续演化。**
  
  这包括：
- dynamic memory refinement；
- latent workspace；
- persistent cognitive field；
- diffusion planning；
- memory denoising；
- hybrid AR-diffusion cognition；
- self-modifying internal state；
- continual world model update。
  
  这些方向与传统 LLM benchmark 的竞争完全不同，更接近下一代 agent operating system。
  
  如果从创业角度看，也同样如此。
  
  现在继续做：
- chatbot；
- prompt wrapper；
- 普通 agent workflow；
  
  竞争已经非常激烈。
  
  但：**“低成本持续运行的大规模自治智能体”**
  
  仍然是几乎空白的市场。
  
  真正有价值的，不是一个“会聊天”的模型，而是一个：
- 能持续存在；
- 能长期维护内部状态；
- 能低成本运行；
- 能形成稳定人格与经验积累；
  
  的认知系统。
  
  而这一方向恰恰会迫使行业重新思考：
- KV Cache 是否仍然成立；
- token rollout 是否仍然合理；
- 是否需要 state-based cognition；
- 是否需要 diffusion-like refinement architecture。
  
  因此，对于课题组而言，我认为应该明确几点。
  
  第一，不应该把 diffusion LM 当成“文本生成新模型”来看，而应该把它视为：**下一代认知状态更新机制。**
  
  第二，不应该尝试与 OpenAI 正面拼基础模型，而应该切入：
- cognition architecture；
- memory evolution；
- agent operating system；
- persistent reasoning；
- dynamic internal state。
  
  第三，应该尽早建立：
- diffusion cognition；
- hybrid reasoning；
- state refinement；
- memory field；
  
  相关积累，因为这个方向现在仍然处于极早期。
  
  第四，如果考虑产业化，真正值得做的不是聊天产品，而是：
- **面向长期自治 agent 的低成本推理基础设施。**
  
  因为未来真正消耗 GPU 的，很可能不是用户聊天，而是：
- 数百万持续运行的智能体。