## 安装
	- https://claude-zh.cn/guide/getting-started
	- ### 下载
		- ```bash
		  curl -fsSL https://claude.ai/install.sh | bash
		  ```
		- 验证安装成功
		  ```bash
		  claude --version
		  ```
	- ### 使用第三方API Key
		- ```bash
		  vim ~/.bashrc
		  ```
		- 在最后加上：
		  ```bash
		  export ANTHROPIC_AUTH_TOKEN=<sk-key>
		  export ANTHROPIC_BASE_URL=<api_endpoint>
		  export API_TIMEOUT_MS=300000
		  ```
	- ### 启动测试
		- ```bash
		  claude
		  ```
	- ### 更新
		- ```bash
		  claude update
		  ```
		-