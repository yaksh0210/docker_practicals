#### 1) What location are the files related to the docker containers and images stored?

ANSWER : /var/lib/docker


#### 2) What directory under /var/lib/docker are the files related to the container alpine-3 image stored?

> cd /var/lib/docker/containers/

```
output : it changes the directory to /var/lib/docker/containers/

```
> docker ps -a

```

CONTAINER ID   IMAGE     COMMAND     CREATED         STATUS                     PORTS     NAMES

aa03354a1ad6   alpine    "/bin/sh"   3 minutes ago   Exited (0) 3 minutes ago             alpine-3
82f5638ae6f3   alpine    "/bin/sh"   3 minutes ago   Exited (0) 3 minutes ago             alpine-2
cce05c4c83c8   alpine    "/bin/sh"   3 minutes ago   Exited (0) 3 minutes ago             alpine-1

Answer: aa03354a1ad6dabe3570a877f0de41005bf6d5f3b183dac4f74debdb6b9713f4

```
#### 3) Run a mysql container named mysql-db using the mysql image. Set database password to db_pass123

> docker run -d --name=mysql-db -e MYSQL_ROOT_PASSWORD=db_pass123 mysql

```
7f709c45fc87583fb9c07898df9ffc7a648db9ec19b6650546d7e01821aaebfb
```

> docker ps

```
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                 NAMES

7f709c45fc87   mysql     "docker-entrypoint.s…"   7 seconds ago   Up 6 seconds   3306/tcp, 33060/tcp   mysql-db

```

#### 4) Run a mysql container again, but this time map a volume to the container so that the data stored by the container is stored at /opt/data on the host. Use the same name : mysql-db and same password: db_pass123 as before. Mysql stores data at /var/lib/mysql inside the container.

> docker run -v /opt/data:/var/lib/mysql -d --name mysql-db -e MYSQL_ROOT_PASSWORD=db_pass123 mysql

```
867679f9d5c3caec391587c70a1f0ca0265620f1ca7f871cb6ffa53d4c6de4a9

```

> docker ps

```
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                 NAMES

867679f9d5c3   mysql     "docker-entrypoint.s…"   5 seconds ago   Up 4 seconds   3306/tcp, 33060/tcp   mysql-db

```

#### 5) Disaster strikes.. again! And the database crashed again. But this time we have the data stored at /opt/data directory. Re-deploy a new mysql instance using the same options as before.Just run the same command as before. Here it is for your convenience: docker run -v /opt/data:/var/lib/mysql -d --name mysql-db -e MYSQL_ROOT_PASSWORD=db_pass123 mysql

> docker run -v /opt/data:/var/lib/mysql -d --name mysql-db -e MYSQL_ROOT_PASSWORD=db_pass123 mysql 

```
9960f4327863ea01a8c76937615eab66bd292698b4ef8ea7e928bb9d1d968190
```
> docker ps

```
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                 NAMES

9960f4327863   mysql     "docker-entrypoint.s…"   24 seconds ago   Up 22 seconds   3306/tcp, 33060/tcp   mysql-db
```


#### 6) Fetch data and make sure it is present.command: sh get-data.sh

> sh get-data.sh 

```

mysql: [Warning] Using a password on the command line interface can be insecure.
id      Name    Phone   Email
1       Kareem  130-5655        Duis.volutpat.nunc@quamCurabitur.org
2       Ruby    1-584-149-0770  Nulla.tempor@vitaeorciPhasellus.org
3       Rowan   199-8663        consectetuer.adipiscing.elit@Sedmalesuada.co.uk
4       Alisa   220-6017        elementum.sem.vitae@enimMauris.edu
5       Ella    731-0337        fermentum@nec.net
6       Tiger   658-4480        quis.diam@odiovelest.net
7       Felix   1-274-848-3378  Mauris.vel@arcu.com
8       Karina  1-390-796-3451  sagittis.semper@odioapurus.co.uk
9       Davis   605-8539        venenatis.vel@risusDonecnibh.com
10      Mohammad        1-590-174-1489  ornare.sagittis.felis@natoque.ca
11      Zane    362-1770        Aenean.euismod@condimentum.co.uk
12      Piper   1-231-386-6903  nunc.sed.pede@nascetur.ca
13      Marshall        1-383-729-4990  Cras.interdum.Nunc@neceuismod.ca
14      Zena    241-6641        Fusce.mollis.Duis@lobortis.org
15      Abdul   1-748-387-9935  eget.lacus.Mauris@Crasvehicula.com
16      Chase   1-401-241-9169  ante.dictum.mi@nascetur.org
17      Zahir   921-0663        non@nonummyutmolestie.edu
18      Brenda  1-691-909-5827  Quisque.ac@magnaCras.co.uk
19      Laura   1-562-983-9565  Quisque.ornare.tortor@sollicitudinadipiscing.ca
20      Madison 1-348-737-0587  Quisque.varius@Intinciduntcongue.org
21      Tanek   991-6278        dignissim.magna@Pellentesqueutipsum.net
22      Dakota  893-0792        Nullam.enim.Sed@nulla.net
23      Boris   1-297-302-5792  non.sollicitudin@eleifendegestasSed.co.uk
24      Celeste 723-6729        mauris.rhoncus@eunulla.edu
25      Connor  1-203-901-7531  et@loremipsumsodales.edu
26      Perry   1-756-607-9187  eros.turpis@tristiquepharetra.co.uk
27      Hayfa   1-609-407-3019  non.lobortis.quis@malesuadafringilla.net
28      Todd    343-0454        id.erat@arcu.org
29      Fuller  881-7273        non.feugiat.nec@adipiscingelit.net
30      Rama    1-927-605-0610  nonummy.ultricies.ornare@malesuada.co.uk

```
