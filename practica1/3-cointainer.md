# Contenedores

### Crear un contenedor
Para crear un nuevo contenedor Docker a partir de una imagen específica, pero sin iniciarlo automáticamente. 

```
docker create --name <nombre contenedor> <nombre imagen>:<tag>
```
Crear el contenedor  **srv-web** usando la imagen nginx version alpine
![image](https://github.com/cristian-sangucho-a/2024A-ISWD633-GR2/assets/93937686/fab12995-7ce8-4f5b-a445-8d99650d67a9)


Si creas un contenedor en Docker sin asignarle un nombre específico utilizando la opción --name, Docker asignará automáticamente un nombre aleatorio al contenedor. Este nombre suele consistir en una combinación de palabras y números.  

Crear el contenedor usando la imagen hello-world
![image](https://github.com/cristian-sangucho-a/2024A-ISWD633-GR2/assets/93937686/9c9c6c46-c617-400e-b699-2fad7a0b5b9f)


### Listar los contenedores ejecutándose o no

```
docker ps -a
```

### Para iniciar un contenedor

```
docker start <nombre contenedor o identificador>
```
Iniciar el contenedor srv-web 
![image](https://github.com/cristian-sangucho-a/2024A-ISWD633-GR2/assets/93937686/b0903168-c893-4286-9512-ede7deab278f)


### Listar los contenedores ejecutándose
```
docker ps 
docker ps | grep <nombre contenedor>
```

### Para detener un contenedor

```
docker stop <nombre contenedor>
```

### Para crear un contenedor y ejecutarlo inmediatamente

```
docker run --name <nombre contenedor> <nombre imagen>:<tag>
```
![Ecosistema de Docker](imagenes/dockerRun.PNG)

Crear y ejecutar inmediatamente el contenedor **srv-web2** usando la imagen nginx:alpine
![image](https://github.com/cristian-sangucho-a/2024A-ISWD633-GR2/assets/93937686/37cb3d30-7753-4949-9978-6b403048796c)


**¿Qué sucede luego de la ejecución del comando?**
Crea los recursos necesarios en el host para ejecutar el contenedor

Cuando ejecutas un contenedor en primer plano sin la opción -d (modo detach), el contenedor captura la entrada estándar (stdin) del terminal, lo que significa que el terminal queda "atrapado" y no puedes introducir más comandos hasta que detengas el contenedor.

### Para crear un contenedor y ejecutarlo inmediatamente sin estar vinculados al mismo
-d: Es la opción que indica a Docker que ejecute el contenedor en segundo plano (en modo "detach").
Cuando un contenedor se ejecuta en segundo plano, Docker devuelve el control al terminal inmediatamente después de iniciar el contenedor, lo que permite al usuario seguir ejecutando otros comandos en el mismo terminal sin que el contenedor detenga la interacción.

```
docker run -d --name <nombre contenedor> <nombre imagen>:tag
```
Crear y ejecutar inmediatamente el contenedor **srv-web3** en modo detach usando la imagen nginx:alpine
![image](https://github.com/cristian-sangucho-a/2024A-ISWD633-GR2/assets/93937686/7030460a-0f44-45f0-941d-8262c3cacb64)


### Para eliminar un contenedor

```
docker rm <nombre contenedor>
```
Eliminar el contenedor que se creó a partir de la imagen hello-world 
![image](https://github.com/cristian-sangucho-a/2024A-ISWD633-GR2/assets/93937686/8876e7e9-0504-4960-94a0-39a8c8cb25ca)


Verificar que el contenedor que se eliminó
![image](https://github.com/cristian-sangucho-a/2024A-ISWD633-GR2/assets/93937686/03b5c357-a0a0-45db-ae63-6d5fbcbe0e1c)


### Para eliminar un contenedor que esté ejecutándose

```
docker rm -f <nombre contenedor>
```
Eliminar el contenedor **srv-web3** 
![image](https://github.com/cristian-sangucho-a/2024A-ISWD633-GR2/assets/93937686/9f432b6e-2b31-4c66-87e5-603b16d5bc68)

Verificar que el contenedor que se eliminó
![image](https://github.com/cristian-sangucho-a/2024A-ISWD633-GR2/assets/93937686/c40d2975-609f-427c-a88e-4063e5f20ebd)


### Para inspecionar un contenedor 

Inspeccionar el contenedor **srv-web** 
````
C:\Users\intel\dockerContainers>docker inspect srv-web
[
    {
        "Id": "0ba4200832b3a7bbe6e7d9c06d0315ab0d3c90995359e304202f74237823e44e",
        "Created": "2024-06-13T00:21:03.838339452Z",
        "Path": "/docker-entrypoint.sh",
        "Args": [
            "nginx",
            "-g",
            "daemon off;"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 846,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2024-06-13T00:24:32.901012748Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:70ea0d8cc5300acde42073a2fbc0d28964ddb6e3c31263d92589c2320c3ccba4",
        "ResolvConfPath": "/var/lib/docker/containers/0ba4200832b3a7bbe6e7d9c06d0315ab0d3c90995359e304202f74237823e44e/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/0ba4200832b3a7bbe6e7d9c06d0315ab0d3c90995359e304202f74237823e44e/hostname",
        "HostsPath": "/var/lib/docker/containers/0ba4200832b3a7bbe6e7d9c06d0315ab0d3c90995359e304202f74237823e44e/hosts",
        "LogPath": "/var/lib/docker/containers/0ba4200832b3a7bbe6e7d9c06d0315ab0d3c90995359e304202f74237823e44e/0ba4200832b3a7bbe6e7d9c06d0315ab0d3c90995359e304202f74237823e44e-json.log",
        "Name": "/srv-web",
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
            "NetworkMode": "bridge",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "ConsoleSize": [
                30,
                120
            ],
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
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": [],
            "BlkioDeviceWriteBps": [],
            "BlkioDeviceReadIOps": [],
            "BlkioDeviceWriteIOps": [],
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": [],
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
                "/sys/firmware",
                "/sys/devices/virtual/powercap"
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
                "LowerDir": "/var/lib/docker/overlay2/3a46901a421bcfa85546d4ae3bebb2e99f28f236a44435ab406f1dfa81edbf91-init/diff:/var/lib/docker/overlay2/65546b098e734e6d11fef9f369d2f9ede8da93402b898684b6f1acb7c76cee6a/diff:/var/lib/docker/overlay2/12834aa257c2bda39c606ee1b923cfeb80cb43cd96aaf88d58ec28f46461c6c0/diff:/var/lib/docker/overlay2/5bde6b74e612adbf6bae6296c544da88748563593d0da44543a3cd0dde915637/diff:/var/lib/docker/overlay2/5b8a2ab7f358ca4e79ac4036c238028dadfe571c0b543f0bbe36de09affee12a/diff:/var/lib/docker/overlay2/89f8267cf864af785d77ec66f63072608284334bdeb088779e39c2207987a101/diff:/var/lib/docker/overlay2/ef6f29c4b000882010ea9dfa55e33306740ce8f8683fcb8470e3a7e71b392ad4/diff:/var/lib/docker/overlay2/05ab8991e1021aeaa92330e676bd625e1502daf4a66fdb44d7d5f35fb8c2fd68/diff:/var/lib/docker/overlay2/ba0fbe196de5b4445ebcb795568b0532511258eefbe97403e2394fa00b227aee/diff",
                "MergedDir": "/var/lib/docker/overlay2/3a46901a421bcfa85546d4ae3bebb2e99f28f236a44435ab406f1dfa81edbf91/merged",
                "UpperDir": "/var/lib/docker/overlay2/3a46901a421bcfa85546d4ae3bebb2e99f28f236a44435ab406f1dfa81edbf91/diff",
                "WorkDir": "/var/lib/docker/overlay2/3a46901a421bcfa85546d4ae3bebb2e99f28f236a44435ab406f1dfa81edbf91/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "0ba4200832b3",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": true,
            "AttachStderr": true,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "NGINX_VERSION=1.27.0",
                "PKG_RELEASE=2",
                "NJS_VERSION=0.8.4",
                "NJS_RELEASE=2"
            ],
            "Cmd": [
                "nginx",
                "-g",
                "daemon off;"
            ],
            "Image": "nginx:alpine",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": [
                "/docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {
                "maintainer": "NGINX Docker Maintainers \u003cdocker-maint@nginx.com\u003e"
            },
            "StopSignal": "SIGQUIT"
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "53ad25c2a441aa3bb2f375c924a3799c52c637c8b12479215f516ddb39fca8b2",
            "SandboxKey": "/var/run/docker/netns/53ad25c2a441",
            "Ports": {
                "80/tcp": null
            },
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "8840643e3c3cc31c0b872668b1f0b6faea3da26675da307883aac4f3ab0f448c",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.2",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:02",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "MacAddress": "02:42:ac:11:00:02",
                    "NetworkID": "bfd354b01a0d25da919814634d2f461e9afbb0fbac4eaed1d55c4dffdb837114",
                    "EndpointID": "8840643e3c3cc31c0b872668b1f0b6faea3da26675da307883aac4f3ab0f448c",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "DriverOpts": null,
                    "DNSNames": null
                }
            }
        }
    }
]
````
