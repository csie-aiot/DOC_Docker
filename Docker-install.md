# Docker 安裝教學
本文件為docker安裝教學

## 系統環境
* Ubuntu Focal 20.04 (LTS)
* Ubuntu Bionic 18.04 (LTS)
* Ubuntu Xenial 16.04 (LTS)


Docker Engine is supported on x86_64 (or amd64), armhf, and arm64 architectures.


## 移除舊Docker套件
如果有舊版docker套件請移除該套件

```
sudo apt-get remove docker docker-engine docker.io containerd runc
```
![](https://i.imgur.com/56UQLpR.png)

確認移除之後就準備安裝docker相關工具


## 安裝


### 第一步 更新ubuntu列表

```
//更新 ubuntu 套件列表
sudo apt update

// 安裝相關工具
sudo apt install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```


### 第二步  加入認證key

這個動作在於使用curl與官方請求認證key

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

```
完成後顯示ＯＫ
![](https://i.imgur.com/5dFk99E.png)


### 第三步驟 驗證數位指紋

驗證數位指紋動作
![](https://i.imgur.com/4eMPIHV.png)


### 第四步驟 設定遠方倉儲

設定套件的倉儲版本 為穩定版來源

```
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
  
```
接者電腦就會抓相關列表

![](https://i.imgur.com/F2UkRmx.png)


### 第五步驟 安裝Docker

注意： 若沒有進行前面步驟 可能導致docker版本 非穩定版本以及不安全套件來源

```
//更新linux套件列表
sudo apt-get update

//安裝docker 套件
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

完成後可輸入docker -v 檢查docker是否有正常運行
![](https://i.imgur.com/U5hXZcH.png)


### 第一次的Image

docker 操作主要是使用包裝好的image把環境建立起來運行
這邊可以測試最簡單的shell是否有運行成功

 ```
 // 這個指令主要是 運行run hello-world 
 // 第一次運行一定會找不到相關image，會自動下載在運行
 sudo docker run hello-world
 ```

成功會顯示hello 以下
![](https://i.imgur.com/9Avv3u5.png)


### 加入使用者群組權限

docker運行每次都需使用最高權限root 來操作
若不想每次都加  sudo可使用以下指令

注意：加入權限後，記得登出或重新連線讓這個設定生效


```
// your-user 改成自己的使用者名稱 我這邊是改成roni
sudo usermod -aG docker your-user

```

![](https://i.imgur.com/5urTX2e.png)
