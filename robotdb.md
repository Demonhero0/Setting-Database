### 数据库部署指南（假设数据库代号为robotdb）
#### 登陆服务器创建数据库

#### 修改配置文件
* 修改robotdb_bash APPNAME为新代号（robotdb+数字），SERVICE改为需要部署的服务器ip

#### 修改完配置文件后
1. 将Setting-robotdb发送到服务器的根目录
        scp -r (Setting-robotdb在本地的地址) root@(服务器ip):/
        （这时会要求输入服务器的密码）
2. 登陆服务器运行脚本  
    登陆服务器之后，bash /Setting-robotdb/robotdb_bash，运行脚本后：
    * 若看到"postgres@..."的东西，则按以下输入
          $
          sudo su - postgres
          postgres@django:~$ createuser --interactive -P
          Enter name of role to add: robot（这个为数据库用户）
          Enter password for new role:12345678（这个为数据库用户密码）
          Enter it again:12345678
          Shall the new role be a superuser? (y/n) n
          Shall the new role be allowed to create databases? (y/n) n
          Shall the new role be allowed to create more new roles? (y/n) n

          postgres@django:~$ createdb --owner robot robotdb（这个为数据库名字）
          postgres@django:~$ logout
          $
      *创建数据库成功，若要在一个服务器上部署两个数据库，请再创建一个新数据库用户和新数据库*  

    * 若看到

#### 手动操作
      cd /webapps/robotdb/
      source venv/bin/activate
      python robot_backend/manage.py mekemigrations
      python robot_backend/manage.py migrate
      python robot_backend/manage.py crontab add    #启动定时清理数据库功能
      python robot_backend/manage.py createsuperuser #创建超级用户
