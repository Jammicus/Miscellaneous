# Mastering Docker, Second Edition 

## Docker Ecosystem

* Docker Engine comes in two versions:
	* Docker Enterprise Edition (Docker EE)
	* Docker Community Edition (CE)
	* Book will use CE
* The docker engine contains the following:
	* Docker Compose: Tool that allows you to define and share nulti container definitons
	* Docker Machine: Tool to launch Docker hosts on multiple platforms.
	* Docker hub: Repository for your docker images
	* Docker store: Storefront for offical docker images and plugins
	* Docker swarm: Multi-host-aware orchestration tool
	* Docker cloud: Dockers contain as a service (CaaS)
	* Docker for Amazon Web Services
	* Docker for Azure

## Building Container Images

### Introducting the Docker File

* Dockerfile is a plain text file that contains a set of user-defined commands, which when executed by the `docker image build` command assembles a container image

Example Docker file:

```
FROM alpine:latest   LABEL maintainer="Russ McKendrick <russ@mckendrick.io>"   LABEL description="This example Dockerfile installs NGINX."   RUN apk add --update nginx && \           rm -rf /var/cache/apk/* && \           mkdir -p /tmp/nginx/   COPY files/nginx.conf /etc/nginx/nginx.conf   COPY files/default.conf /etc/nginx/conf.d/default.conf
   
  ADD files/html.tar.gz /usr/share/nginx/   EXPOSE 80/tcp   ENTRYPOINT ["nginx"]   CMD ["-g", "daemon off;"]
```

* Alpine Linux is a non commerical linux distribution designed for security, efficiency and ease of use

### Reviewing the Dockerfile in Depth

#### From

* Tells docker which base you would like to use for your image (in our example we are using Alpine linux)


#### Label

* Used to add extra information to the image.
* Can be anything from version number to description
* Use the schema detailed at `http://label-s chema.org/. `
* To view a containers labels, use the `docker inspect` command: `docker image inspect <IMAGE_ID>`
* You can filter labels: `docker image inspect -f {{.Config.Labels}} <IMAGE_ID>
* Its good practice to define your labels when you create a container from the image rather than at build time.
* Labels should just be metadata data about the image.

#### Run

* Where we interact with our image to install software and run scripts, commands and other tasks.
* Run can run several commands

Example:

```
RUN apk add --update nginx && \
	rm -rf /var/cache/apk/* && \
	mkdir -p /tmp/nginx/
```

* `apk add --update nginx` installs the NGINX using apline linux package manager
* `&&` moves on to the next command if the previous command was successful
* `/` is used to split commands over multiple lines
* `rm -rf /var/cache/apk/*` removes any temp files
* `mkdir -p /tmp/nginx/` makes the folder so that NGINX starts correctly

#### Copy and Add

* Copy takes a directory or file and moves its to another directory

Example

```
COPY files/nginx.conf /etc/nginx/nginx.conf
```

* Add does the same thing, **BUT**, it will automatically uploads, uncompresses and puts the resulting folders and files at the path we tell it to!

```
#Download html.tar.gz then uncompress and move it to user/share/nginx
ADD files/html.tar.gz /usr/share/nginx/
```

#### Expose

* Lets docker know that when the image is executed, then the port and protocol defined will be exposed at runtime.
* This does not map the port to the host machine, rather it opens the port to allow access to the service on the container network.

Example

```
#Open port 80 Every time the image runs:
EXPOSE 80/tcp
```

#### ENTRYPOINT and CMD

* Its best to use ENTRYPOINT and CMD together
* Only use ENTRYPOINT if you want to have your container executable
* CMD is used to ass command lines arguments

Example

```
ENTRYPOINT ["nginx"]CMD ["-g", "daemon off;"]
```

Is Equvilent to:

```
 $ nginx -g daemon off;
```

### Other Dockerfile Commands

#### User

* Lets you specify the username to be used when a command is run
* Can be used on the RUN, CMD or ENTRYPOINT instruction in the Dockerfile.
* The user defined in USER must exist in your image file or there will be an error 

#### Workdir

*Sets the working directory for the RUN, CMD,ADD and ENTRYPOINT commands

#### Onbuild

* Lets you stash a set of commands that will be used when the image is used again as a base image for a container.
* Eg, if you need environments for developers to run their code. You can define the base code, and pass their code from a directory using ONBUILD.

Example

```
ONBUILD RUN apk update && apk upgrade && rm -rf /var/cache/apk/*
```
#### Env

* Sets the environment variables within the image both when it is build and when it is executed
* These can be overridden when you launch your image

### Dockerfiles - Best Practicies

* Should use `.dockerignore`
	* Essentially ignores the items you have specified in the file during the build process
* Have only one Dockerfile per folder. This will help you organize your containers
* Use version control for your Dockerfile
* Minimize the number of packages you need per image. You want to keep your images as small as possible
* Execute only one application process per container. When you need a new application, its best practice to use a new container to run that application in.
* Learn by example from `https://github.com/docker-library/official-images/`

## Building Docker Images

### The Docker Build Command


* The `docker build` command converts your file to an actual image

Syntax:

```
docker image build --helpUsage: docker image build [OPTIONS] PATH | URL | -Build an image from a Dockerfile
```

### Build an Image From a Dockerfile

* only really need to use `--tag` or `-t`. This is used to name the image


#### Building Custom Images using Dockerfiles

* You can build your base docker images from Dockerfiles.

Example of a docker file:

```
FROM alpine:latestLABEL maintainer="Russ McKendrick <russ@mckendrick.io>"LABEL description="This example Dockerfile installs NGINX."RUN apk add --update nginx && \        rm -rf /var/cache/apk/* && \        mkdir -p /tmp/nginx/
        
COPY files/nginx.conf /etc/nginx/nginx.confCOPY files/default.conf /etc/nginx/conf.d/default.confADD files/html.tar.gz /usr/share/nginx/EXPOSE 80/tcpENTRYPOINT ["nginx"]CMD ["-g", "daemon off;"]
```

* You can build the image from the docker file above in two ways:

* Specifying the -f switch when using `docker build`
	Eg: `  $ docker image build --file <path_to_Dockerfile> --tag <REPOSITORY>:<TAG>`
	* Repository is typically the username you signed upf ro on Docker hub.
	* Can use local to link to a local docker file

Example 

```
docker image build --file /path/to/your/dockerfile --tag   local:dockerfile-example 
```

* When the image is build, you can use `docker image ls` to find information about your image


#### Using an Existing Container

* Firstly you need to download the image you want as the base. This is done using ` docker image pull`

Example

` docker image pull alpine:latest`

* You then run the container in the foreground so you can add packages to it:

` docker container run -it --name apline-test alpine /bin/sh`

* To add the packages for our linux example, we use the `apk` command

```
   $ apk update   $ apk upgrade   $ apk add --update nginx   $ rm -rf /var/cache/apk/*   $ mkdir -p /tmp/nginx/   $ exit
```

* After installing the required packages, you need to stop and save the container. 
* To stop the container, use `exit`
* To save the container, use the following:

` docker container commit  <container_name> <REPOSITORY>:<TAG>`

Example

` docker container commit alpine-test local:broken-container`

* To save the container as an image file, run the following:

` docker image save -o <name_of_file.tar> <REPOSITORY>:<TAG>`

Example:

`  docker image save -o broken-container.tar local:broken-container`

#### Building from Scratch


* You have to create a dockerfile that uses scratch, and then add the TAR file.

Example

```
FROM scratchADD files/alpine-minirootfs-3.6.1-x86_64.tar /CMD ["/bin/sh"]

```

* When you have built your Dockerfile and operating system in a TAR file, you can build your image as you would for any other docker image:

` docker image build --tag local:fromscratch . `

* Once build, you can test the image by running the following:

` docker container run -it --name alpine-test local:fromscratch /bin/sh`

* The above example will launch a shall on the Alpine linux image

### Environmental Variables

#### Using Environmental variables in your docker file

* To use environmental variables in your Dockerfile, you use the `ENV` instruction.

Example

```
ENV <key> <value>
ENV username admin
```

* If you wish, you can use an equal sign between the key and value

```
ENV <key>=<value>
ENV username=admin
```

* If you are not using the equal sign, you can only set one environment variable per line.
* If you are using the equal sign, you can set many variables per line

```
ENV username=admin database=db1 tableprefix=pr2_
```

* To veiw what varaibles are set on a given image, you can use `inspect`

`docker image inspect <IMAGE_ID>` 


CONTINUE WITH EXAMPLES HERE


## Storing and Distributing Images

### Docker Hub