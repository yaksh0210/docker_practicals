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
aeb5ceeea4b00a0f9a5f3c485ffe8cbceb09b1c33b2081cfe9f0d278e5a24ba9
```

> docker ps

```
CONTAINER ID   IMAGE        COMMAND             CREATED         STATUS         PORTS                                       NAMES
aeb5ceeea4b0   tomcat:8.0   "catalina.sh run"   4 seconds ago   Up 3 seconds   0.0.0.0:8888->8080/tcp, :::8888->8080/tcp   flamboyant_moore

```

> docker exec aeb5ceeea4b0 ps -eaf = it will list all process running on the container 

```
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  5 09:51 pts/0    00:00:04 /docker-java-home/jre/bin/java -Djava.util.logging.config.file=/usr/local/tomcat/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djdk.tls.ephemeralDHKeySize=2048 -Djava.protocol.handler.pkgs=org.apache.catalina.webresources -Dignore.endorsed.dirs= -classpath /usr/local/tomcat/bin/bootstrap.jar:/usr/local/tomcat/bin/tomcat-juli.jar -Dcatalina.base=/usr/local/tomcat -Dcatalina.home=/usr/local/tomcat -Djava.io.tmpdir=/usr/local/tomcat/temp org.apache.catalina.startup.Bootstrap start
root          59       0  0 09:53 ?        00:00:00 ps -eaf

```

> ps -eaf | grep docker-java-home

```
root      485413  485391  3 15:21 pts/0    00:00:04 /docker-java-home/jre/bin/java -Djava.util.logging.config.file=/usr/local/tomcat/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djdk.tls.ephemeralDHKeySize=2048 -Djava.protocol.handler.pkgs=org.apache.catalina.webresources -Dignore.endorsed.dirs= -classpath /usr/local/tomcat/bin/bootstrap.jar:/usr/local/tomcat/bin/tomcat-juli.jar -Dcatalina.base=/usr/local/tomcat -Dcatalina.home=/usr/local/tomcat -Djava.io.tmpdir=/usr/local/tomcat/temp org.apache.catalina.startup.Bootstrap start
einfoch+  485739  407471  0 15:24 pts/0    00:00:00 grep --color=auto docker-java-home
 
```

* above two command run the same process but with the different PID because of Namespace concept where in first command PID is 1 for the very first process but in actual global environment it is 485413 as shown in second command 

