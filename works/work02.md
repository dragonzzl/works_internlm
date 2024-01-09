# 作业2
### 1. 大模型以及InternLM模型介绍
	大模型：人工智能领域中参数数量巨大，拥有庞大计算力和参数规模的模型
	InterLM是一个开源的轻量级训练框架
	Lagent是一个轻量级、开源的基于大语言模型智能体框架
	浦语灵笔是基于书生浦语大模型研发的视觉语言大模型
### 2. InterLM-Chat-7B智能对话demo
**环境准备**  
进入 conda 环境之后，使用以下命令从本地克隆一个已有的 pytorch 2.0.1 的环境  
```
bash # 请每次使用 jupyter lab 打开终端时务必先执行 bash 命令进入 bash 中  
/root/share/install_conda_env_internlm_base.sh internlm-demo
```
然后使用以下命令激活环境  
```conda activate internlm-demo```  
并在环境中安装运行 demo 所需要的依赖。  

升级pip  
	```python -m pip install --upgrade pip```
安装包  
	```pip install modelscope==1.9.5
	pip install transformers==4.35.2
	pip install streamlit==1.24.0
	pip install sentencepiece==0.1.99
	pip install accelerate==0.24.1```
 
**模型下载**  
InternStudio 平台的 share 目录下已经为我们准备了全系列的 InternLM 模型，所以我们可以直接复制即可。使用如下命令复制：  
	```mkdir -p /root/model/Shanghai_AI_Laboratory
	cp -r /root/share/temp/model_repos/internlm-chat-7b /root/model/Shanghai_AI_Laboratory```
 
**代码准备**  
首先 clone 代码，在 /root 路径下新建 code 目录，然后切换路径, clone 代码.  
	```cd /root/code
	git clone https://gitee.com/internlm/InternLM.git```
切换 commit 版本，与教程 commit 版本保持一致，可以让大家更好的复现。  
	```cd InternLM
	git checkout 3028f07cb79e5b1d7342f4ad8d11efad3fd13d17```
将 /root/code/InternLM/web_demo.py 中 29 行和 33 行的模型更换为本地的 /root/model/Shanghai_AI_Laboratory/internlm-chat-7b。

**终端运行**  
在终端运行以下命令，即可体验 InternLM-Chat-7B 模型的对话能力。对话效果如下所示：
	```python /root/code/InternLM/cli_demo.py```
 
**web demo运行**  
换到 VScode 中，运行 /root/code/InternLM 目录下的 web_demo.py 文件，输入以下命令后，配置本地端口后，将端口映射到本地。在本地浏览器输入 http://127.0.0.1:6006 即可。  
	```bash
	conda activate internlm-demo  # 首次进入 vscode 会默认是 base 环境，所以首先切换环境
	cd /root/code/InternLM
	streamlit run web_demo.py --server.address 127.0.0.1 --server.port 6006```
### 3. Lagent工具调用demo
部署同上
有点小问题，调用工具解决复杂问题会报错显存不够，一元二次方程解法会出错
### 4. 浦语·灵笔图文理解创作 Demo
部署同上，注意选用开发机A100(1/4)*2
端口映射采用以下方式
	ssh -CNg -L 6006:127.0.0.1:6006 root@ssh.intern-ai.org.cn -p 33090
具体使用起来，图文并茂创作速度比较慢，多模态对话会出现幻觉问题（比如认为图片中有篮球，实际上没有）
### 5. 作业截图





