## 快速部署静态网页指南

#### 操作指南（假设代号为pdf1）
#### 注意：脚本运行过程中会有一些选项，都选Y即可
##### 修改配置文件

* 修改pdf_bash的APPNAME为新代号（pdf+数字），SERVICE改为需要部署的域名(www.().com这种)


##### 修改网页图片
>1. 将图片放到Fastash/project/main/static/images的目录下 并命名为paperForPc.png(如手机端要放不同的图，则再放一张名为paperForMobile.png的图，如果不需要手机端，则改Fastash/project/main/templates/main/index.html第26行为document.getElementById('demo').src="static/images/paperForPc.png")
2. 将白皮书pdf放在Fastash/project/main/static/目录下，命名为sth.pdf
3. 将小logo的图片放在Fastash/project/main/static/images的目录下并命名为logo.jpg


##### 修改完配置文件后
> 1. 将文件夹发送到服务器的根目录(scp -r 文件夹地址 root@(服务器ip):/ )  
2. 登陆服务器后 bash Setting-Pdf/pdf_bash #运行脚本
