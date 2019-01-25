## 快速部署静态网页指南

#### 操作指南（假设代号为pdf1）
#### 注意：脚本运行过程中会有一些选项，都选Y即可
##### 修改配置文件
>1. 修改pdf_bash的APPNAME(3)  
2. 增加需要部署的域名到base.py的ALLOWED_HOSTS(29)  
3. 修改bash_supervisor.conf(1、2、3、4)的pdf1改为新代号  
4. 修改gunicorn_start的APPNAME为新代号  
5. 修改base_nginx的service_name为所需部署的域名(12),修改(6、17、18、21、25、63)的地址中的pdf1改为新代号
6. 修改bashForVirtualenv的APPNAME为新代号

##### 修改网页图片
>1. 将图片放到Fastash/project/main/static/images的目录下 并命名为paperForPc.png，修改Fastash/project/main/templates/main/index.html的108行为<img id="demo" src="static/images/paperForPc.png" alt="">(如手机端要放不同的图，则再放一张名为paperForMobile.png的图，修改第26行为      document.getElementById('demo').src="static/images/paperForMobile.png"，如果不需要手机端，则改为document.getElementById('demo').src="static/images/paperForPc.png"
2. 将白皮书pdf放在Fastash/project/main/static/目录下，假设命名为sth.pdf,则修改Fastash/project/main/templates/main/index.html的第109行为<span onclick="location.href='static/sth.pdf'">white paper project</span>
3. 将小logo的图片放在Fastash/project/main/static/images的目录下并命名为logo.jpg，修改第77行为<link href="static/images/logo.jpg" rel="shortcut icon" type="image/x-icon" />


##### 修改完配置文件后
> 1. 将文件夹发送到服务器的根目录(scp -r 文件夹地址 root@(服务器ip))  
2. bash Setting-Pdf/pdf_bash #运行脚本
