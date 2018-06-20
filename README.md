# RestAPI using Python-Flask 
### `Version 0.1`

> This package is built to test and review one main website [CodeJudge](http://console.codejudge.io)

> I am testing the first two milestones. 



## Package contents

	.
	├── app.py				# Master script controlling all endpoints
	├── requirements.txt	# Contains the necessary library downloads along with version to be made by Dockerfile.
	├── Dockerfile			# Command for Docker to run.
	└── README.md

## Docker
### Introduction

Docker is a tool designed to make it easier to create, deploy, and run applications by using containers. Containers allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and ship it all out as one package.

###Installation

Download and install Docker for your own Operating System and boot it. With Docker running, the following execution is to be done on the command line.


### Execution

1) The docker build command to build Docker images from the **Dockerfile** and a “context”.


```shell
 $./path/to/the/folder/ docker build -t restapi .
```

>#### Flags 
>--tag , -t    -> Name and optionally a tag in the ‘name:tag’ format

2) Create a network. When you create a network, Engine creates a non-overlapping subnetwork for the network by default. This subnetwork is not a subdivision of an existing network. It is purely for ip-addressing purposes. Here we override this default and specify subnetwork values directly using the --subnet option.

```shell
 $./path/to/the/folder/ docker network create --subnet=255.255.255.0/16 myDockerNet
```

3)Provided our script has port 5200 exposed and tag name is restapi with myDockerNet as the network name, when an operator executes docker run, the container process that runs is isolated in that it has its own file system, its own networking, and its own isolated process tree separate from the host.


```shell
$./path/to/the/folder/ docker run -d --rm -p 5200:5200 --name restapi --net myDockerNet --ip 255.255.255.1 restapi
```
>#### Flags 
>-d , -d=true    -> To start a container in detached mode.containers started in detached mode exit when the root process used to run the container exits, unless you also specify next flag.

> --rm -> If you use -d with --rm, the container is removed when it exits or when the daemon exits, whichever happens first.

> -p -> Port specifications

> --name -> Conatiner name
> 
> --net -> Network name
> 
> --ip -> Allocated ip from subnet specified before.
> 

Succesful execution of the above commands shall result in successful execution of you API. To access its benefits send relevant requests to the URL and port mentioned in app.py.

### Extra Commands

#### 1)Stop container.
-Provided the container name is restapi.

```shell
$./path/to/the/folder/ docker stop restapi
```

#### 2)Container details.
-List all container currently executing.

```shell
$./path/to/the/folder/ docker container ls
```


