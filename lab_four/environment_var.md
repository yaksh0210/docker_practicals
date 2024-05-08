#### 1) Inspect the environment variables set on the running container and identify the value set to the APP_COLOR variable.

> docker ps
```
output:

CONTAINER ID   IMAGE                     COMMAND           CREATED          STATUS          PORTS      NAMES
5501a369ab5f   kodekloud/simple-webapp   "python app.py"   37 seconds ago   Up 36 seconds   8080/tcp   quizzical_wescoff

```

```
docker inspect 5501
[
    {
        "Id": "5501a369ab5f309ca3d38dad7ea5738136fdc8b7c776669f5e5087e6628db20a",
        "Created": "2024-05-08T12:22:14.327424855Z",
        "Path": "python",
        "Args": [
            "app.py"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 1227,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2024-05-08T12:22:14.952336694Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:c6e3cd9aae3645a98dd69c15b048614603efce6cda26c60f5f7e867ef68f729f",
        "ResolvConfPath": "/var/lib/docker/containers/5501a369ab5f309ca3d38dad7ea5738136fdc8b7c776669f5e5087e6628db20a/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/5501a369ab5f309ca3d38dad7ea5738136fdc8b7c776669f5e5087e6628db20a/hostname",
        "HostsPath": "/var/lib/docker/containers/5501a369ab5f309ca3d38dad7ea5738136fdc8b7c776669f5e5087e6628db20a/hosts",
        "LogPath": "/var/lib/docker/containers/5501a369ab5f309ca3d38dad7ea5738136fdc8b7c776669f5e5087e6628db20a/5501a369ab5f309ca3d38dad7ea5738136fdc8b7c776669f5e5087e6628db20a-json.log",
        "Name": "/quizzical_wescoff",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "host",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "ConsoleSize": [
                0,
                0
            ],
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": null,
            "BlkioDeviceWriteBps": null,
            "BlkioDeviceReadIOps": null,
            "BlkioDeviceWriteIOps": null,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "KernelMemory": 0,
            "KernelMemoryTCP": 0,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/affcfe5d75fd20c30e244ea76f30cdd0dbe8c67acce78bfa733bb7726af7b507-init/diff:/var/lib/docker/overlay2/009a4658f99085f09f8b4657086b3db457b62c4fb6ccdb0da2d9e6557f9a5780/diff:/var/lib/docker/overlay2/b2feabc65b4665d946750c72164d84a10a46262bbf9593cb115035e5b23d9c8c/diff:/var/lib/docker/overlay2/d88063b12719f039c423a30b5d48389831d9bbc10ae67a7c4363fd39221e324e/diff:/var/lib/docker/overlay2/44028c86ccd32ce29e1ba42a17b6a62c49636cc30522be9f640acbecae40e286/diff:/var/lib/docker/overlay2/1e3d9b662653e0b63032f3011d96c87f5ccb838eb314335fdee04ad6a7975a75/diff:/var/lib/docker/overlay2/cffd17e9af7ffe676424f81dd8e4aaae8bc6b0045d2fda32b2871c25d954ed0e/diff:/var/lib/docker/overlay2/7a98e284a33d9e53c5fbe93c268b78f98c908782514b11939aa254c7c8cb29f5/diff",
                "MergedDir": "/var/lib/docker/overlay2/affcfe5d75fd20c30e244ea76f30cdd0dbe8c67acce78bfa733bb7726af7b507/merged",
                "UpperDir": "/var/lib/docker/overlay2/affcfe5d75fd20c30e244ea76f30cdd0dbe8c67acce78bfa733bb7726af7b507/diff",
                "WorkDir": "/var/lib/docker/overlay2/affcfe5d75fd20c30e244ea76f30cdd0dbe8c67acce78bfa733bb7726af7b507/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "5501a369ab5f",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "8080/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "APP_COLOR=pink",
                "PATH=/usr/local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "LANG=C.UTF-8",
                "GPG_KEY=0D96DF4D4110E5C43FBFB17F2D347EA6AA65421D",
                "PYTHON_VERSION=3.6.6",
                "PYTHON_PIP_VERSION=18.1"
            ],
            "Cmd": null,
            "Image": "kodekloud/simple-webapp",
            "Volumes": null,
            "WorkingDir": "/opt",
            "Entrypoint": [
                "python",
                "app.py"
            ],
            "OnBuild": null,
            "Labels": {}
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "d9b8f18cbc2df3a6c86eb0ba588568cc056fd070a547b7fbb09ad23e3b6e43e9",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {
                "8080/tcp": null
            },
            "SandboxKey": "/var/run/docker/netns/d9b8f18cbc2d",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "6949a9e70dc027663b9db1fea60f611e63ad857f18123e6ed7d8c3e4b3e8b73d",
            "Gateway": "172.12.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.12.0.2",
            "IPPrefixLen": 24,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:0c:00:02",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "fdca51ceb7a4bef7dbc5cb0065fca989f174e76203ba1f4fc7d8e8a4732806dc",
                    "EndpointID": "6949a9e70dc027663b9db1fea60f611e63ad857f18123e6ed7d8c3e4b3e8b73d",
                    "Gateway": "172.12.0.1",
                    "IPAddress": "172.12.0.2",
                    "IPPrefixLen": 24,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:0c:00:02",
                    "DriverOpts": null
                }
            }
        }
    }
]

```

ANS: PINK

#### 2) Run a container named blue-app using image kodekloud/simple-webapp and set the environment variable APP_COLOR to blue. Make the application available on port 38282 on the host. The application listens on port 8080.

> docker run -p 38282:8080 --name blue-app -e APP_COLOR=blue -d kodekloud/simple-webapp

```

output:

a1707f6a7e2538973643a01f700017f2176e731478b45470fa04fd7641f3c987


docker exec -it blue-app env

PATH=/usr/local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
HOSTNAME=a1707f6a7e25
TERM=xterm
APP_COLOR=blue
LANG=C.UTF-8
GPG_KEY=0D96DF4D4110E5C43FBFB17F2D347EA6AA65421D
PYTHON_VERSION=3.6.6
PYTHON_PIP_VERSION=18.1
HOME=/root

```

#### 3) Deploy a mysql database using the mysql image and name it mysql-db.

> docker run -d -e MYSQL_ROOT_PASSWORD=db_pass123 --name mysql-db mysql

```

output:

cdd46056c97cc86afa7556f10458eff1d149c855c3f0f6a77c702ffac45b67b4

docker exec -it mysql-db env

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
HOSTNAME=cdd46056c97c
TERM=xterm
MYSQL_ROOT_PASSWORD=db_pass123
GOSU_VERSION=1.16
MYSQL_MAJOR=8.0
MYSQL_VERSION=8.0.33-1.el8
MYSQL_SHELL_VERSION=8.0.33-1.el8
HOME=/root

```
