# 流量超标自动关机脚本——超详细版

## 使用方法

### 1、简介

本脚本为腾讯云轻量服务器的流量监控脚本，可以定时监控多账户多地域多机器的流量使用情况，当已使用流量占总流量的百分比达到设定值（默认为95%）时会自动发出关机请求，避免流量超标，产生不必要的费用。

### 2、获取腾讯云API密钥

由于需要对腾讯云账号内的轻量服务器进行查询关机等操作，所以需要申请腾讯云API密钥。

先登录上腾讯云官网，然后点开下面这个链接：https://console.cloud.tencent.com/cam/capi

进入API密钥管理页面。

保存SecretId、SecretKey

### 3、获取qmsg酱 key（用于通知关机信息）

打开qmsg网址登录获取key

### 4、部署至GitHub Action

**4.1、fork项目**

由于需要使用自己的API密钥以及GitHub Action所以请务必先FORK本项目

fork完之后接下来的操作请在自己账号下的刚fork的repository下进行操作

**4.2、添加密钥**

项目中按照 Setting--Secrets--New repository secert的顺序添加secrets

依次添加之前保存的三个值

```
SecretId #腾讯云api密钥ID 以英文逗号分隔

SecretKey #腾讯云api密钥key 以英文逗号分隔

qkey #qmsg酱key
```

多账户需要注意腾讯云账号密钥的ID 和KEY的顺序，不能乱，单账号直接复制粘贴即可，添加后密钥显示名称会统一更换为大写字母。

依次添加完成即可。

### 效果检验

点击build就可以看到输出日志了

## 详细配置修改

流量百分比可以在LH.py中修改

更改运行频率

默认每小时运行一次 想要修改频率可以修改 .github/workflows/LH.yml中schedule的cron参数，具体使用方法可以前往 [crontab使用方法](https://2demo.top/231.html)查看

## 原作者
原版地址：https://github.com/2lifetop/LightHouse_Automatic_Shutdown/