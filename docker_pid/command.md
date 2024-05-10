> docker run -d -it --rm -p 8888:8080 tomcat:8.0

```
Unable to find image 'tomcat:8.0' locally
8.0: Pulling from library/tomcat
f189db1b88b3: Pull complete 
3d06cf2f1b5e: Pull complete 
edd0da9e3091: Pull complete 
eb7768aae14e: Pull complete 
e2780f585e0f: Pull complete 
e5ed720afeba: Pull complete 
d9e134700cfc: Pull complete 
e4804b33d02a: Pull complete 
b9df0c24315e: Pull complete 
49fdae8eaa20: Pull complete 
1aea3d9a32e6: Pull complete 
Digest: sha256:8ecb10948deb32c34aeadf7bf95d12a93fbd3527911fa629c1a3e7823b89ce6f
Status: Downloaded newer image for tomcat:8.0
64b31f4f4780590ea5ffdaeee1d9b19365575ee91276c029159e0f6afbc17175

```
> docker ps

```
CONTAINER ID   IMAGE        COMMAND             CREATED         STATUS         PORTS                                       NAMES

64b31f4f4780   tomcat:8.0   "catalina.sh run"   2 minutes ago   Up 2 minutes   0.0.0.0:8888->8080/tcp, :::8888->8080/tcp   affectionate_brown

```

* docker exec 64b31f4f4780 ps -eaf = will list all running process on a container 

> docker exec 64b31f4f4780 ps -eaf

```
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  2 09:25 pts/0    00:00:07 /docker-java-home/jre/bin/java -Djava.util.logging.config.file=/usr/local/tomcat/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djdk.tls.ephemeralDHKeySize=2048 -Djava.protocol.handler.pkgs=org.apache.catalina.webresources -Dignore.endorsed.dirs= -classpath /usr/local/tomcat/bin/bootstrap.jar:/usr/local/tomcat/bin/tomcat-juli.jar -Dcatalina.base=/usr/local/tomcat -Dcatalina.home=/usr/local/tomcat -Djava.io.tmpdir=/usr/local/tomcat/temp org.apache.catalina.startup.Bootstrap start
root          59       0  0 09:29 ?        00:00:00 ps -eaf

```
#### see below example

> docker exec 64b31f4f4780 ps -eaf

```
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  2 09:25 pts/0    00:00:07 /docker-java-home/jre/bin/java -Djava.util.logging.config.file=/usr/local/tomcat/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djdk.tls.ephemeralDHKeySize=2048 -Djava.protocol.handler.pkgs=org.apache.catalina.webresources -Dignore.endorsed.dirs= -classpath /usr/local/tomcat/bin/bootstrap.jar:/usr/local/tomcat/bin/tomcat-juli.jar -Dcatalina.base=/usr/local/tomcat -Dcatalina.home=/usr/local/tomcat -Djava.io.tmpdir=/usr/local/tomcat/temp org.apache.catalina.startup.Bootstrap start
root          65       0  0 09:31 ?        00:00:00 ps -eaf

```
> ps -eaf | grep docker-java-home

```
root      467717  467696  1 14:55 pts/0    00:00:07 /docker-java-home/jre/bin/java -Djava.util.logging.config.file=/usr/local/tomcat/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djdk.tls.ephemeralDHKeySize=2048 -Djava.protocol.handler.pkgs=org.apache.catalina.webresources -Dignore.endorsed.dirs= -classpath /usr/local/tomcat/bin/bootstrap.jar:/usr/local/tomcat/bin/tomcat-juli.jar -Dcatalina.base=/usr/local/tomcat -Dcatalina.home=/usr/local/tomcat -Djava.io.tmpdir=/usr/local/tomcat/temp org.apache.catalina.startup.Bootstrap start
einfoch+  471714  407471  0 15:02 pts/0    00:00:00 grep --color=auto docker-java-home

```

* here we are seeing same process but different PID which is only possible because it is using same process but the Namespace define differently for it 


