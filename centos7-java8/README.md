## centos7-jdk8 镜像制作 ##

### Oracle官网下载jdk linux安装包
	http://www.oracle.com/technetwork/java/javase/downloads/index.html
	这里以下载的 jdk-8u152-linux-x64.tar.gz 为例
	
### 编写Dockerfile
```
# Version 0.0.1.snapshots
FROM centos
MAINTAINER MARSPIE "marspie@126.com"

# 将jdk8添加到容器中   
ADD jdk-8u152-linux-x64.tar.gz /usr/local/

# 配置java环境变量 
ENV JAVA_HOME /usr/local/jdk1.8.0_152
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
ENV PATH $PATH:$JAVA_HOME/bin 
```

### build
```
root@ubuntu:~/docker/centos7-jdk8# docker build -t marspie/centos7-jdk8:0.0.1 .
Sending build context to Docker daemon  189.8MB
Step 1/6 : FROM centos
 ---> 3fa822599e10
Step 2/6 : MAINTAINER MARSPIE "marspie@126.com"
 ---> Running in 4c828c31e018
 ---> 38a79bfcb29d
Removing intermediate container 4c828c31e018
Step 3/6 : ADD jdk-8u152-linux-x64.tar.gz /usr/local/
 ---> b4097b35cbae
Removing intermediate container 3a241ceb60e8
Step 4/6 : ENV JAVA_HOME /usr/local/jdk1.8.0_152
 ---> Running in 99535b7fe479
 ---> 29dbc08f5d6c
Removing intermediate container 99535b7fe479
Step 5/6 : ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
 ---> Running in 3bc67973be35
 ---> 0d7fed803189
Removing intermediate container 3bc67973be35
Step 6/6 : ENV PATH $PATH:$JAVA_HOME/bin
 ---> Running in a15768ff1795
 ---> 875393d2fff2
Removing intermediate container a15768ff1795
Successfully built 875393d2fff2
Successfully tagged marspie/centos7-jdk8:0.0.1
```

### docker images
查看制作好的 docker镜像
```
docker images
```
