# Mastering Docker Second Edition
[Mastering Docker - Second Edition: Master this widely used containerization tool eBook: Russ McKendrick, Scott Gallagher: Amazon.co.uk: Kindle Store](https://www.amazon.co.uk/Mastering-Docker-Second-Master-containerization-ebook/dp/B06X3X8JQ7/ref=sr_1_1?ie=UTF8&qid=1510399892&sr=8-1&keywords=Mastering+Docker+Second+Edition)
- - - -
## Docker Overview

### Understanding Docker

* General principle of docker to allow developers to wrap their code in a container to provide a repeatable environment. 

### Differences between dedicated hosts, virtual machines, and docker

* Technically, docker is a _container-management system_ which helps you easily manage linux containers (LXC).
* They allow you to create images in virtual environments on a machine and run commands against those images.
* The commands you use on the containers run locally on that container, so you can repeatedly run them on duplicates of that container and expect the same results
* Remembering that containers are not exactly virtual machines and not dedicated machines such as a server, here are the differences in their architectures 


![](Mastering%20Docker%20Second%20Edition/Screen%20Shot%202017-11-10%20at%2015.12.54.png)

![](Mastering%20Docker%20Second%20Edition/Screen%20Shot%202017-11-10%20at%2015.13.25.png)


* The key difference here is that with Docker we do not need a complete operating system each time we want to spin up a container unlike virtual machines -> This makes docker containers considerably smaller than virtual machines and dedicated machines
	* This is due to the fact that a docker image does not have a kernel. It believes that it does due to the configuration of the binaries that are come with a desired container.
	

### The Docker Command-line Client


* To get a full list of docker commands, use `docker help`
* To get help with a specific command, use `docker <COMMAND> —help`
* To run a container, use `docker container run <containerName>
* To pull a container image, use `docker image pull <containerName>`
* To run a pulled container of a specific port, with a specific name, use `docker container run -d —name <nameToCallContainer> -p <hostMachinePort:YourMachinePort> <originalContainerName>`
	* As an example, using the nginx container, which we will call nginx-test, and mapping port :8080 on the host machine to :80 on our machine `docker container run -d --name nginx-test -p 8080:80 nginx`

### The Docker Ecosystem - Key Terms

* Docker Compose - Tool that allows you define and share multi-container definitions
* Docker Machine - A tool to launch Docker hosts on multiple platforms
* Docker Hub - A repository for your Docker images
* Docker Store - Official store for docker images and plugins.
* Docker Swarm - Multi-host-aware orchestration tool
* Docker Cloud - Docker’s Container as a Service (CaaS). 

- - - -

## Building Container Images

### Introducing Docker Files

* Docker Files are plain text files that have a series of user defined commands.
* When the user runs `docker image build`, these commands are executed sequentially which in turn produce a docker container image

```
FROM alpine:latest
   LABEL maintainer="Russ McKendrick <russ@mckendrick.io>"
   LABEL description="This example Dockerfile installs NGINX."
   RUN apk add --update nginx && \
           rm -rf /var/cache/apk/* && \
           mkdir -p /tmp/nginx/
   COPY files/nginx.conf /etc/nginx/nginx.conf
   COPY files/default.conf /etc/nginx/conf.d/default.conf
     
Building Container Images
    ADD files/html.tar.gz /usr/share/nginx/
   EXPOSE 80/tcp
   ENTRYPOINT ["nginx"]
   CMD ["-g", "daemon off;"]
```


### Docker File In Depth

#### From

* `From` command tells docker which base you would like to use as your image (Eg ubuntu, apline, tomcat7 ….)
* You can specify that you want to use the latest of a specific base by using `<baseName>:latest`

#### Label

* `label`Is used to add extra information to the image, such as a version number or description. 
* Its good practice to have a limit on the number of labels you have on a container -> Try to only keep the bare minimum. 
* Ideally, follows the label schema defined here: http://label-s chema.org/.
* You can view a containers labels by using `docker image inspect <IMAGE_ID>`
* You can filters by doing the following: `docker image inspect -f {{.Config.Labels}} <IMAGE_ID>`
* Its good practice to define you labels when you create a container from an image, rather than adding them at build tie. 

#### Run

* `RUN` command is where you define steps that your image should do to get itself into a desired state, such as installing certain software, or configuring directories.
* You can define multiple commands in a `RUN` block:
```
 RUN apk add --update nginx && \
           rm -rf /var/cache/apk/* && \
           mkdir -p /tmp/nginx/
```
	* The \ is used to split the command over several lines, rather than having one mahoooosive line. 
* Each Run command is considered a “Layer” in the container. 
* So if you have 3 run commands, you’ll have 3 layers of run commands.
* Its good practice to set the commands that are not often changed in any way at the beginning of the file, with often changed commands at the bottom
	* Its prevents layers being rebuild when nothing has changed to their run command. 
* It is also good practice to chain you run commands so you minimise the amount of layers you have. 

#### COPY and ADD

* The `COPY` command takes a source file and overwrites another specified file:
`COPY files/nginx.conf /etc/nginx/nginx.conf`
	* This copies `files/nginx.conf` to `/ect/nginx/nginx.conf`
* The `ADD` command automatically uploads, uncompresses and puts the resulting folders and files in the path you specify .
`ADD files/html.tar.gz /usr/share/nginx/`
* You can use this command to add contents from remove sources like so
`ADD http://www.myremotesource.com/files/html.tar.gz /usr/share/nginx/`
	* It should be noted, that when you use `ADD` with files from a remote source, the files WILL NOT BE UNCOMPRESSED. You’ll need to deal with this separately. 

#### Expose

*  Allows you to define what port, and what protocol  will be exposed at runtime.
* Does not map the port to the host machine, but rather opens the port to allow access to the container.

Example of opening a port 80, and that we should use TCP to access the container

`EXPOSE 80/tcp`

#### Entrypoint and cmd

* `ENTRYPOINT` defines a service or program that should be ran when the container is spun up.
* Think of it as a terminal command that you want to run.
* For example `ENTRYPOINT [“nginx”]` is equivalent to: `nginx` in the terminal
* `CMD` can be used along side `ENTRYPOINT` to specify flags that should be passed to the command executed
* For an example the following to code snippets, the first being in the docker file, and the second in the terminal, are equivalent :

```
ENTRYPOINT ["nginx"]
   CMD ["-g", "daemon off;"]
```
`nginx -g daemon off;` 
* **You can only have one entry point**
* `CMD` on its own should be used to run any software contained in the image, along with the arguments you want provide in the following format: `[“executable”, “param1”, “param2”…]`

Example	:
`CMD [“Java”,’-v’]`

#### User
* `USER` instruction allows you to specify a username to be used when a command is ran. 
* This can be used on the `RUN` instruction, `CMD` instruction, and `ENTRYPOINT` instruction

#### Workdir

* Allows you to set the working directory for the set of instructions that the `USER` instruction can use (`RUN`,`CMD`,`ENTRYPOINT`)
* It also allows you to use the `CMD` and `ADD` instructions as well

#### ONBUILD

* Allows you to stash a set of commands that will be used when the image is again as a base image for a container. 
* As example, when you pull a container, `ONBUILD` will set the container into a specific state so everyone will have containers sharing identical states

Example: Running some commands when the user uses `build container`

```
   ONBUILD RUN apk update && apk upgrade && rm -rf /var/cache/apk/*
```

#### ENV

* Allows you to set environment variables within the image when its built and when its executed. These can be overwritten when you launch your image 

### Best Practices

* You should try to get into the habit of using a .dockerignore file. We will cover the .dockerignore file in the next section; it will seem very familiar if you are used to using a .gitignore file. It will essentially ignore the items you have specified in the file during the build process.
* Remember to only have one Dockerfile per folder to help you organise your containers.
* Use version control for your Dockerfile; just like any other text-based document, version control will help you move forward, but only backward as necessary.
* Minimize the number of packages you need per image. One of the biggest goals you want to achieve while building your images is to keep them as small as possible. Not installing unnecessary packages will greatly help in achieving this goal.
* Execute only one application process per container. Every time you need a new application, it is best practice to use a new container to run that application in. While you can couple commands into a single container, it's best to separate them. Keep things simple; over complicating your Dockerfile will add bloat and also potentially cause you issues further down the line.
* Learn by example, Docker themselves have quite a detailed style guide for publishing the official images they host on Docker Hub, documented at https :github.com/docker-library/official-images/.

### Building Docker Images


* To build an image, use `docker build`
* You can also use the `docker build --help` to see what is available

#### Build An Image From a Dockerfile

* Docker comes with a `.dockerignore` file. This file excludes files or folders you don’t want to include in the docker build.
	* This should be placed in the folder where the Dockerfile was placed.
	* Try to keep the items in the ignore file to a minimum.

#### Building Custom Images using Dockerfiles.

* When you run `docker build`, it runs against a docker file and builds an image of that file
* There are two ways of building an image:
	* Specifying the `-f` switch when using the docker build command. 
`   $ docker image build --file <path_to_Dockerfile> --tag <REPOSITORY>:<TAG> .`

		* Generally, <REPOSITORY> is the username you signed up for docker, or, if you want to store it locally, you use `local`
```
docker image build --file /path/to/your/dockerfile --tag local:dockerfile-example .
```

	* You can also build the docker  image by placing the docker file with any resources needed to create the image in a report folder. Then run the command with the `.` operator at the end (This says run the command in the specified folder

```
  docker image build --tag local:dockerfile-example .
```


* You can inspect the image once it has been build using `docker image ls`

#### Using an existing container

* Its considerably easier to build a base image by using one of the official images from the Docker Hub.
* Docker also keeps docker files for these in their [GitHub](https://github.com/docker) repositories 
* They also state you can spin up a container, alter it during runtime and then saving it. This is not recommended so I’m not covering this, but you can find it on page 43

### Building From Scratch

* When we think of build a container from scratch - This is build a container without any base image. Its literally from scratch.
* Docker will provide you with most of the hard work done for you in a TAR file called scratch
* You need to `FROM scratch`, then add a base image like so:

```
FROM scratch
   ADD files/alpine-minirootfs-3.6.1-x86_64.tar /
   CMD ["/bin/sh"]
```

* Once you have a DOckefile, and an operating system in a TAR file, you can build your image as you would any other docker image by dong the following:

```
docker image build --tag local:fromscratch .
```

* Once built, you can test the image by running the following?:

```
   $ docker container run -it --name alpine-test local:fromscratch /bin/sh
```


* You can check this image by using `cat /ect/*release`

#### Using Environment Variables in your Dockerfile

* You can use environment variables in your Dockerfile by using the `ENV` instruction
```
   ENV <key> <value>
   ENV username admin
```
* You can alternatively do it in the following way:
```
 ENV <key>=<value>
 ENV username=admin
```

* The difference between these two formats is if you use `=`, you can assign multiple environment variables per line

`ENV username=admin database=db1 tableprefix=pr2_ `

* You can beige what environment variables are set on an image by doing the following:
`docker image inspect <IMAGE_ID>`

### Putting it all together

* Below is an example DockerFile that demonstrates the following:
	* Set an environment variable to define which version of PHP we would like to install
	* Install Apache2 and our chosen PHP version
	* Set up the image so Apache2 starts without issue
	* Remove the default index.html and add an index.php file that displays the results of the phpinfo command
	* Expose port 80 on the container
	* Set Apache so it is the default process


```
 FROM alpine:latest
   LABEL maintainer="Russ McKendrick <russ@mckendrick.io>"
   LABEL description="This example Dockerfile installs Apache & PHP."
   ENV PHPVERSION 7
   RUN apk add --update apache2 php${PHPVERSION}-apache2 php${PHPVERSION} && \
       rm -rf /var/cache/apk/* && \
       mkdir /run/apache2/ && \
       rm -rf /var/www/localhost/htdocs/index.html && \
       echo "<?php phpinfo(); ?>" > /var/www/localhost/htdocs/index.php && \
       chmod 755 /var/www/localhost/htdocs/index.php
   EXPOSE 80/tcp
   ENTRYPOINT ["httpd"]
   CMD ["-D", "FOREGROUND"]
```

* You can build the image using : `docker build --tag local/apache-php:7 .`
*  To launch the container, on port 9090, you can run it by:
`docker container run -d -p 9090:80 --name apache-php5 local/apache-php:5`

- - - -
## Sorting and Distributing Images

* Below we will talk about different services that store docker images.

### Docker Hub

CONTINUE

### Docker Registry
CONTINUE
### Third-party Registries
 CONTINUE

- - - -
## Managing Containers

* Will be covering the following:
	* Docker container commands
		* The basics
		* Interacting with your containers
		* Logs and process information
		* Resource Limits
		* Container states and miscellaneous commands
		* Removing containers
	* Docker networking and volume


### Docker Container Commands

* Launching a container:  `docker container run <name>`
* Getting container information: `docker container ls -all` or `docker container ls`
* Removing containers: `docker container rm <name>`
* Laughing container on a specific port: `docker container run -p <hostMachinePort:portOnYourLocalMachine> <name>`
* To spin up a container with a specific name: `docker container run —-name <nameYouWantToCallContiner> <imageName>`
* To download the image `docker container run -d <containerToDownload>`

### Interacting With Your Containers

#### Attach

* `attach` allows you to interact a process which is running in the container via your terminal
* You do this by `docker container attach <containerName>`
* If you do stop a process while in an attached state, you can start it back up using `docker container start <containerName>`

#### Exec
* This spawns a new process in the container that you can interact with.
* Example of spawning the cat command in a container: `docker container exec <containerName> cat <FileToCat>`
* This is a one use process -> you need to specify what you want to do do with the process when you run the exec command
* You can keep STDIN open for the container by passing the `-i` flag

#### Logs

* Allows you to interact with the stdout stream of the container. 
* Docker uses this to print out whats happening in the container
* To print previous logs:  `docker container logs <containerName>` 
* To print logs in real time: `docker container logs -f <containerName>`
* you can use `exec` and `date` to find out what has happened at specific times and dates:
	* `docker container exec <containerName> date`
* To filter based on things happening after a specific time:
	 `docker container logs --since 2017-06-24T15:00 -t <containerName>`

#### Top
* Lists the processes that are running within the container
 `docker container top <containerName>`

#### Stats

* Provides real-time information on a specified container, or if no container name is passed, all running containers

`docker container stats <optionalContainerName>`

### Resource Limits

* This allows you to set resource limits for the container, such as memory and CPU priority.

` docker container run —cpu-shares <value> —memory <value>M <containerName>`

* If you want to update the memory of a running container, you can do this using `update` and `-—memory-swap`
`docker container update --cpu-shares 512 --memory <oldValue>M  --memory-swap <newValue>M  <containerName>`


Example

`docker container update --cpu-shares 512 --memory 128M --memory-swap 256M nginx-test`


### Container States and Miscellaneous Commands

* Running `docker container ls -a` lets you know what states they are in along with various other information

#### Pausing a container

* To pause a container, you use `docker container pause <containerName>`
* To unpuase the container use `docker container unease <containerName>`

#### Stop, Start, Restart and Kill

* Stop command stops the container running the foreground of your system
* This sends a process called `SIGTERM` to kill it, if its not killed during the grace period , `SIGKILL` is sent to finish the job.

`docker container stop <containerName>`

* You can specify a grace period using the `-t` flag

`docker container stop -t <timeToWaitInSeconds> <containerName>`

* The start command starts processes back up. However, unlike pause and unpause, it starts the command from scratch, rather than resuming

`docker container start <containerName>`

* Restart command is a combination of stop + start commands. You can pass it the -t command to make it stop after a set time

`docker container restart -t <gracePeriodTime> <containerName>`

* Kill command sends `SIGKILL` immediately to a container

`docker container kill <containerName>`

### Removing Containers

* You can use prune to remove all containers that are in an exited state
* This will need confirmation from you to continue however

`docker container prune`

* To remove a container that is any state, use rm. You will need to pass the -f flag to prevent warnings occurring

`docker container rm -f <containerName>`

### Miscellaneous Commands

* The create command is just like the run command, however it does not start the container, it just prepares and configures it:

`docker container create <containerName>`

* The port command displays the port, and all port mappings
`docker container port <containerName>`

* You can check what files have been added, or modified since the container has started compared to its original image by using diff

`docker container diff <containerName>`

### Docker Networking

* You’re able to link containers together on a network.
* You can use `--network` to define the network that a container is ran on.

```
docker container run -d --name moby-counter --network moby-counter -p 8080:80 russmckendrick/moby-counter
```

* You can remove containers from a network using `docker network prune`
	* Remember prune needs a stopped container!

### Docker Volumes

* Docker containers can define volumes and working directories using `VOLUME` and `WORKDIR`

```
...
 RUN mkdir /data && chown redis:redis /data
   VOLUME /data
   WORKDIR /data
...
```

* If these are defined, you can get information on the volume using `docker volume ls`
* However, thats pretty useless. you can use exec with /data to get cleaner information:
```
docker container exec <containerName> ls -lhat /data
```

* If you want to override the volume with your own volume, you can use the `volume` command

```
docker volume create <volumeName>
```

* The `inspect` command allows you to inspect the volume in a container

```
docker volume inspect <containerName>
```

* To remove volumes, use `docker volume prune`
	* Again, remember to turn off the container!!!

### Quick Chapter Summary

* There are 4 main commands to understand:
	* `docker container [command]`
	* `docker network [command]`
	* `docker volume [command]`
	* `docker image [command]`
- - - -


## Docker Machine

* Docker machines biggest strength is its ability to provide consistent interfaces to the following cloud providers:
	* Amazon Web Services
	* Microsoft Azure
	* DigitalOcean
	* Exoscale
	* Google Compute Engine
	* Rackspace
	* IBM SoftLayer
* It also supports the following self-hosted VM/Cloud platform
	* Microsoft Hyper-V
	* OpenStack
	* VMware vSphere
* And the following locally hosted hypervisors:
	* Oracle VirtualBox
	* VMware Fusion
	* VMware Workstation

### Deploying Local Docker Hosts with Docker Machine

* We’re going to use Oracle Virtual Box to act as a our local Docker Machine
* To do this, use the command:
```
docker-machine create --driver virtualbox docker-local
```

* If you then open VirtualBox, you should have the following:
![](Mastering%20Docker%20Second%20Edition/Screenshot%202017-11-12%2013.49.14.png)

* You’ll then need to configure the local docker client to connect to the newly launched docker host. You do this by:
```
docker-machine env docker-local
```

* To get information on the docker server and the client, use `docker version`
* To list the currently configured docker hosts, use `docker-machine ls`
	* The * in the ACTIVE column indicates which docker host your local client is currently configured to interact with. (Can also check this with `docker-machine active`)
* To connect yourself to the Docker host using SSH, use the following:
```
docker-machine ssh docker-local
```

* To find the IP address of your local docker `docker-machine ip docker-local`

* There are several commands to manage your Docker Host:
	* `docker-machine stop docker-local`
	* `docker-machine start docker-local`
	* `docker-machine restart docker-local`
	* `docker-machine rm docker-local`

* And several to find out more details on your Docker Host:
	* `docker-machine aspect docker-local`
	* `docker-machine config docker-local`
	* `docker-machine status docker-local`
	* `docker-machine url docker-local`

### Launching Docker Hosts In the Cloud

Not covering this- see page 133

### More Docker Networking

* You can find out what docker hosts are running using
```
docker-machine ls
```


NOTE: There are many examples from this point on setting up Docker on other machines, please read the book for it, as I don’t want to cover it for now.


- - - -
## Docker Compose
* Docker Compose allows you run multiple containers in one go by grouping the required information in YAML Files

### Our Docker Compose Application

* Docker compose uses YAML files
* The YAML files are essentially docker-machines.
An example docker compose YAML file:

```
version: "3"
   services:
     redis:
      image: redis:alpine
      volumes:
         - redis_data:/data
      restart: always
     mobycounter:
      depends_on:
         - redis
      image: russmckendrick/moby-counter
      ports:
         - "8080:80"
      restart: always
   volumes:
     redis_data:
```

* To launch the application, go to the directory the yaml file is and use `docker-compose up`
* To exit the container, use ctrl+c in the terminal

### Docker Compose YAML File

* The example YAML file above is split in 3 sections (These a nested sections, rather than procedural sections, think of a section for each tab indentation!)
	* The version
	* The services section,which defines containers, this has the following format:
```
	services:
   --> container name:
   ----> container options
   --> container name:
   ----> container options
```
		* In our example, we have two containers defined, redis and mobycounter
	* The services section takes  flags for the `docker container run` command, here are a few flags you can use:
		* `image`: Defines what image to download and run
		* `volume`: equivalent to `—volume` flag
		* `depends_on`: which is used to build some logic into the order your containers are launched, such as container B being ran before container A
		* `ports`: which accepts a list of ports
		* `restart`
	* The final section of the compose file is where you define your volumes

### Docker Compose Commands

* `docker-compose up -d` : this turns the container back on in detached mode (remove -d if you want it up normally)
* `docker-compose ps` : shows the status of the containers
* `docker-compose config` : this validates your docker compose files when ran in the same directory. If you don’t want to see the output and just want to check for errors, pass the `-q` flag (AKA —quiet)
* To prepare your to launch your compose file, you need to:
	* `docker-compose pull` to pull the relevant images
	* `docker-compose build` to build the instructions it finds in your file.
	* `docker-compose create`: This builds the container, but does not launch it. The container will be in an exited state
	* These are both useful when you are first defining your Docker Compose-powered application, and want to test without launching your application.
* The following manages the docker-compose container once its built:
	* `docker-compose start`
	* 	 `docker-compose stop`
	* 	 `docker-compose restart`
	* 	 `docker-compose pause`
	* 	 `docker-compose unpause`
* You can also target a single service and pause/unpause it:
	* `docker-compose pause <serviceName>`
	* `docker-compose unpause <serviceName>`
* There are 3 commands that give feedback on what is happening within our running containers and Docker Compose:
	* `docker-compose top`  or `docker-compose top <servicename>`
	* `docker-compose logs` which streams log from each of the running containers to your screen
	* `docker-compose events` which streams events to your screen
* You can use `exec` and `run` like before:
	* `docker-compose exec worker <action> <serviceName>`
	* `docker-compose run <....>`
* The `up` command takes a service and scale it based to the number. As an example, adding more worker containers:
	 `docker-compose up -d --scale worker=3`
* The `kill` command immediately stops running containers
	 `docker-compose kill`
* The `rm` command removes any containers with a exited state:
	 `docker-compose rm`
* The `down` command is the opposite of the `up` command
	 `docker-compose down`
* If you want to remove everything:
`docker-compose down —rim all —volumes`

----

## Docker Swarm

* Docker swarms allow you create and manage Docker clusters.
* Swarms also give you the option to distribute containers across multiple hosts and scale containers.

### Docker Swarm Roles

* Two main roles in the docker swarm cluster:
	* Swarm Manager
	* Swarm worker

### Swarm Manager

* Is the host(s) that is the central management point for all swarm hosts
* Swarm managers issue commands to control the work nodes, with some of these being:
	* Switching between nodes
	* Joining nodes
	* Removing nodes
	* Manipulating nodes
* For production, its recommended that you run a minimum of 5 swarm managers. 
* Swarm managers use the Raft Consensus Algorithm, which maintains a consistent state across all of the manager nodes.

### Swarm Worker

* Swarm workers main job is to run Docker containers. 
* The manager determines what container a swarm worker should run.

![](Mastering%20Docker%20Second%20Edition/Screenshot%202017-11-12%2016.33.35.png)

### Creating a Cluster 

* This starts by creating a swarm manager.
* As we’re doing this on our local machine, we’re using virtual box and docker-machine
```
docker-machine create \
       -d virtualbox \
       swarm-manager
```

* The swarm manager node is now up, you can check this by doing `docker-machine ls`
* You then need to point the Docker Machine at the swarm manager by `docker-machine env swarm-manager`, which will give you instructions on what to do
* To create the worker, do:
```
docker-machine create \
       -d virtualbox \
       swarm-worker<numberORName>
```

* Then need to bootstrap the manager. You need to pass the results of a few Docker Machine commands to the host:

```
$ docker $(docker-machine config swarm-manager) swarm init \
       --advertise-addr $(docker-machine ip swarm-manager):2377 \
       --listen-addr $(docker-machine ip swarm-manager):2377
```


### Joining Workers

* To add the workers to the cluster:
```
docker $(docker-machine config swarm-worker01) swarm join \
       $(docker-machine ip swarm-manager):2377 \
       --token
   SWMTKN-1-3fxwovyzh24120myqbzolpen303uzk562y26q4z1wgxto5avm3-4aiagep3e2a1nwy
   af4yjp7ic5
```


### Listing Nodes

* To check the swarm, you can use `docker-machine ls`
* You also use `docker node ls` which will connect to the swarm master and query all nodes in your cluster

### Managing a Cluster

* `docker info` will give you lots of information about the Swarm manager host.
* That however will produce a load of shit thats hard to read, instead, try this:` docker node inspect swarm-manager --pretty`
	* You can replace swarm-manager will any node in the swarm to get information about it

### Promoting Worker Nodes

* This is done by:
`docker node promote <nodeName>`

### Demoting a manager node

* This is done by:
`docker node demote <nodeToDemote>`

### Draining a Node

* If you want to temporarily remove a node from the cluster to perform maintence, you have to put it in a drained state first. 
* This is done by:
`docker node update —availability drain <nodeToDrain>`
* Once maintenance is done, to turn it back to active:
`docker node update —availability active <nodeName>`

### Docker Swarm Services and Stacks

* Docker service and stack commands allow us to execute tasks that in turn launch, scale, and manage containers within the swarm
* The have the format of `docker service <command>` and `docker stack <command>`

### Services

* Services command is a way of launching containers that take advantage of the swarm cluster.

Example of a service called cluster, that containers a single container on port 80 mapped to the host machine


```
docker service create --name cluster --constraint "node.role == worker" -
   p:80:80/tcp russmckendrick/cluster
```

* You can then find what nodes are up from starting the service `docker node ls` or `docker-machine ls`
* To inspect a specific service: `docker service inspect <serveName> --pretty`
* To find out what containers are running on a host, use `docker node ps`

### Stacks

* Stacks are used to create complex, highly available multi-container applications.
* These are done through docker  compose files, such as:

![](Mastering%20Docker%20Second%20Edition/Screenshot%202017-11-25%2010.38.56.png)

* Compose files can contain multiple services.

### Deleting a Swarm Cluster

* This is done by `docker-machine rm swarm-manager swarm-worker01 swarm-worker02`


### Load Balancing, Overlays and Scheduling

* Docker has Ingress Load balancing built in, making it easy to distribute traffic to our public facing containers.
* You can expose applications within your swarm cluster to services, knowing that your request will be router to the correct containers no matter which host happens to currently be hosting it.

![](Mastering%20Docker%20Second%20Edition/Screenshot%202017-11-25%2010.45.37.png)

* Docker also offers a single scheduling strategy in the swarm called spread.
* The strategy schedules tasks to be run against the least loaded node that meets any of the constraints you defined when launching the service or stack.


## Extras

Im not going to cover these, but its interesting to look into

* Portainer
* Rancher
* Docker cloud
* Docker secruity
* Docker workflows

- - - -
