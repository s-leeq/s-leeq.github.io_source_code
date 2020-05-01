---
layout: post
title: Linux 系统使用 vlmcsd 搭建 KMS 服务器教程
date: 2020-04-29 14:54
author: "Stan Lee"
categories:
	- 教程
---

# 快速食用

## 快速激活命令

```PowerShell
site : kms.stanlsite.xyz
port : 1688 (default)

# Windows 激活命令：
slmgr /ipk GVLK
slmgr /skms kms-server[:tcp-port]
slmgr /ato

# Microsoft Office 激活方法：
# 使用 Office Tool Plus 激活，下载地址：
https://download.coolhub.top/Office-Tool-v8.0.zip
```

## 快速部署命令

```bash
# 秋水逸冰大佬的 VLMCSD 一键部署脚本
wget --no-check-certificate https://github.com/teddysun/across/raw/master/kms.sh && chmod +x kms.sh && ./kms.sh

# 启动
/etc/init.d/kms start
```



# KMS 介绍

> 批量授权密钥（英语：Volume License Key，简称VLK）是软件公司使用的一个词汇，用户购买批量授权，便会获得一产品密钥，该密钥可安装于多部电脑。换言之，企业可于多台电脑使用同一产品密钥，而不需为每台电脑输入不同的密钥。这种授权方式通常只给商业机构、政府和教育机构，价格会因购买数量、类型和使用条款而不同。
> Microsoft也会为其软件提供大量授权，包括Windows Vista, Windows 7 Pro, Windows 7 Enterprise, Windows 8, Windows 8.1, Windows 10, Windows Server, Microsoft Office。
>
> > 摘自 [Wikipedia](https://zh.wikipedia.org/wiki/大量授權金鑰)。 



# 在 CentOS 上部署 VLMCSD

## 使用秋水逸冰[《一键安装KMS服务脚本》](https://teddysun.com/530.html)中的快速部署脚本进行部署

1. 在获取 root 权限的前提下，输入以下指令：

   ```bash
   wget --no-check-certificate https://github.com/teddysun/across/raw/master/kms.sh && chmod +x kms.sh && ./kms.sh
   ```

2. 安装完成后，检查1688端口监听情况：

   ```bash
   netstat -nxtlp | grep 1688
   ```

3. 完成。

> 注：脚本运行完毕后 VLMCSD 将自动设置为开机自启动。

```bash
# Usage: 
./kms.sh start | stop | restart | status
```



# 详细激活方法

## Windows 激活

1. 使用管理员权限打开CMD；

2. （如果已安装VL版系统且未使用其他密钥尝试激活过则可以跳过）安装GVLK(Generic Volume License Keys 通用批量许可证密钥)；
```PowerShell
# usage:
slmgr /ipk GVLK
# 以 Windows 10 专业工作站版为例
slmgr /ipl NRG8B-VKK3Q-CXVCJ-9G2XF-6Q84J
```
注：GVLK 附在文后。

3. 配置 KMS 服务器；
```PowerShell
# usage:
slmgr /skms kms-server[:tcp-port]
# 以 kms.stanlsite.xyz (port : 1688) 举例
slmgr /skms kms.stanlsite.xyz:1688 # 若端口为1688（默认值）则可省略
```

4. 激活Windows；
```PowerShell
slmgr /ato
```

5. 稍待片刻系统将提示成功激活信息。

---

## Office 激活

个人推荐使用基于 Office 部署工具（ODT）开发的 [Office Tool Plus](https://download.coolhub.top/Office-Tool-v8.0.zip) 部署并安装批量激活版 Microsoft Office 软件。下载完成后，按提示步骤部署 Office 软件（如果想使用 KMS 激活，必须选择批量版下载安装）。