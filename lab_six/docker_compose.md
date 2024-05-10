#### 1) First create a redis database container called redis, image redis:alpine.

> docker run --name=redis redis:alpine

```

output:

Unable to find image 'redis:alpine' locally
alpine: Pulling from library/redis
4abcf2066143: Pull complete 
5c3180d10209: Pull complete 
f76326fd8e6b: Pull complete 
034c076ba1e7: Pull complete 
dffcad17539b: Pull complete 
5913474e0f39: Pull complete 
4f4fb700ef54: Pull complete 
cc6fccbbefa3: Pull complete 
Digest: sha256:a40e29800d387e3cf9431902e1e7a362e4d819233d68ae39380532c3310091ac
Status: Downloaded newer image for redis:alpine
1:C 10 May 2024 06:36:05.967 # WARNING Memory overcommit must be enabled! Without it, a background save or replication may fail under low memory condition. Being disabled, it can also cause failures without low memory condition, see https://github.com/jemalloc/jemalloc/issues/1328. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
1:C 10 May 2024 06:36:05.967 * oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
1:C 10 May 2024 06:36:05.967 * Redis version=7.2.4, bits=64, commit=00000000, modified=0, pid=1, just started
1:C 10 May 2024 06:36:05.967 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
1:M 10 May 2024 06:36:05.968 * monotonic clock: POSIX clock_gettime
1:M 10 May 2024 06:36:05.968 * Running mode=standalone, port=6379.
1:M 10 May 2024 06:36:05.970 * Server initialized
1:M 10 May 2024 06:36:05.970 * Ready to accept connections tcp

```


#### 2) Next, create a simple container called clickcounter with the image kodekloud/click-counter, link it to the redis container that we created in the previous task and then expose it on the host port 8085


> docker run -d --name=clickcounter --link redis:redis -p 8085:5000 kodekloud/click-counter

```
output:

Unable to find image 'kodekloud/click-counter:latest' locally
latest: Pulling from kodekloud/click-counter
540db60ca938: Pull complete 
a7ad1a75a999: Pull complete 
37ce6546d5dd: Pull complete 
ec9e91bed5a2: Pull complete 
767433e10bb0: Pull complete 
156f0b0493cb: Pull complete 
3fe82d8a2401: Pull complete 
4a41f7c94204: Pull complete 
473063430a4f: Pull complete 
452c68a16ccd: Pull complete 
Digest: sha256:530e4532a718e8f5cbda05844a6c0638ebe8898fa4c4307ee6afbdd5d1f213db
Status: Downloaded newer image for kodekloud/click-counter:latest
b4c2cca212fe222bf6118a801ee1f2287ca05a4162be71d437d578343e6f57af

```


#### 3) Let's clean up the actions carried out in previous steps. Delete the redis and the clickcounter containers.

> docker ps

```
CONTAINER ID   IMAGE                     COMMAND                  CREATED              STATUS              PORTS                    NAMES
b4c2cca212fe   kodekloud/click-counter   "flask run"              About a minute ago   Up About a minute   0.0.0.0:8085->5000/tcp   clickcounter
cbce283392b4   redis:alpine              "docker-entrypoint.s…"   12 minutes ago       Up 11 minutes       6379/tcp                 redis
```

> docker stop b4c cbc

```
b4c
cbc
```
> docker ps -a

```
CONTAINER ID   IMAGE                     COMMAND                  CREATED              STATUS                        PORTS     NAMES
b4c2cca212fe   kodekloud/click-counter   "flask run"              About a minute ago   Exited (137) 13 seconds ago             clickcounter
cbce283392b4   redis:alpine              "docker-entrypoint.s…"   12 minutes ago       Exited (0) 22 seconds ago               redis
```

> docker rm b4c cbc

```
b4c
cbc
```
