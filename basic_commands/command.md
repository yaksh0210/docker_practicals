### 1) sudo docker run [module] = through this we can run nginx, sql , ansible etc images using docker 

``` command: sudo docker run nginx ```

```
output:

Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
b0a0cf830b12: Pull complete 
8ddb1e6cdf34: Pull complete 
5252b206aac2: Pull complete 
988b92d96970: Pull complete 
7102627a7a6e: Pull complete 
93295add984d: Pull complete 
ebde0aa1d1aa: Pull complete 
Digest: sha256:ed6d2c43c8fbcd3eaa44c9dab6d94cb346234476230dc1681227aa72d07181ee
Status: Downloaded newer image for nginx:latest
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2024/05/03 06:23:57 [notice] 1#1: using the "epoll" event method
2024/05/03 06:23:57 [notice] 1#1: nginx/1.25.5
2024/05/03 06:23:57 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14) 
2024/05/03 06:23:57 [notice] 1#1: OS: Linux 5.15.0-105-generic
2024/05/03 06:23:57 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1024:524288
2024/05/03 06:23:57 [notice] 1#1: start worker processes
2024/05/03 06:23:57 [notice] 1#1: start worker process 29
2024/05/03 06:23:57 [notice] 1#1: start worker process 30
2024/05/03 06:23:57 [notice] 1#1: start worker process 31
2024/05/03 06:23:57 [notice] 1#1: start worker process 32
2024/05/03 06:23:57 [notice] 1#1: start worker process 33
2024/05/03 06:23:57 [notice] 1#1: start worker process 34
2024/05/03 06:23:57 [notice] 1#1: start worker process 35
2024/05/03 06:23:57 [notice] 1#1: start worker process 36
```

### 2) sudo docker ps = It helps to list out currently running containers

``` command: sudo docker ps ```

```
output:

CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS     NAMES
28e5b9ca7ce1   nginx     "/docker-entrypoint.…"   54 seconds ago   Up 54 seconds   80/tcp    hardcore_kilby
```

### 3) sudo docker ps -a = it will help to list out all runnning as well as previously stopped containers

``` command: sudo docker ps -a ```
```
output:

CONTAINER ID   IMAGE             COMMAND                  CREATED              STATUS                         PORTS     NAMES
28e5b9ca7ce1   nginx             "/docker-entrypoint.…"   About a minute ago   Up About a minute              80/tcp    hardcore_kilby
5698d0b8e16b   docker/whalesay   "cowsay Hello-World!"    47 minutes ago       Exited (0) 46 minutes ago                nostalgic_yalow
83bde0e414f4   ubuntu            "bash"                   57 minutes ago       Exited (0) 55 minutes ago                sleepy_chebyshev
4e29a6cafc51   ubuntu            "bash"                   57 minutes ago       Exited (0) 57 minutes ago                lucid_albattani
a97183ffe4f4   hello-world       "/hello"                 About an hour ago    Exited (0) About an hour ago             sweet_black
```

### 4) sudo docker stop [name_container] = it will stopped the running container 

``` command: docker stop upbeat_shockley```

``` output: upbeat_shockley ```


### 5) sudo docker rm [Name_continer] = it will permenently remove the container from the process


``` command: sudo docker ps -a ```

```
output:

CONTAINER ID   IMAGE             COMMAND                  CREATED             STATUS                         PORTS     NAMES
802acd77a105   nginx             "/docker-entrypoint.…"   4 minutes ago       Exited (0) 3 minutes ago                 upbeat_shockley
28e5b9ca7ce1   nginx             "/docker-entrypoint.…"   14 minutes ago      Exited (0) 8 minutes ago                 hardcore_kilby
5698d0b8e16b   docker/whalesay   "cowsay Hello-World!"    59 minutes ago      Exited (0) 59 minutes ago                nostalgic_yalow
83bde0e414f4   ubuntu            "bash"                   About an hour ago   Exited (0) About an hour ago             sleepy_chebyshev
4e29a6cafc51   ubuntu            "bash"                   About an hour ago   Exited (0) About an hour ago             lucid_albattani
a97183ffe4f4   hello-world       "/hello"                 About an hour ago   Exited (0) About an hour ago             sweet_black
```
``` command: docker rm sweet_black ```
``` output: sweet_black ```


``` command: docker ps -a ```
```

output:

CONTAINER ID   IMAGE             COMMAND                  CREATED             STATUS                         PORTS     NAMES
802acd77a105   nginx             "/docker-entrypoint.…"   4 minutes ago       Exited (0) 3 minutes ago                 upbeat_shockley
28e5b9ca7ce1   nginx             "/docker-entrypoint.…"   14 minutes ago      Exited (0) 9 minutes ago                 hardcore_kilby
5698d0b8e16b   docker/whalesay   "cowsay Hello-World!"    About an hour ago   Exited (0) 59 minutes ago                nostalgic_yalow
83bde0e414f4   ubuntu            "bash"                   About an hour ago   Exited (0) About an hour ago             sleepy_chebyshev
4e29a6cafc51   ubuntu            "bash"                   About an hour ago   Exited (0) About an hour ago             lucid_albattani
```

### 6) sudo docker images = it will display list of all image created using docker previously 


``` command: sudo docker images ```
```
output:

REPOSITORY        TAG       IMAGE ID       CREATED         SIZE
ubuntu            latest    bf3dc08bfed0   3 days ago      76.2MB
nginx             latest    7383c266ef25   9 days ago      188MB
hello-world       latest    d2c94e258dcb   12 months ago   13.3kB
docker/whalesay   latest    6b362a9f73eb   8 years ago     247MB
```


### 7) sudo docker rmi [repository_name] = it is used to delete an image from docker which is not in running or stopped state to make sure entier container is deleted with its image file 

``` command: sudo docker rmi nginx ```

```
output:

Untagged: nginx:latest
Untagged: nginx@sha256:ed6d2c43c8fbcd3eaa44c9dab6d94cb346234476230dc1681227aa72d07181ee
Deleted: sha256:7383c266ef252ad70806f3072ee8e63d2a16d1e6bafa6146a2da867fc7c41759
Deleted: sha256:284239a88aa2a215c3ab52265554c83612e73efea682954be87982e370c98f49
Deleted: sha256:05092aeb22646fda43f7e25fc418b7e21942112b84bc0f5b2466f6206372e099
Deleted: sha256:04de068faa51d09eb7e1e52a4911ffc894d2ab2640db17e77eab84ca22cada85
Deleted: sha256:08b0ce47715b739cb30d253768b913e0d81a466f34b84addf24dc78ae61579e8
Deleted: sha256:90f1c22432ddccd4e1f6cd933c964e71a8f6bdd39b035f60cf4b8153820db7b5
Deleted: sha256:0a9e7b5b5ef53ef025d0cb5798a2a49aa52289a5d9ad86687b428c19a63a3e22
Deleted: sha256:52ec5a4316fadc09a4a51f82b8d7b66ead0d71bea4f75e81e25b4094c4219061
```

### 8) sudo docker pull [repo] = it is used to pull on image and not runnning the container 

``` command: sudo docker pull nginx ```
```
output:

Using default tag: latest
latest: Pulling from library/nginx
b0a0cf830b12: Pull complete 
8ddb1e6cdf34: Pull complete 
5252b206aac2: Pull complete 
988b92d96970: Pull complete 
7102627a7a6e: Pull complete 
93295add984d: Pull complete 
ebde0aa1d1aa: Pull complete 
Digest: sha256:ed6d2c43c8fbcd3eaa44c9dab6d94cb346234476230dc1681227aa72d07181ee
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest
```
