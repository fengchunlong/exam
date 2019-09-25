1.  介绍
Django教学项目——在线考试系统
2.  系统环境
Windows7及以上/ Linux发行版（Ubuntu16.04 / CentOS等）
MySQL 5.7及以上
Python3.5以上版本
Redis任意新版本即可
Django版本2.1


3.  配置文件
在项目根目录下的config文件夹中，新建一个local_settings.py文件
添加如下配置，注意python文件的严格缩进，不能多或少空格：
# MySQL配置
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'xx',
        'USER': 'xxx',
        'PASSWORD': 'xxx'
    }
}
# Redis配置
REDIS = {
    'default': {
        'HOST': '127.0.0.1',
        'PORT': 6379,
        'USER': '',
        'PASSWORD': '',
        'db': 0,
    }
}
BANK_REPO = ' F:/PythonProject/exam/backup '  # 修改为存放excel题库的位置，用来保留题库
BASE_NUM_ID = 100000
INIT_PASSWORD = 'p@ssw0rd'
DOMAIN = "http://xxx.xx.xx.xxx"  #### 需要修改此处域名
WEB_INDEX_URI = "{}/web/index".format(DOMAIN)  # 首页

# 发送邮件
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'  # 邮箱验证后台
EMAIL_USE_TLS = True  # 使用TSL
EMAIL_USE_SSL = False  # 使用SSL
EMAIL_SSL_CERTFILE = None  # SSL证书
EMAIL_SSL_KEYFILE = None  # SSL文件
EMAIL_TIMEOUT = None  # 延时
EMAIL_HOST = 'xxx.xxx@xx.xxx' SMTP地址
EMAIL_PORT = 465  # 端口
EMAIL_HOST_USER = 'xxx@xxx.xx'  # 发件邮箱
EMAIL_HOST_PASSWORD = 'password'  # 密码
SERVER_EMAIL = EMAIL_HOST_USER  # 服务器邮箱
DEFAULT_FROM_EMAIL = EMAIL_HOST_USER  # 默认发件人
ADMINS = [('Admin', 'xxx@xxx.xx')]  # 管理员邮箱

MANAGERS = ADMINS


4.安装环境
创建虚拟环境：
virtualenv venv
等待虚拟环境创建完成执行：
venv/bin/activate
然后安装项目所需安装包
pip install -r requirements.txt
安装过程如果发现错误，解决错误，直到所有文件安装完成。

5.创建数据库
执行命令连接数据库
mysql -uroot -p密码
创建数据库：
Create database 数据库名 default character set utf8;
然后执行：
python manage.py migrate  # 迁移数据库，创建数据表
继续创建超级用户：
python manage.py createsuperuser
创建完成整个系统部署完成了。
