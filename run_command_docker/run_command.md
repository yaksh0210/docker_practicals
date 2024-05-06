#### 1) Sudo docker run [module]:[version] = it will help you to download module/container with its specific version using docker

> sudo docker run redis:4.0.0

``` output:

Unable to find image 'redis:4.0' locally
4.0: Pulling from library/redis
54fec2fa59d0: Pull complete 
9c94e11103d9: Pull complete 
04ab1bfc453f: Pull complete 
7988789e1fb7: Pull complete 
8ce1bab2086c: Pull complete 
40e134f79af1: Pull complete 
Digest: sha256:2e03fdd159f4a08d2165ca1c92adde438ae4e3e6b0f74322ce013a78ee81c88d
Status: Downloaded newer image for redis:4.0
1:C 06 May 09:04:01.797 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
1:C 06 May 09:04:01.797 # Redis version=4.0.14, bits=64, commit=00000000, modified=0, pid=1, just started
1:C 06 May 09:04:01.797 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
1:M 06 May 09:04:01.798 * Increased maximum number of open files to 10032 (it was originally set to 1024).
1:M 06 May 09:04:01.799 * Running mode=standalone, port=6379.
1:M 06 May 09:04:01.799 # Server initialized
1:M 06 May 09:04:01.799 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
1:M 06 May 09:04:01.799 # WARNING you have Transparent Huge Pages (THP) support enabled in your kernel. This will create latency and memory usage issues with Redis. To fix this issue run the command 'echo never > /sys/kernel/mm/transparent_hugepage/enabled' as root, and add it to your /etc/rc.local in order to retain the setting after a reboot. Redis must be restarted after THP is disabled.
1:M 06 May 09:04:01.799 * Ready to accept connections

sudo docker ps (TO CHECK PROCESS)

CONTAINER ID   IMAGE       COMMAND                  CREATED         STATUS         PORTS      NAMES
f92a8d5c418b   redis:4.0   "docker-entrypoint.s…"   3 minutes ago   Up 3 minutes   6379/tcp   quirky_mccarthy

```

#### 2) sudo docker run -i [own_created_container]/simple-prompt-docker = it will run your container with -i ( interactive mode) which helps to take an input during run time and it works to print output which will be performed in container 

> sudo docker run -i kodekloud/simple-prompt-docker


```
output:

Welcome! Please enter your name: yaksh

Hello and Welcome yaksh!

```

