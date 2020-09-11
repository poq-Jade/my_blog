title: Hexo博客搭建
author: John Doe
tags:
  - Hexo
date: 2020-09-08 12:08:41
---
# 什么是 Hexo？
Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

官方文档：https://hexo.io/zh-cn/docs/

# 安装
安装 Hexo 相当简单，只需要先安装下列应用程序即可：

Node.js (Node.js 版本需不低于 8.10，建议使用 Node.js 10.0 及以上版本)

## Git

如果您的电脑中已经安装上述必备程序，那么恭喜您！你可以直接前往 安装 Hexo
步骤。如果您的电脑中尚未安装所需要的程序，请根据以下安装指示完成安装。

## 安装 Git
```
sudo yum -y install git 
git config --global user.name "你的账号" 
git config --global user.email "你的邮箱"
```
## 安装 Node.js
下载地址 https://nodejs.org/en/download/
```
wget https://nodejs.org/dist/v12.16.1/node-v12.16.1-linux-x64.tar.xz 

#解压 tar xf
node-v12.16.1-linux-x64.tar.xz -C /usr/local/ 

#配置软连接 
cd /usr/local/ 
ln -s node-v12.16.1-linux-x64 node 
echo 'export PATH=/usr/local/node/bin:\$PATH' >> /etc/profile 
source /etc/profile 

#查看版本 
node -v 
npm -v
```

## 安装 Hexo
所有必备的应用程序安装完成后，即可使用 npm 安装 Hexo
```
npm install -g hexo-cli

hexo -v
```

进阶安装和使用

对于熟悉 npm 的进阶用户，可以仅局部安装 hexo 包。

```
npm install hexo
```

安装完hexo框架，就可以开始初始化hexo了，选择一个目录存放你的博客文件，切换到目录。接着，输入

hexo init blog 进行初始化hexo
## 初始化Hexo
```
hexo init my_blog
```

## 建站
```
cd /data/my_blog

npm install
```
新建完成后，指定文件夹的目录如下：
```
├── _config.yml
├── package.json
├── scaffolds 
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

|文件/文件夹|说明|	
| ----------------------|:--------------------- |
| _config.yml |	配置文件			|
| public    |生成的静态文件，这个目录最终会发布到服务器 |
| scaffolds	|一些通用的markdown模板					|
| source|编写的markdown文件，_drafts草稿文件，_posts发布的文章|
| themes|主题文件夹。Hexo 会根据主题来生成静态页面。|

Hexo会根据主题来生成静态页面。

清除缓存
```
hexo clean
```
生成静态文件
```
hexo g
```
运行hexo
```
hexo s
```
后台运行hexo
```
npm install -g pm2 

vi run.js
//run.js
const { exec } = require('child_process')
exec('hexo server',(error, stdout, stderr) => {
  if(error){
    console.log(`exec error: ${error}`)
    return
  }
  console.log(`stdout: ${stdout}`);
  console.log(`stderr: ${stderr}`);
})

#进入博客根目录,运行脚本
pm2 start run.js
```

# 访问hexo
http://localhost:4000/

# Github与Gitee的配置与访问
上面已经搭建完成了基础环境，下面我们想要在互联网上可以随意访问个人的博客，但是我们当下没有自己的服务器和相应的外网IP地址，对此，这里我们采用GitHub的方式进行发布自己的个人博客。

前提条件自己需要去https://github.com/官网进行注册一个账号

在该账号下创建一个项目，该项目名称命名方式要遵循以下格式：

hexo的个人博客名称（也是自己以后访问使用的域名）.github.io

注册好了后，登录Github,创建仓库：点击右上角的+号，选择new repository:
![](/images/pasted-0.png)


![](:mages/pasted-1.png)



切换到自己的服务器中，在~目录下执行
```
ssh-keygen -t rsa -C "你的github中设置的邮箱"
```


建议在设置ssh的秘钥时设置一个证书密码
```
cat .ssh/id_rsa.pub
```
将上面查看的所有信息复制一份放到GitHub上面

在服务器中进行执行以下命令进行测试ssh直连是否可用

```
ssh -T git@github.com
```
这里在执行时会让输入一个密码，这个密码就是上面证书设置的密码，如果上面没有设置密码，则这里直接免密连接。

连接成功会打印一句话：

```
Hi cnHuaShao! You've successfully authenticated, but GitHub does not provide
shell access.
```


# hexo的git基础管理工具
## 安装基础的管理软件
```
cd /data/my_blog 

npm install hexo-deployer-git --save
```

# 设置hexo项目提交位置
```
cd ~/你的hexo项目名
vim _config.yml
#翻到最底部，设置以下内容,:wq保存并退出
deploy:
  type: git
  repo: https://github.com/你的GitHub的名称/上面设置的名称.github.io.git
  branch: master
```
注：在提交的过程中会让输入GitHub的账号密码，如果想不输入账号密码，则把repo更改为ssh地址

# 加载博客样式文件     
需要修改_config.yml文件中的url地址和根目录
url：是github Page给我们分配的网址
root：是搭建该博客的仓库名
```
url: https://poq-jade.github.io/hexo.github.io/
root: /hexo.github.io
```

# 清理缓存，重新生成静态文件并部署
```
hexo clean
hexo generate
hexo deploy
```

# 安装hexo-admin后台
首先进入hexo创建的博客项目的根目录下，执行

```
npm install --save hexo-admin
```
mac可能需要root权限，前面加个sudo就可以了。如果报错缺少组件，则缺少什么安装什么，npm install 加缺少的组件。

运行下列命令启动hexo-admin ：
```
hexo server -d
```
打开 http://localhost:4000/admin/ 就可以访问到hexo-admin管理页面了。

密码保护

打开setting，点击Setup authentification
here输入用户名，密码，密钥，下面会自动生成配置文件，复制加在hexo根目录下的_config.yml中：
```
admin:
  username: xxx
  password_hash: xxx
  secret: xxx
  deployCommand: ./admin_script/hexo-d.sh
```
重启hexo，就可以看到登录页面了