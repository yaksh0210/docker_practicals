#####1) Run an instance of kodekloud/simple-webapp with a tag blue and map port 8080 on the container to 38282 on the host.

###### Image: kodekloud/simple-webapp:blue
###### Container Port: 8080
###### Host Port: 38282



> docker run -p 38282:8080 kodekloud/simple-webapp:blue

```
output:


blue: Pulling from kodekloud/simple-webapp
4fe2ade4980c: Already exists 
7cf6a1d62200: Already exists 
f0d690b9e495: Already exists 
fac5d45ad062: Already exists 
a6fc8a0deb7d: Pull complete 
f43c8e496f88: Pull complete 
58ca939f7651: Pull complete 
095a1a007cdb: Pull complete 
Digest: sha256:9caf15476dc60b77c7460791bea8ea5f6ca02b90199aabe088beea83bc943fe5
Status: Downloaded newer image for kodekloud/simple-webapp:blue
 * Serving Flask app "app" (lazy loading)
 * Environment: production
   WARNING: Do not use the development server in a production environment.
   Use a production WSGI server instead.
 * Debug mode: off
 * Running on http://0.0.0.0:8080/


docker ps


CONTAINER ID   IMAGE                          COMMAND                  CREATED              STATUS              PORTS                                           NAMES
c1b859ef4484   kodekloud/simple-webapp:blue   "python app.py"          About a minute ago   Up About a minute   0.0.0.0:38282->8080/tcp                         intelligent_mendeleev


````
