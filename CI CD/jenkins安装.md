jenkins安装
===========
1、下载yum源  
https://mirrors.tuna.tsinghua.edu.cn/jenkins/redhat/  
``` wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo ```  
2、安装jdk 1.8以上  

3、安装jenkins  更改用户可选
```
# yum install jenkins -y 
# useradd deploy
# vim /etc/sysconfig/jenkins
  JENKINS_USER="deploy"
  JENKINS_PORT="8080"
#chown -R deploy:deploy /var/lib/jenkins
#chown -R deploy:deploy /var/log/jenkins
```  
4、配置jenkins JDK路径  
```
vim /etc/init.d/jenkins    #在candidates中第一行添加java路径
candidates=" 
/opt/jdk1.8.0_60/bin/java     #添加此项
/etc/alternatives/java
/usr/lib/jvm/java-1.6.0/bin/java
/usr/lib/jvm/jre-1.6.0/bin/java
/usr/lib/jvm/java-1.7.0/bin/java
/usr/lib/jvm/jre-1.7.0/bin/java
/usr/lib/jvm/java-1.8.0/bin/java
/usr/lib/jvm/jre-1.8.0/bin/java
/usr/bin/java
```  
5、启动jenkins  
``` systemctl start jenkins ```  
6、网页访问  
192.168.1.1:8080  
7、根据网页提示密码路径查看密码  
```
# cat /var/lib/jenkins/secrets/initialAdminPassword
073543b7bd5c4935b07b4a294c87e5bc
```  
