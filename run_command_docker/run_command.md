#### 1) Sudo docker run [module]:[version] = it will help you to download module/container with its specific version using docker you can run this jenkins file with your ip attached with your define port number

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

#### 3) 

> sudo docker run ubuntu:17.10 cat /etc/*release* = it will pull image of ubutnu version 17.10 and also display it's release version via cat /etc/*release* command


```
output

Unable to find image 'ubuntu:17.10' locally
17.10: Pulling from library/ubuntu
4ccdce43d1e0: Pull complete 
c95f13c88d92: Pull complete 
82656eee95ad: Pull complete 
78ff727be57a: Pull complete 
448bb314afa5: Pull complete 
Digest: sha256:3b811ac794645dfaa47408f4333ac6e433858ff16908965c68f63d5d315acf94
Status: Downloaded newer image for ubuntu:17.10
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.10
DISTRIB_CODENAME=artful
DISTRIB_DESCRIPTION="Ubuntu 17.10"
NAME="Ubuntu"
VERSION="17.10 (Artful Aardvark)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 17.10"
VERSION_ID="17.10"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=artful
UBUNTU_CODENAME=artful

```
#### 4) 

> sudo docker run -d ubuntu sleep 1000 = it will run container in sleep mode for 100 sec in background if we run with -d 

```
output

e79ee55a756f1cd407bf0880b504e24232928dbd6ac8256672c95ec83561cca9

sudo docker ps -a (to check running container)

CONTAINER ID   IMAGE             COMMAND                  CREATED              STATUS                      PORTS     NAMES
e79ee55a756f   ubuntu            "sleep 1000"             About a minute ago   Up About a minute                     flamboyant_wright

```
#### 5) 
> sudo docker attach e79ee55a756f1cd407bf0880b504e24232928dbd6ac8256672c95ec83561cca9 = by running this command you can take background process to foreground easily

```
output:

(it will stop run the background process in foreground and then and only go towards next process)

```


#### 6) sudo docker inspect [container_id] = will provide detail information about container in json format 


> sudo docker inspect 0325


```
output:


[
    {
        "Id": "032547a176ab62f1e04f53de65e2da96d3ea72a5fd9af4f41a2f15e9702d86f1",
        "Created": "2024-05-08T05:59:54.855243869Z",
        "Path": "/usr/bin/tini",
        "Args": [
            "--",
            "/usr/local/bin/jenkins.sh"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 181723,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2024-05-08T05:59:55.371661598Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:6f99dfc713097f3add8d5f6fa4553c277db2c818e55824338d5b0466bae4ca86"
...

```
#### 7) sudo docker run -p [portnumber]:[port_we_define] = this will help you to run container on your defined port number


> sudo docker run -p 8080:8080 jenkins/jenkins

```
output 

Running from: /usr/share/jenkins/jenkins.war
webroot: /var/jenkins_home/war
2024-05-08 06:29:26.695+0000 [id=1]	INFO	winstone.Logger#logInternal: Beginning extraction from war file
2024-05-08 06:29:27.921+0000 [id=1]	WARNING	o.e.j.s.handler.ContextHandler#setContextPath: Empty contextPath
2024-05-08 06:29:27.999+0000 [id=1]	INFO	org.eclipse.jetty.server.Server#doStart: jetty-10.0.20; built: 2024-01-29T20:46:45.278Z; git: 3a745c71c23682146f262b99f4ddc4c1bc41630c; jvm 17.0.11+9
2024-05-08 06:29:28.270+0000 [id=1]	INFO	o.e.j.w.StandardDescriptorProcessor#visitServlet: NO JSP Support for /, did not find org.eclipse.jetty.jsp.JettyJspServlet
2024-05-08 06:29:28.325+0000 [id=1]	INFO	o.e.j.s.s.DefaultSessionIdManager#doStart: Session workerName=node0
2024-05-08 06:29:28.912+0000 [id=1]	INFO	hudson.WebAppMain#contextInitialized: Jenkins home directory: /var/jenkins_home found at: EnvVars.masterEnvVars.get("JENKINS_HOME")
2024-05-08 06:29:29.030+0000 [id=1]	INFO	o.e.j.s.handler.ContextHandler#doStart: Started w.@1de0a46c{Jenkins v2.456,/,file:///var/jenkins_home/war/,AVAILABLE}{/var/jenkins_home/war}
2024-05-08 06:29:29.042+0000 [id=1]	INFO	o.e.j.server.AbstractConnector#doStart: Started ServerConnector@5e8ac0e1{HTTP/1.1, (http/1.1)}{0.0.0.0:8080}
2024-05-08 06:29:29.052+0000 [id=1]	INFO	org.eclipse.jetty.server.Server#doStart: Started Server@1ae67cad{STARTING}[10.0.20,sto=0] @3034ms
2024-05-08 06:29:29.053+0000 [id=27]	INFO	winstone.Logger#logInternal: Winstone Servlet Engine running: controlPort=disabled
2024-05-08 06:29:29.277+0000 [id=35]	INFO	jenkins.InitReactorRunner$1#onAttained: Started initialization
2024-05-08 06:29:29.302+0000 [id=43]	INFO	jenkins.InitReactorRunner$1#onAttained: Listed all plugins
2024-05-08 06:29:30.167+0000 [id=41]	INFO	jenkins.InitReactorRunner$1#onAttained: Prepared all plugins
2024-05-08 06:29:30.171+0000 [id=41]	INFO	jenkins.InitReactorRunner$1#onAttained: Started all plugins
2024-05-08 06:29:30.176+0000 [id=46]	INFO	jenkins.InitReactorRunner$1#onAttained: Augmented all extensions
2024-05-08 06:29:30.351+0000 [id=35]	INFO	jenkins.InitReactorRunner$1#onAttained: System config loaded
2024-05-08 06:29:30.351+0000 [id=39]	INFO	jenkins.InitReactorRunner$1#onAttained: System config adapted
2024-05-08 06:29:30.352+0000 [id=38]	INFO	jenkins.InitReactorRunner$1#onAttained: Loaded all jobs
2024-05-08 06:29:30.353+0000 [id=44]	INFO	jenkins.InitReactorRunner$1#onAttained: Configuration for all jobs updated
2024-05-08 06:29:30.374+0000 [id=61]	INFO	hudson.util.Retrier#start: Attempt #1 to do the action check updates server
2024-05-08 06:29:30.810+0000 [id=36]	INFO	jenkins.install.SetupWizard#init: 

*************************************************************
*************************************************************
*************************************************************

Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:

b97503b8837347fba2a058***********

This may also be found at: /var/jenkins_home/secrets/initialAdminPassword

*************************************************************
*************************************************************
*************************************************************

2024-05-08 06:29:46.994+0000 [id=61]	INFO	h.m.DownloadService$Downloadable#load: Obtained the updated data file for hudson.tasks.Maven.MavenInstaller
2024-05-08 06:29:46.996+0000 [id=61]	INFO	hudson.util.Retrier#start: Performed the action check updates server successfully at the attempt #1
2024-05-08 06:29:56.865+0000 [id=36]	INFO	jenkins.InitReactorRunner$1#onAttained: Completed initialization
2024-05-08 06:29:56.881+0000 [id=26]	INFO	hudson.lifecycle.Lifecycle#onReady: Jenkins is fully up and running

docker ps 

CONTAINER ID   IMAGE             COMMAND                  CREATED          STATUS          PORTS                                                  NAMES
426267ecb6ba   jenkins/jenkins   "/usr/bin/tini -- /u…"   33 seconds ago   Up 32 seconds   0.0.0.0:8080->8080/tcp, :::8080->8080/tcp, 50000/tcp   loving_austin

```

#### 8) docker run -p 8080:8080 -v /root/my-jenkins-data:/var/jenkins_home -u root jenkins = this will save a backup of a conatiner or we can say volume of container at define path after -v 

```
output:


docker run -p 8080:8080 -v /root/my-jenkins-data:/var/jenkins_home -u root jenkins/jenkins

Running from: /usr/share/jenkins/jenkins.war
webroot: /var/jenkins_home/war
2024-05-08 07:17:40.402+0000 [id=1]	INFO	winstone.Logger#logInternal: Beginning extraction from war file
2024-05-08 07:17:40.522+0000 [id=1]	WARNING	o.e.j.s.handler.ContextHandler#setContextPath: Empty contextPath
2024-05-08 07:17:40.611+0000 [id=1]	INFO	org.eclipse.jetty.server.Server#doStart: jetty-10.0.20; built: 2024-01-29T20:46:45.278Z; git: 3a745c71c23682146f262b99f4ddc4c1bc41630c; jvm 17.0.11+9
2024-05-08 07:17:40.900+0000 [id=1]	INFO	o.e.j.w.StandardDescriptorProcessor#visitServlet: NO JSP Support for /, did not find org.eclipse.jetty.jsp.JettyJspServlet
2024-05-08 07:17:40.958+0000 [id=1]	INFO	o.e.j.s.s.DefaultSessionIdManager#doStart: Session workerName=node0
2024-05-08 07:17:41.600+0000 [id=1]	INFO	hudson.WebAppMain#contextInitialized: Jenkins home directory: /var/jenkins_home found at: EnvVars.masterEnvVars.get("JENKINS_HOME")
2024-05-08 07:17:41.735+0000 [id=1]	INFO	o.e.j.s.handler.ContextHandler#doStart: Started w.@3bc735b3{Jenkins v2.456,/,file:///var/jenkins_home/war/,AVAILABLE}{/var/jenkins_home/war}
2024-05-08 07:17:41.752+0000 [id=1]	INFO	o.e.j.server.AbstractConnector#doStart: Started ServerConnector@609db43b{HTTP/1.1, (http/1.1)}{0.0.0.0:8080}
2024-05-08 07:17:41.766+0000 [id=1]	INFO	org.eclipse.jetty.server.Server#doStart: Started Server@2bfc268b{STARTING}[10.0.20,sto=0] @2040ms
2024-05-08 07:17:41.766+0000 [id=27]	INFO	winstone.Logger#logInternal: Winstone Servlet Engine running: controlPort=disabled
2024-05-08 07:17:41.980+0000 [id=33]	INFO	jenkins.InitReactorRunner$1#onAttained: Started initialization
2024-05-08 07:17:42.152+0000 [id=32]	INFO	jenkins.InitReactorRunner$1#onAttained: Listed all plugins
2024-05-08 07:17:45.670+0000 [id=43]	INFO	jenkins.InitReactorRunner$1#onAttained: Prepared all plugins
2024-05-08 07:17:45.689+0000 [id=36]	INFO	jenkins.InitReactorRunner$1#onAttained: Started all plugins
2024-05-08 07:17:45.710+0000 [id=45]	INFO	jenkins.InitReactorRunner$1#onAttained: Augmented all extensions
2024-05-08 07:17:46.072+0000 [id=32]	INFO	h.p.b.g.GlobalTimeOutConfiguration#load: global timeout not set
2024-05-08 07:17:46.903+0000 [id=33]	INFO	jenkins.InitReactorRunner$1#onAttained: System config loaded
2024-05-08 07:17:46.904+0000 [id=33]	INFO	jenkins.InitReactorRunner$1#onAttained: System config adapted
2024-05-08 07:17:46.949+0000 [id=42]	INFO	jenkins.InitReactorRunner$1#onAttained: Loaded all jobs
2024-05-08 07:17:46.962+0000 [id=42]	INFO	jenkins.InitReactorRunner$1#onAttained: Configuration for all jobs updated
2024-05-08 07:17:47.002+0000 [id=46]	INFO	jenkins.InitReactorRunner$1#onAttained: Completed initialization
2024-05-08 07:17:47.122+0000 [id=26]	INFO	hudson.lifecycle.Lifecycle#onReady: Jenkins is fully up and running

```






