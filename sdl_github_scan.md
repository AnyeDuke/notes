### github泄露扫描

使用小米的开源系统[MiSecurity/x-patrol: github泄露扫描系统](https://github.com/MiSecurity/x-patrol)

### 搭建过程

进入 https://github.com/MiSecurity/x-patrol/releases

下载 二进制版本

MAC的二进制文件名为x-patrol_darwin_amd64

还需要下载仓库中的3个文件夹：conf、public、templates

现在文件夹结构如下：
```
.
├── conf
│   ├── app.ini
│   └── gitrob.json
├── public
│   ├── css
│   ├── js
│   └── lib
├── templates
└── x-patrol_darwin_amd64
```

配置数据库命令：
```
mysqld #启动mysql服务端
create database xiaomi; #登录mysql并创建一个让该系统使用的数据库 我这里命名为xiaomi
```

修改conf/app.ini文件：
```
HTTP_HOST = 127.0.0.1
HTTP_PORT = 8000
MAX_INDEXERS = 2
DEBUG_MODE = true
REPO_PATH = repos
MAX_Concurrency_REPOS = 1

[database]
;support sqlite3, mysql, postgres
DB_TYPE = mysql
HOST = 127.0.0.1
PORT = 3306
NAME = xiaomi
USER = root
PASSWD = root
SSL_MODE = disable
PATH = data
```

运行二进制文件：
```
./x-patrol_darwin_amd64 web
```

登录系统：
```
http://127.0.0.1:8000

#默认账号密码 建议登录后修改
xsec
x@xsec.io
```

![效果图.png (2862×1234)](https://images2.imgbox.com/97/e4/Vvwo6DPU_o.png)