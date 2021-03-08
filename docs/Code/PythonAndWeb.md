---
title: Python Django学习
tags:
  - [网络]
  - [Python]
categories: [网络]
date: 2020-06-25 20:08:49
---
<font face="微软雅黑"> </font>
<center> </center>

<!-- more -->
[Python-100-Days](https://github.com/jackfrued/Python-100-Days)

# Web框架
Flask：The Python micro framework for building web applications.
## flask与django
[比较与选择](https://www.zhihu.com/question/20706333)
WSGI（Web Server Gateway Interface），
1. Flask 讲究的是 less is more
2. Django 讲究的是 more is less


## fastapi
自动生成API文档：编写API接口后，你就可以使用符合标准的UI如SwaggerUI，ReDoc等来使用API​​。
其它异步框架，包括：Tornado、Snaic、Quart。

```
pip install fastapi uvicorn
```
main.py:
```
from fastapi import FastAPI

app = FastAPI()


@app.get("/")
def read_root():
    return {"Hello": "World"}

@app.get("/items/{item_id}")
def read_item(item_id: int, q: str = None):
    return {"item_id": item_id, "q": q}
```

```
uvicorn main:app --reload
```
可访问：
网站： http://127.0.0.1:8000
Interactive API docs： http://127.0.0.1:8000/docs
Alternative API docs： http://127.0.0.1:8000/redoc

**Uvicorn**:轻量的 **ASGI**服务, built on uvloop and httptools.


# Django学习
官方教程[初识 Django](https://docs.djangoproject.com/zh-hans/3.0/intro/overview/)


## MVT
Django 采用了 MVT 的软件设计模式，即模型（Model），视图（View）和模板（Template）。
- Model:构建并操作web应用的数据。`models.py`
- View：处理用户请求并返回响应。`views.py`,`urls.py`，Django 中的视图的概念是「一类具有相同功能和模板的网页的集合」。
- Template：提供一个对设计者友好的语法用于渲染向用户呈现的信息.`./templates/app_name/template_file`

## Tutorial-创建投票应用
安装2.2.13版本的django，[官方入门教程](https://docs.djangoproject.com/zh-hans/2.2/contents/)。

Django使用对象关系映射（Object Relational Mapping，简称 `ORM` ）用于实现面向对象编程语言里不同类型系统的数据之间的转换


**创建站点**
```
django-admin startproject mysite
```
startproject 创建了:

```
mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        wsgi.py

```
- `最外层的 mysite/` 根目录只是你项目的容器， Django 不关心它的名字，你可以将它重命名为任何你喜欢的名字。
- `manage.py`: 管理 Django 项目的命令行工具。
- `里面一层的 mysite/` 目录包含你的项目，是一个纯 Python 包。它的名字就是引用它内部任何东西时需要用到的 Python 包名。 (比如 mysite.urls).
- `mysite/__init__.py`：一个空文件，告诉 Python 这个目录应该被认为是一个 Python 包。
- `mysite/settings.py`：Django 项目的配置文件。
- `mysite/urls.py`：Django 项目的 URL 声明。
- `mysite/wsgi.py`：作为你的项目的运行在 WSGI 兼容的Web服务器上的入口。

运行
```
python manage.py runserver 8080
```
**站点内创建app**
```
python manage.py startapp polls

```
这将会创建一个 polls 目录，它的目录结构大致如下：

```
polls/
    __init__.py
    admin.py  #管理界面
    apps.py
    migrations/
        __init__.py
    models.py #模型定义
    tests.py  #测试工具
    views.py  #视图
```

**数据表**
Python 内置 SQLite，数据保存为一个文件。也可使用其它数据库。
默认开启的某些应用在使用之前需要在数据库中创建一些表。执行以下命令：
```
python manage.py migrate
```
创建管理用户：
```
python manage.py createsuperuser

```
交互式命令：
```
python manage.py shell
```
manage.py 会设置 DJANGO_SETTINGS_MODULE 环境变量，这个变量会让 Django 根据 mysite/settings.py 文件来设置 Python 包的导入路径。



**模板**
`/mysite/polls/templates/polls/index.html`

**css**
`./polls/static/polls/style.css`




## 搭建博客

[Python-100Days-Django](https://github.com/jackfrued/Python-100-Days/tree/master/Day41-55)
[blog教程](https://www.zmrenwu.com/courses/hellodjango-blog-tutorial)


已使用GitHub Pages、LNMP+Wordpress、静态网站托管搭建博客，Django客管理较复杂，无必要学习。

---

## 打包与复用


# 爬虫框架
[Scrapy](https://github.com/scrapy/scrapy)
https://www.runoob.com/w3cnote/scrapy-detail.html

[crawlab](https://github.com/crawlab-team/crawlab)：分布式爬虫管理平台，支持任何语言和框架。
