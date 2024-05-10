#### 1) What is a Docker Registry?


```
Answer is : It is a storage and distribution system for named Docker images

```

#### 2) By default, the Docker engine interacts with ?

```
Answer is : DockerHub

```

#### 3) Which command is used for Login to a self-hosted registry?

```
Answer is : Docker login [server]                                                      

```

#### 4) Let practice deploying a registry server on our own.Run a registry server with name equals to my-registry using registry:2 image with host port set to 5000, and restart policy set to always.

> docker run -d -p 5000:5000 --restart=always --name=my-registry registry:2

``` 
Unable to find image 'registry:2' locally
2: Pulling from library/registry
619be1103602: Pull complete 
862815ae87dc: Pull complete 
74e12953df95: Pull complete 
6f0ce73649a0: Pull complete 
ef4f267ce8ed: Pull complete 
Digest: sha256:4fac7a8257b1d7a86599043fcc181dfbdf9c8f57e337db763ac94b0e67c6cfb5
Status: Downloaded newer image for registry:2
dc6af2d1697284a4cb545512807d2a3cdde6f7ff4855a2801b1965af2bd60cab

```

>  docker ps

CONTAINER ID   IMAGE        COMMAND                  CREATED              STATUS              PORTS                    NAMES

dc6af2d16972   registry:2   "/entrypoint.sh /etc…"   About a minute ago   Up About a minute   0.0.0.0:5000->5000/tcp   my-registry


#### 5)Now its time to push some images to our registry server. Let's push two images for now .i.e. nginx:latest and httpd:latest.Note: Don't forget to pull them first.

> docker pull nginx:latest

```
latest: Pulling from library/nginx
b0a0cf830b12: Pull complete 
4d84de5fb9b2: Pull complete 
2818b7b6a9db: Pull complete 
1e5314d67f16: Pull complete 
8066e07ce4f2: Pull complete 
05f7109fea9e: Pull complete 
e58cbd904f7f: Pull complete 
Digest: sha256:32e76d4f34f80e479964a0fbd4c5b4f6967b5322c8d004e9cf0cb81c93510766
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest

```

> docker image tag nginx:latest localhost:5000/nginx:latest

> docker push localhost:5000/nginx:latest

```
The push refers to repository [localhost:5000/nginx]
b80974699bdb: Pushed 
3f69a32a2b31: Pushed 
d75fd41110a4: Pushed 
2e0d92876e9f: Pushed 
a8a738834a4d: Pushed 
bf6cd01dee5e: Pushed 
52ec5a4316fa: Pushed 
latest: digest: sha256:d3fdeec162caf4f4124a4924fcd442610e2eafd0513ed0bd9012585473999eb7 size: 1778

```

> docker pull httpd:latest

```
latest: Pulling from library/httpd
b0a0cf830b12: Already exists 
851c52adaa9b: Pull complete 
4f4fb700ef54: Pull complete 
39d9f60535a6: Pull complete 
943a2b3cf551: Pull complete 
ea83e81966d6: Pull complete 
Digest: sha256:36c8c79f900108f0f09fd4148ad35ade57cba0dc19d13f3d15be24ce94e6a639
Status: Downloaded newer image for httpd:latest
docker.io/library/httpd:latest

```

> docker image tag httpd:latest localhost:5000/httpd:latest

> docker push localhost:5000/httpd:latest

```
The push refers to repository [localhost:5000/httpd]
dba1169a4ef8: Pushed 
ed8b961e754f: Pushed 
53920c8b9c11: Pushed 
5f70bf18a086: Pushed 
46176a0cbe9f: Pushed 
52ec5a4316fa: Mounted from nginx 
latest: digest: sha256:1cfdddb545e2ced605763ad7d6f72c27f88e72d0ba26bcb57bb3d41c57d991c5 size: 1572

```

* To check the list of images pushed

> curl -X GET localhost:5000/v2/_catalog


``` {"repositories":["httpd","nginx"]} ```

#### 6) Let's remove all the dangling images we have locally. Use docker image prune -a to remove them. How many images do we have now?Note: Make sure we don't have any running containers except our registry-sever. To get list of images use: docker image ls

> docker image prune -a

```
WARNING! This will remove all images without at least one container associated to them.
Are you sure you want to continue? [y/N] y
Deleted Images:
untagged: httpd:latest
untagged: httpd@sha256:36c8c79f900108f0f09fd4148ad35ade57cba0dc19d13f3d15be24ce94e6a639
untagged: localhost:5000/httpd:latest
untagged: localhost:5000/httpd@sha256:1cfdddb545e2ced605763ad7d6f72c27f88e72d0ba26bcb57bb3d41c57d991c5
deleted: sha256:67c2fc9e3d849b21a35b4c96f5ad8ec4dc9b73ca44c56537039e8c6f3054db0a
deleted: sha256:f936a5242a64ac31b67a82b97893ed11b3714567e39362890bad496374029486
deleted: sha256:87a86ebdb0e8643ca908f058814c42066199d4b348258a8018aad90c68803591
deleted: sha256:8cbaa3d8954887877518ed80f6807ecb380f67b618820d91c627a15b90d60079
deleted: sha256:8b2b346ba36bb622138e1fcc1a3e419df2c340f34ee47d1849ed0b5a49b9d8b5
deleted: sha256:1e7a9c8fd5183d741333e1a8e1ab8c1d0a67dbb5936b717c486232d18fbbe319
untagged: mysql:latest
untagged: mysql@sha256:a43f6e7e7f3a5e5b90f857fbed4e3103ece771b19f0f75880f767cf66bbb6577
deleted: sha256:8189e588b0e8fcc95b0d764d6f7bdb55b5b41e9249157177d73781058f603ca9
deleted: sha256:48c450c06ed83938e899fb0b77b2e9e35094015b503bb5e88de6c2d93f445241
deleted: sha256:c5d77efb49ec3a7a74ab898b9da9217ec78fa9bee47018409025467611d60329
deleted: sha256:de0c00e28b37cc33347f02709e0a6a2f17637b1e761fb96616861ed345bd34f6
deleted: sha256:cc635684e233946f93fe008e0322c86e15cbb97b56c58d269a5f8f9da15d973d
deleted: sha256:0b795b85d567512d79a544b1b74f21108339156cbbc78d16921e96a2a69f687b
deleted: sha256:16e250c36f4c0e1085512653edd47fd03b60d230ddb575aabc8eb224d96e668f
deleted: sha256:d023b92a46a5fa8fa8d54387e6d3cb0c73997fefc64ec9000eab0ee1c550ef45
deleted: sha256:f1c1643119168a94089eab1c9126cda0ee6056a4bb4b18e27a7dcacdf4823972
deleted: sha256:b147319dd21e8994e6d2fb3bb58a8278c5a72f39488e1f1cff94fc73f1089eb9
deleted: sha256:ff7c2b28c0dfaa63d0d30b7a5069bf526b0f6492143110381351bbf7d07b4baf
deleted: sha256:caefa4e45110eab274ebbdbc781f9227229f947f8718cee62ebeff1aac8f1d5b
untagged: ubuntu:latest
untagged: ubuntu@sha256:67211c14fa74f070d27cc59d69a7fa9aeff8e28ea118ef3babc295a0428a6d21
deleted: sha256:08d22c0ceb150ddeb2237c5fa3129c0183f3cc6f5eeb2e7aa4016da3ad02140a
deleted: sha256:b93c1bd012ab8fda60f5b4f5906bf244586e0e3292d84571d3abb56472248466
untagged: kodekloud/simple-webapp-mysql:latest
untagged: kodekloud/simple-webapp-mysql@sha256:92943d2b3ea4a1db7c8a9529cd5786ae3b9999e0246ab665c29922e9800d1b41
deleted: sha256:129dd9f673673e9e8507ac837dcd9eaa3906469c10ef4aa63d0cac1f1dfa6b3a
deleted: sha256:07711c2005c750fa9c42f5667ec657d7f5126f710915cf917cf5c0e9e3871242
deleted: sha256:69dbe0a61b055e5e63706bc76a875220e02769e880d1846c6f965c2f4b1b1dfe
deleted: sha256:5978a6831cce81b23e657b11150010eb8acf463a183cbe540eb6c769314a0f8a
deleted: sha256:93099f51e789a3d87e77501591ab260ca2ff9b8532a78f9fc6bebaa2d5ffcad4
deleted: sha256:15df614f20bc13c6da75c43616dec28d17908970491a562820fabbc11a1e562c
deleted: sha256:a8dc474c5cce41198ea9a334a54bd7d59043f86c32c3b8e3f0d76a52adf09cf2
deleted: sha256:362e5432c5954e9f081657f369b00d821cecd10274b8885f1d6fd1b2e8c1a405
deleted: sha256:73046094a9b835e443af1a9d736fcfc11a994107500e474d0abf399499ed280c
untagged: postgres:latest
untagged: postgres@sha256:6cc97262444f1c45171081bc5a1d4c28b883ea46a6e0d1a45a8eac4a7f4767ab
deleted: sha256:ceccf204404e5efe764f2d4d97e6977db04062579d525d9cb445cf93e0f0fef4
deleted: sha256:5581e2a0252cdb4f2b1847cfd9300122841787cd0a9ba13e095425b22c08bb05
deleted: sha256:b8d9a959ce0f6039bf4061ddedb320c05b9b049b5bd8dabb2b5f9d697fdc4e0e
deleted: sha256:d426781ae8413908a52d86fb8f28319b834625c5c6b194e3d122d1b1eb179d87
deleted: sha256:ee6f16055bfd3ad8bcc92a9af3567c69c0bb499cbc2c2b9a2f2ccafa3538504b
deleted: sha256:42c973890245849bff76e03def91ceacb87da92a19fa5aa7eab58975a811c683
deleted: sha256:179015cc5c69fea24583ca7a52a8ba75dd363310d17461b6eb9b430c0d69a37e
deleted: sha256:9362c3f758a9916eb7e2262af8e63d7f1b0a45818e7ac033c9152ecf049933d0
deleted: sha256:b47ed6c8bc9fa1548ed586316aa7a0e27b34937efb1b3c4ad5742ae3a5d63f8c
deleted: sha256:a603ddfeb1e19bb984a56b96e96cc987d8e27621390a9bc1b11f7003ff357e7d
deleted: sha256:ca073f3da5fc959ed40fff93ae9a550ddb14916b3f8bd620235d306f5e9d3d64
deleted: sha256:fd2d7bb88deba0351caf0ee032dac84272a04e489fd055407cddd740009e329c
deleted: sha256:2c3cc0e91a94c04e5446f3a8061970073053850ce8093a46ba819b8e59af1dee
untagged: redis:latest
untagged: redis@sha256:f50031a49f41e493087fb95f96fdb3523bb25dcf6a3f0b07c588ad3cdbe1d0aa
deleted: sha256:eca1379fe8b541831fd5ce4a252c263db0cef4efbfd428a94225dc020aaeb1af
deleted: sha256:21acda8c08f1a6109e2fb61ed010d368ee6581cf30128cdaab0e6b91dabffc22
deleted: sha256:aafc83c9f9299ba7a3af08ab0b1f822340278803714695fd2a96351fe89b37ea
deleted: sha256:644ab96acc6e4232dc7be6f1855b27f5f3534b17b9e9c19ae2557991b99487db
deleted: sha256:6e75f4867056adfca8dfafbb0e94a525064797e4f0a106bca817b5afce47af73
deleted: sha256:84e4c46eefa83bc327e4e356365ec03a3ee1f691d181235e5b69e36663f7dd57
deleted: sha256:ed7b0ef3bf5bbec74379c3ae3d5339e666a314223e863c70644f7522a7527461
untagged: alpine:latest
untagged: alpine@sha256:124c7d2707904eea7431fffe91522a01e5a861a624ee31d03372cc1d138a3126
deleted: sha256:9ed4aefc74f6792b5a804d1d146fe4b4a2299147b0f50eaf2b08435d7b38c27e
deleted: sha256:f1417ff83b319fbdae6dd9cd6d8c9c88002dcd75ecf6ec201c8c6894681cf2b5
untagged: kodekloud/simple-webapp:latest
untagged: kodekloud/simple-webapp@sha256:e5355b4c7804f453d79de75d6659ee702eeebbe30c02d9f1ce6602a96b576e57
deleted: sha256:c6e3cd9aae3645a98dd69c15b048614603efce6cda26c60f5f7e867ef68f729f
deleted: sha256:33833b97952fc68d999bc3bccaad23687ea6a939724e0130c151dc973ba8f2d3
deleted: sha256:a3dd002bb33a1cdb83aface983ea0d268be1b4ffda0e42ce72aa5c22ced6701f
deleted: sha256:12e8c893d121075ced84d32b967f6de75ff67e1cf7c9b66b63636bdf630ac12c
deleted: sha256:4785d1dd03a24d6b30c9342db24ac2254d01362e7f3b3f28f55a00e4858f85e5
deleted: sha256:9de207c08e3d729c3b9c451d87e109144cdc6e2e71f4fcad80c9cbf99879d8bb
deleted: sha256:0a2679c979afc5eb30764613ae1fa22199b872610f709f556b9f35bc0717e3f1
deleted: sha256:df64d3292fd6194b7865d7326af5255db6d81e9df29f48adde61a918fbd8c332
untagged: nginx:latest
untagged: nginx@sha256:32e76d4f34f80e479964a0fbd4c5b4f6967b5322c8d004e9cf0cb81c93510766
untagged: localhost:5000/nginx:latest
untagged: localhost:5000/nginx@sha256:d3fdeec162caf4f4124a4924fcd442610e2eafd0513ed0bd9012585473999eb7
deleted: sha256:1d668e06f1e534ab338404ba891c37d618dd53c9073dcdd4ebde82aa7643f83f
deleted: sha256:682c535e9134a5a3ed2363f4f3157b1775d6909ba09821c89834487cdc987145
deleted: sha256:8d4ac15aab86b75e75a1f3b4f6606872df9435cd84245e5084a287c3b678f4fc
deleted: sha256:97747011f58480c1b05123187af96370ee38c15c57a98f0b8da53fcf2042e222
deleted: sha256:503533d0672e01e9deeff1aaab9495f54783ae70a4036a77ed715208d62f8a50
deleted: sha256:60f69ec2ab71ac63bcc19f116118e03118eabd578128d2fa75fdd6a476459ed7
deleted: sha256:e995270c3fe3253ceaa35882876089c2ef357c502ce8f1f7e683946d1fdf6f62
deleted: sha256:52ec5a4316fadc09a4a51f82b8d7b66ead0d71bea4f75e81e25b4094c4219061

Total reclaimed space: 1.506GB

```

> docker image ls

```
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
registry     2         d6b2c32a0f14   7 months ago   25.4MB

```

#### 7) Let's clean up after ourselves.Stop and remove the my-registry container.

> docker ps

```
CONTAINER ID   IMAGE        COMMAND                  CREATED          STATUS          PORTS                    NAMES

dc6af2d16972   registry:2   "/entrypoint.sh /etc…"   12 minutes ago   Up 12 minutes   0.0.0.0:5000->5000/tcp   my-registry

```
> docker stop dc6

```dc6```

> docker rm dc6

```dc6```
