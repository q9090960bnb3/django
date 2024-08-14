# 官方教程

https://docs.djangoproject.com/zh-hans/5.1/

## 常用命令

```sh
# 创建项目
django-admin startproject mysite
```

`cd mysite` 后

```sh
# 运行服务器
python manage.py runserver 
# 创建应用 
python manage.py startapp polls
# 迁移数据库
python manage.py migrate
# 激活模型
python manage.py makemigrations polls
# 查看迁移对应的sql
python manage.py sqlmigrate polls 0001
```

## 管理页面

```sh
# 创建一个能登录管理页面的用户
python manage.py createsuperuser
```

## 运行测试

```sh
python manage.py test polls
```