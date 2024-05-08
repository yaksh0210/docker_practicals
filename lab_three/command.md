#### 1) Build a docker image using the Dockerfile and name it webapp-color. No tag to be specified.

> docker build -t webapp-color .

``` Output:

lecting MarkupSafe>=2.0
  Downloading MarkupSafe-2.0.1-cp36-cp36m-manylinux_2_5_x86_64.manylinux1_x86_64.manylinux_2_12_x86_64.manylinux2010_x86_64.whl (30 kB)
Collecting dataclasses
  Downloading dataclasses-0.8-py3-none-any.whl (19 kB)
Collecting zipp>=0.5
  Downloading zipp-3.6.0-py3-none-any.whl (5.3 kB)
Collecting typing-extensions>=3.6.4
  Downloading typing_extensions-4.1.1-py3-none-any.whl (26 kB)
Installing collected packages: zipp, typing-extensions, MarkupSafe, importlib-metadata, dataclasses, Werkzeug, Jinja2, itsdangerous, click, flask
Successfully installed Jinja2-3.0.3 MarkupSafe-2.0.1 Werkzeug-2.0.3 click-8.0.4 dataclasses-0.8 flask-2.0.3 importlib-metadata-4.8.3 itsdangerous-2.0.1 typing-extensions-4.1.1 zipp-3.6.0
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv
WARNING: You are using pip version 21.2.4; however, version 21.3.1 is available.
You should consider upgrading via the '/usr/local/bin/python -m pip install --upgrade pip' command.
Removing intermediate container df7fcb8644d2
 ---> e2ad727d9ece

...

```


#### 2) Run an instance of the image webapp-color and publish port 8080 on the container to 8282 on the host


> docker run -p 8282:8080 webapp-color
``` 
output:

This is a sample web application that displays a colored background. 
 A color can be specified in two ways. 

 1. As a command line argument with --color as the argument. Accepts one of red,green,blue,blue2,pink,darkblue 
 2. As an Environment variable APP_COLOR. Accepts one of red,green,blue,blue2,pink,darkblue 
 3. If none of the above then a random color is picked from the above list. 
 Note: Command line argument precedes over environment variable.


No command line argument or environment variable. Picking a Random Color =green
 * Serving Flask app 'app' (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: off
 * Running on all addresses.
   WARNING: This is a development server. Do not use it in a production deployment.
 * Running on http://172.12.0.2:8080/ 
```

#### 3) what is the base system of python:3.6 

> docker run python:3.6 cat /etc/*release*

```
output:

PRETTY_NAME="Debian GNU/Linux 11 (bullseye)"
NAME="Debian GNU/Linux"
VERSION_ID="11"
VERSION="11 (bullseye)"
VERSION_CODENAME=bullseye
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"
```

#### 4) What is the approximate size of the webapp-color image?

> docker images
REPOSITORY                      TAG           IMAGE ID       CREATED         SIZE
webapp-color                    latest        921d58cfa4c5   6 minutes ago   913MB
redis                           latest        eca1379fe8b5   12 months ago 


==> 913 MB


#### 5) Build a new smaller docker image by modifying the same Dockerfile and name it webapp-color and tag it lite. Hint: Find a smaller base image for python:3.6. Make sure the final image is less than 150MB

> first  modify Dockerfile to use python:3.6-alpine then docker build -t webapp-color:lite .

```
output:


Sending build context to Docker daemon  125.4kB
Step 1/6 : FROM python:3.6-alpine
3.6-alpine: Pulling from library/python
59bf1c3509f3: Pull complete 
8786870f2876: Pull complete 
acb0e804800e: Pull complete 
52bedcb3e853: Pull complete 
b064415ed3d7: Pull complete 
Digest: sha256:579978dec4602646fe1262f02b96371779bfb0294e92c91392707fa999c0c989
Status: Downloaded newer image for python:3.6-alpine
 ---> 3a9e80fa4606
Step 2/6 : RUN pip install flask
 ---> Running in cc295ee984f1
Collecting flask
  Downloading Flask-2.0.3-py3-none-any.whl (95 kB)
Collecting click>=7.1.2
  Downloading click-8.0.4-py3-none-any.whl (97 kB)
Collecting Werkzeug>=2.0
  Downloading Werkzeug-2.0.3-py3-none-any.whl (289 kB)
Collecting itsdangerous>=2.0
  Downloading itsdangerous-2.0.1-py3-none-any.whl (18 kB)
Collecting Jinja2>=3.0
  Downloading Jinja2-3.0.3-py3-none-any.whl (133 kB)
Collecting importlib-metadata
  Downloading importlib_metadata-4.8.3-py3-none-any.whl (17 kB)
Collecting MarkupSafe>=2.0
  Downloading MarkupSafe-2.0.1-cp36-cp36m-musllinux_1_1_x86_64.whl (29 kB)
Collecting dataclasses
  Downloading dataclasses-0.8-py3-none-any.whl (19 kB)
Collecting typing-extensions>=3.6.4
  Downloading typing_extensions-4.1.1-py3-none-any.whl (26 kB)
Collecting zipp>=0.5
  Downloading zipp-3.6.0-py3-none-any.whl (5.3 kB)
Installing collected packages: zipp, typing-extensions, MarkupSafe, importlib-metadata, dataclasses, Werkzeug, Jinja2, itsdangerous, click, flask
Successfully installed Jinja2-3.0.3 MarkupSafe-2.0.1 Werkzeug-2.0.3 click-8.0.4 dataclasses-0.8 flask-2.0.3 importlib-metadata-4.8.3 itsdangerous-2.0.1 typing-extensions-4.1.1 zipp-3.6.0
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv
WARNING: You are using pip version 21.2.4; however, version 21.3.1 is available.
You should consider upgrading via the '/usr/local/bin/python -m pip install --upgrade pip' command.
Removing intermediate container cc295ee984f1
 ---> cd3d6649d2ca
Step 3/6 : COPY . /opt/
 ---> acc05f852574
Step 4/6 : EXPOSE 8080
 ---> Running in 3f754c889dc0
Removing intermediate container 3f754c889dc0
 ---> 5ae37ad38387
Step 5/6 : WORKDIR /opt
 ---> Running in 2233c8b882d9
Removing intermediate container 2233c8b882d9
 ---> 42fbba7610e7
Step 6/6 : ENTRYPOINT ["python", "app.py"]
 ---> Running in 44f0890335a5
Removing intermediate container 44f0890335a5
 ---> e15481c520f3
Successfully built e15481c520f3
Successfully tagged webapp-color:lite

```
