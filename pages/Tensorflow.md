- Tensorflow是 [[Google]]设计的一种 [[机器学习]]框架
- ## 安装
  id:: 631c2feb-bc55-4582-a044-4b7cc592ac49
	- 默认使用tensorflow将会安装tensorflow2，如需其他版本请标明如`tensorflow==1.15`
	  参考：[官方安装文档](https://www.tensorflow.org/install)
	- 前置要求：
		- 必须在系统中安装以下 NVIDIA® 软件：
		- [NVIDIA® GPU 驱动程序](https://www.nvidia.com/drivers) - CUDA® 11.2 要求 450.80.02 或更高版本。
		- [CUDA® 工具包](https://developer.nvidia.com/cuda-toolkit-archive)：TensorFlow 支持 CUDA® 11.2（TensorFlow 2.5.0 及更高版本）
		- CUDA® 工具包附带的 [CUPTI](http://docs.nvidia.com/cuda/cupti/)。
		- [cuDNN SDK 8.1.0](https://developer.nvidia.com/cudnn) [cuDNN 版本](https://developer.nvidia.com/rdp/cudnn-archive)。
		- （可选）[TensorRT 6.0](https://docs.nvidia.com/deeplearning/tensorrt/archives/index.html#trt_6)，可缩短用某些模型进行推断的延迟时间并提高吞吐量。
	- [[pip]]
		- 建议使用pip安装，成功率较高
		- ```bash
		  pip install tensorflow
		  ```
	- [[conda]]
		- Default installs support for both cpu and gpu
		- ```bash
		  conda install tensorflow
		  ```
	- ### 安装后报错处理
		- [TensorFlow libdevice not found](https://stackoverflow.com/questions/68614547/tensorflow-libdevice-not-found-why-is-it-not-found-in-the-searched-path)
		  collapsed:: true
		  `InternalError: libdevice not found at ./libdevice.10.bc`
			- **for Windows** user
			- **Step-1**
				- run (as administrator)
				- ```
				  conda install -c anaconda cudatoolkit
				  ```
				- you can specify the cudatoolkit version as per your installed cudaCNN /supported version ex:conda install -c anaconda cudatoolkit=10.2.89
			- **Step-2**
				- go to the installed conada folder
				- > C:\ProgramData\Anaconda3\Library\bin
			- **Step-3**
				- locate "**libdevice.10.bc**" ,copy the file
			- **Step-4**
				- create a folder named "**nvvm**" inside bin
				- create another folder named "**libdevice**" inside nvvm
				- paste the "**libdevice.10.bc**" file inside "libdevice"
			- **Step-5**
				- go to environmental variables
				- System variables >New
				- variable name:
					- > XLA_FLAGS
				- variable value:
					- > --xla_gpu_cuda_data_dir=C:\ProgramData\Anaconda3\Library\bin
				- (edit above as per your directory)
			- **Step-6**
				- restart the cmd/virtual env