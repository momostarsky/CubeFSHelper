### Maven 镜像采用阿里云镜像
maven 配置文件：  ~/.m2/settings.xml

注意 代理配置和镜像配置

```
<?xml version="1.0" encoding="UTF-8"?>
 
<settings xmlns="http://maven.apache.org/SETTINGS/1.2.0"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.2.0 https://maven.apache.org/xsd/settings-1.2.0.xsd">
  
 
 
  <proxies>
 
     <proxy>
      <id>myproxy</id>
      <active>true</active>
      <protocol>http</protocol> 
      <host>192.168.1.111</host>
      <port>33333</port>
      <nonProxyHosts>*.cn|*.aliyun.com|*.huaweicloud.com|local|localhost|::1|198.168.*</nonProxyHosts>
    </proxy>

  </proxies>

 
 
  <mirrors>
     
   <mirror>
    <id>aliyunmaven</id>
    <mirrorOf>central</mirrorOf>
    <url>https://maven.aliyun.com/repository/public</url>
   </mirror>

 
  </mirrors>

  
 
</settings>
```
