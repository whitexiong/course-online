# 选题

SpringCloud + Vue  的在线视频课程系统与实现

# 架构

前后端分离

## 项目模块说明

* **admin**<br>
  控台管理，vue cli项目
* **business**<br>
  核心业务模块，spring boot项目
* **doc**<br>
  项目相关的文档，包含项目数据库初始化脚本
* **eureka**<br>
  注册中心，spring boot项目
* **file**<br>
  文件模块，spring boot项目
* **gateway**<br>
  路由模块，spring boot项目
* **generator**<br>
  代码生成器
* **server**<br>
  公共jar模块，被business, file, system依赖
* **system**<br>
  系统模块，spring boot项目
* **web**<br>
  网站模块，vue cli项目


## 项目启动

* 启动注册中心：EurekaApplication
* 启动路由模块：GatewayApplication
* 启动系统模块：SystemApplication
* 启动业务模块：BusinessApplication
* 启动文件模块：FileApplication
* 启动控台管理：admin\package.json
* 启动前端网站：web\package.json

## 页面访问

* 控台地址: http://localhost:8080/login<br>
  初始用户名密码：test/test


## 启动 Redis

> cd C:\software\redis\Redis-x64-5.0.10 <br>
> redis-server.exe redis.windows.conf

## 启动 Vue 后端

> cd C:\software\LunWen\www\zj\course-online\admin <br>
> npm run serve-dev

## 启动 Vue 前端

> cd C:\software\LunWen\www\zj\course-online\web <br>
> npm run serve-dev

