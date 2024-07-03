# GoT -- 基于SQLite数据库的指纹识别-漏洞POC管理扫描工具

## 工具功能截图
![基础功能](https://github.com/AgentVirus/GoT/blob/master/%E5%9B%BE%E7%89%87/1.jpg)

基于sqlite数据对网站指纹和POC进行管理使用，此工具的开发目的就是存储各个框架的识别指纹，和降低批量漏扫poc脚本编写和管理难度。

POC数据库支持类似于nuclei poc脚本部分功能（base64解密，正则表达式匹配，提取json字段），以后根据需要会更新更多功能。
![基础功能](https://github.com/AgentVirus/GoT/blob/master/%E5%9B%BE%E7%89%87/poc.jpg )

指纹数据库基于 网站title，body，图标hash和header对网站框架进行识别
![基础功能](https://github.com/AgentVirus/GoT/blob/master/%E5%9B%BE%E7%89%87/指纹.jpg )

## 基础功能

### 资产信息识别(Sniff)

#### 基本使用

-u

GoT.exe sniff -u http://127.0.0.1

![基础功能](https://github.com/AgentVirus/GoT/blob/master/%E5%9B%BE%E7%89%87/3.jpg)

#### sniff模块其他功能

![基础功能](https://github.com/AgentVirus/GoT/blob/master/%E5%9B%BE%E7%89%87/4.jpg)

#### 开启代理并检测代理位置

-proxy

-pr

GoT.exe sniff -u http://127.0.0.1 -proxy socks5://127.0.0.1:7890 -pr

![基础功能](https://github.com/AgentVirus/GoT/blob/master/%E5%9B%BE%E7%89%87/5.jpg)

#### 资产识别＋漏洞扫描

-at

GoT.exe sniff -u http://127.0.0.1.com:8888 -at

![基础功能](https://github.com/AgentVirus/GoT/blob/master/%E5%9B%BE%E7%89%87/6.jpg)

### POC+漏扫模块(Attempt)

#### 基础使用

-u 单个url

-f txt文件

-condition 通过数据库中的字段匹配漏洞进行漏洞扫描

使用sqlite数据库工具（DB Browser for SQLite）打开sqlite打开数据库

![基础功能](https://github.com/AgentVirus/GoT/blob/master/%E5%9B%BE%E7%89%87/7.jpg)

可以看到poc配置信息

编写poc的高级函数目前只支持3种：正则表达式，json提取，base64加密。以后会更新支持更多版本的高级函数。

#### attempt模块功能

![基础功能](https://github.com/AgentVirus/GoT/blob/master/%E5%9B%BE%E7%89%87/8.jpg)

-condition vuln="xxxx漏洞"
-condition CMS="xxxOA"

GoT.exe attempt -u http://127.0.0.1:8090  -condition vuln="用友U9-0702-敏感信息泄露-TransWebService" 

![基础功能](https://github.com/AgentVirus/GoT/blob/master/%E5%9B%BE%E7%89%87/9.jpg)

### 与FOFA联动(fofa)

在command.txt中编写fofa命令，在setting.json中填入key和邮箱

![基础功能](https://github.com/AgentVirus/GoT/blob/master/%E5%9B%BE%E7%89%87/12.jpg)

# 其余功能以后会更详细的文档进行详细的说明

### 有啥事发邮箱 agentpumpkin@zohomail.cn
