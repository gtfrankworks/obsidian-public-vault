## 1.  Hermes的安装
## 2. OpenWebUi的安装
### 1. 首先根据官方的推荐安装docker
1. 登录官网https://www.docker.com/
2. 下载相应的docker根据自己的操作系统，这里我mac为例
	![[Pasted image 20260427113605.png]]
3. 下载完直接双击安装完毕
	1. ![[Pasted image 20260427113645.png]]
### 2.安装openwebui
1. 直接运行下面的代码
```
	1. docker run -d \
  -p 3000:8080 \
  --add-host=host.docker.internal:host-gateway \
  -v open-webui:/app/backend/data \
  --name open-webui \
  ghcr.io/open-webui/open-webui:main
```
![[Pasted image 20260427113843.png|697]] 
 2. 安装完毕测试运行
	 1. http://localhost:3000/
	 2. 这个是需要注册，我注册过了
		 ![[Pasted image 20260427114026.png]]
	 3. 直接登录
		 1. ![[Pasted image 20260427114058.png]]
 ### 3. 配置hermes
 