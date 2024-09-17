- #大模型 #llm #工具
- Ollama为包括llama模型在内的大语言模型的部署与使用提供了极大便利
  [官方GitHub仓库](https://github.com/ollama/ollama)
- ## 下载安装
	- [linux平台下载](https://ollama.com/download/linux)，其他平台包括windows和macos
	  ```bash
	  curl -fsSL https://ollama.com/install.sh | sh
	  ```
	- 在配置好基本的 [[CUDA]] 和 [[CUDNN]] 环境的情况下安装完成即可直接使用
	- ### 升级
		- 如需升级，重复执行该命令即可
- ## 配置模型储存路径
	- 大模型需要较大储存空间，默认存储路径为：
	  ```
	  macOS: ~/.ollama/models
	  Linux: /usr/share/ollama/.ollama/models
	  Windows: C:\Users\%username%\.ollama\models
	  ```
	  参考：[faq - how-do-i-set-them-to-a-different-location](https://github.com/ollama/ollama/blob/main/docs/faq.md#how-do-i-set-them-to-a-different-location)
	- 系统安装盘往往存储资源较为宝贵，因此建议重设安装路径：
	  ```bash
	  systemctl edit ollama.service
	  ------------------------------
	  [Service]
	  Environment="OLLAMA_MODELS=<model storage path>"
	  ```
	- 请注意<model storage path>需要将该目录设为 `ollama:ollama`（用户组:用户） 所有，并将所有父目录设为所有用户可读+执行
	  ```bash
	  sudo chown -R <model storage path>
	  sudo a+rx <all parent folders>
	  ```
	- 完成后重启ollama服务
	  ```bash
	  systemctl daemon-reload
	  systemctl restart ollama
	  ```
- ## 下载与运行
	- ollama在找不到目标模型时会自动下载，因此直接运行`run`操作即可，注意模型参数量选择需要用小写`b`
	  ```bash
	  ollama run llama3.1:70b
	  ```
- ## 可选模型
	- [官方支持目录](https://ollama.com/library)
- ## 更多支持的操作
	- 参考：[官方GitHub仓库](https://github.com/ollama/ollama)
	- ### Create a model
	  `ollama create` is used to create a model from a Modelfile.
	  ```
	  ollama create mymodel -f ./Modelfile
	  ```
	- ### Pull a model
	  ```
	  ollama pull llama3.1
	  ```
	  > This command can also be used to update a local model. Only the diff will be pulled.
	- ### Remove a model
	  ```
	  ollama rm llama3.1
	  ```
	- ### Copy a model
	  ```
	  ollama cp llama3.1 my-model
	  ```
	- ### Multiline input
	  For multiline input, you can wrap text with `"""`:
	  ```
	  >>> """Hello,
	  ... world!
	  ... """
	  I'm a basic program that prints the famous "Hello, world!" message to the console.
	  ```
	- ### Multimodal models
	  ```
	  ollama run llava "What's in this image? /Users/jmorgan/Desktop/smile.png"
	  The image features a yellow smiley face, which is likely the central focus of the picture.
	  ```
	- ### Pass the prompt as an argument
	  ```
	  $ ollama run llama3.1 "Summarize this file: $(cat README.md)"
	  Ollama is a lightweight, extensible framework for building and running language models on the local machine. It provides a simple API for creating, running, and managing models, as well as a library of pre-built models that can be easily used in a variety of applications.
	  ```
	- ### Show model information
	  ```
	  ollama show llama3.1
	  ```
	- ### List models on your computer
	  ```
	  ollama list
	  ```
	- ### Start Ollama
	  `ollama serve` is used when you want to start ollama without running the desktop application.
	- ## Building
	  See the [developer guide](https://github.com/ollama/ollama/blob/main/docs/development.md)
	- ### Running local builds
	  Next, start the server:
	  ```
	  ./ollama serve
	  ```
	  Finally, in a separate shell, run a model:
	  ```
	  ./ollama run llama3.1
	  ```
-