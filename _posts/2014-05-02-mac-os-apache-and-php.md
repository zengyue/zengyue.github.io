---
layout: post
title: "MacOS下Apache和PHP的配置"
category: apache
tagline: 
tags: [apache]
description: "MacOS下Apache和PHP的配置"
---

# MacOS下Apache+PHP的配置
> mac os下是自带apache+php的，所以只要把服务开起来就可以了

## apache+php的基本配置
1. cd到/etc/apache2目录，打开httpd.conf文件
2. 找到`#LoadModule php5_module        libexec/apache2/libphp5.so`这一行，把前面的`#`号去掉
3. 然后将/etc/php.ini.default复制为/etc/php.ini
4. 执行`sudo apachectl start`起动就行了

## 启用虚拟主机
1. 打开httpd.conf文件
2. 找到`#Include /private/etc/apache2/extra/httpd-vhosts.conf`，把前面的`#`号去掉
3. 然后打开/etc/apache2/extra/httpd-vhosts.conf
4. 添加一个虚拟主机就可以了

```
   <VirtualHost *:80>
    DocumentRoot "/Users/xxx/Sites"
    ServerName localhost
    ErrorLog "/private/var/log/apache2/localhost-error_log"
    CustomLog "/private/var/log/apache2/localhost-access_log" common
    <Directory />
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order deny,allow
        Allow from all
    </Directory>
   </VirtualHost> 
```

## https服务的配置
### 1. 生成主机密钥
```
mkdir /private/etc/apache2/ssl
cd /private/etc/apache2/ssl
sudo ssh-keygen -f server.key
```
### 2. 生成证书请求文件
```
sudo openssl req -new -key server.key -out server.csr
```
### 3. 生成ssl证书
```
sudo openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt
```

### 4. 这样证书就算生成完了，接下来开始配置apache了

#### 1. 打开`/etc/apache2/httpd.conf`文件

```
# 分别找到下面这两行，去掉前面的#号
LoadModule ssl_module libexec/apache2/mod_ssl.so
Include /private/etc/apache2/extra/httpd-ssl.conf
```

#### 2. 打开`/etc/apache2/extra/httpd-ssl.conf`文件
```
# 找到下面这两行，去掉前面的#号，并将后面的文件指定为前面生成的文件
SSLCertificateFile "/private/etc/apache2/ssl/server.crt"
SSLCertificateKeyFile "/private/etc/apache2/ssl/server.key"
```

#### 3. 打开`/etc/apache2/extra/httpd-vhosts.conf`
```
# 在文件末尾添加
<VirtualHost *:443>
  SSLEngine on
  SSLCipherSuite ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL
  SSLCertificateFile /private/etc/apache2/ssl/server.crt
  SSLCertificateKeyFile /private/etc/apache2/ssl/server.key
  ServerName localhost
  DocumentRoot "/some/website/directory/"
</VirtualHost>
```

#### 4. 执行`sudo apachectl restart`重启apache就可以了