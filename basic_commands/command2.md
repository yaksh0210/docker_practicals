### 1) sudo docker run -it [repo][command]  = this will let you logged in container of runnning repo to perform tasks without asking any login credetntials

> sudo docker run -it nginx bash
 ``` output: root@8941324cf347:/# ```

### 2) sudo docker run -d --name "{name}" [repo] = this will create a manual name for the container

> docker run -d --name webapp nginx:1.14-alpine

``` 34ed5167f7469accadc8c4ee2f6839b88335adbd4ece26809ef2479fd97f44a4 ```
 
> docker ps  
```
CONTAINER ID   IMAGE               COMMAND                  CREATED          STATUS          PORTS     NAMES
34ed5167f746   nginx:1.14-alpine   "nginx -g 'daemon of…"   14 seconds ago   Up 12 seconds   80/tcp    webap
```
