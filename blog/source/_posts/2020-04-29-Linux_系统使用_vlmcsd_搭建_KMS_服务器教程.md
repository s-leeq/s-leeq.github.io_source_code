---
layout: post
title: Linux 系统使用 vlmcsd 搭建 KMS 服务器教程
date: 2020-04-29 14:54
author: "Stan Lee"
categories:
	- 教程
---

# 快速食用

```
site : kms.stanlsite.xyz
port : 1688 (default)
```

## 食用方法

### Windows 激活

1. 使用管理员权限打开CMD；

2. （如果已安装VL版系统且未使用其他密钥尝试激活过则可以跳过）安装GVLK(Generic Volume License Keys 通用批量许可证密钥)；
```PowerShell
slmgr /ipk GVLK
```
GVLK 附在文后。

3. 配置 KMS 服务器；
```PowerShell
slmgr /skms kms-server[:tcp-port]
# 以 kms.stanlsite.xyz (port : 1688) 举例
slmgr /skms kms.stanlsite.xyz:1688 # 若端口为1688（默认值）则可省略
```

4. 激活Windows；
```PowerShell
slmgr /ato
```

5. 稍待片刻系统将提示成功激活信息。

### Office 激活介绍

#### 

# KMS 介绍
> 批量授权密钥（英语：Volume License Key，简称VLK）是软件公司使用的一个词汇，用户购买批量授权，便会获得一产品密钥，该密钥可安装于多部电脑。换言之，企业可于多台电脑使用同一产品密钥，而不需为每台电脑输入不同的密钥。这种授权方式通常只给商业机构、政府和教育机构，价格会因购买数量、类型和使用条款而不同。
Microsoft也会为其软件提供大量授权，包括Windows Vista, Windows 7 Pro, Windows 7 Enterprise, Windows 8, Windows 8.1, Windows 10, Windows Server, Microsoft Office。
> 摘自 [Wikipedia](https://zh.wikipedia.org/wiki/大量授權金鑰)。