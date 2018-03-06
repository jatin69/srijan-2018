/*
Writer - Jatin Rohilla - MCA 1st year
Editor - Jatin
*/

## The Era of Containerization

Somewhere along your journey of computer science, you must have come across virtual machines and probably used one for running a Linux machine inside windows. The golden days of virtual box and VMware when running a virtual machine smoothly needed considerable hardware resources, and once you switch to the Guest OS, you could barely do anything on the Host OS. Multiple machines running together was a far stretched dream.

In the early days, virtual machines ( VM ) served the purpose of stable development environment over a team. A virtual machine with all the required software was made and passed on to each team member. Download the half-gigabyte operating system image that you want and install it. Then download and configure the stack you’ll be working with: let’s say Apache, MySQL, PHP. Then install some libraries, CuRL and ImageMagick maybe, and finally configure the ability to easily copy files from your machine to the new virtual one, something like Samba, or install an FTP server. Once this is all done, copy the code over, import the database, configure Apache’s virtual host, restart and cross your fingers. Pretty easy, right?
This setting up was a overhead. Even for a standard web development environment, the devs had to set it up from scratch. We needed something better.  

Soon enough, just one virtual machine was not enough. Individuals simultaneously worked on multiple projects , each of which needed separate development environments. New stacks coming up so aften, it was head to keep track. Setting up each of these from scrtach just to try out some cool new features. Easy, right?

Enter vagrant.
Vagrant brought the concept of boxes, which were VM images with standard dev environments pre-installed. Setting up the new tech stack was now a command away. Just find the right box, and start working. 

Vagrant leverages a declarative configuration file which describes all your software requirements. Instead of passing around VM's between team members, this config file could be version controlled, everyone could just pull and get ready to work. This made updates easier. Each team member could just update the config file and the next time they fired up vagrant, the VM already had the updated software. Starting a VM was as easy as typing `vagrant up`.

Vagrant, for long, gave us consistent environments to develop, test and deploy our app. But VM's were inherently slow, firing up the smallest of them would take a few minutes. Assume you have Python 3.6 installed but you want to test some code from Python 2.7. What would you do?
You could fire up and entire OS with Python 2.7 in it and test the code? Not bad, right? Hogging all your Host OS resources because you wanted Python 2.7.

We wanted something lighter, which would just do just what we wanted, and nothing more. 

Enter Docker.

Docker Inc is the company which popularised the concept of containers. Think of a container to be same as a container from a cargo ship. we don't know what's inside of each box, and from outside they all look same. what's inside them is limited to them. 

A virtual machine packs together a guest OS, its kernel, file system, device drives, then our tools, runtimes, and more. This makes them heavy. 
Docker used the fact that we don't really want an OS. All we want is a dev environment. So it leverages this fact and makes use of the Host OS kernel, instead of packing the guest OS kernel. This results in a smaller size and much faster deployment of containers.

## How are dockers so light?

Docker utilises AuFS.
AuFS is a layered file system, so you can have a read only part and a write part which are merged together. One could have the common parts of the operating system as read only (and shared amongst all of your containers) and then give each container its own mount for writing.

So, let's say you have a 1 GB container image; if you wanted to use a full VM, you would need to have 1 GB times x number of VMs you want. With Docker and AuFS you can share the bulk of the 1 GB between all the containers and if you have 1000 containers you still might only have a little over 1 GB of space for the containers OS.

Like vagrant, Docker also utilises the concept of centrally hosted images. Docker Hub is like a playstore for dev environments. You find `images` which fit your need, pull them, and then spin out containers from them.
Containers are like runtimes of the images. 
Dockerfile does the job even easier. It lets us specify which tools to install in the docker image. This adds a layer over the base image. What dockerfile does is keep track of all these layers.
So you want to build an image with python and anaconda. Just write down a dockerfile, specifying the base image to use, say ubuntu 17, and then specifying the additional commands to run to install anaconda. That's it.
Run the build command, and you get an image, just as you needed.
Then spin up a container from this image, and you are good to go to work.

Dockerfile has many other features, one of them is `port binding`. We can choose to map any port from the host os, to any port of the container. Assuming a web server running inside a container serving on port 80.
From outside the container, We cannot directly access it, so what we do is map any of our host port, say 5000, to container's port 80.

Dockerfile also allow us to specify volumes for data-persistance.
Remember that Containers are like runtime instances of images. so anything you do in the container gets lost as soon as you take them down. But that's not what we wanted, right? For this, Docker given us Volumes, which are just shared folders between host OS and container. This gives us data persistence over container runs. Any changes made from within the container are saved to this volume.

### one process per container

With docker, a rather new approach came into the picture, `one process per container`. Each container with a specific process within. so while building our custom app, we could just pick the images we want from docker hub. 
Each image serving only one need, may it be database, or server, and so on.

This `one process per container` approach gives us horizontal scalability. Too many server requests? Need one more apache server? Just spin up one more container from the same image. 
It keeps the containers light, and in a state of failure, another one with same specs could be brought up within seconds.

But how do these containers communicate with each other. One service running within each container, unaware of the world outside the container.
Docker compose does our job. Docker compose allows us to define a `docker-compose.yml` file which basically lists which container provides what service. All the containers mentioned in this file can communicate via specified ports, and some ports can be exposed to host OS to serve.

This unveils the real power of Docker. Hundreds of containers, serving from same image, but with different mount points for writing.

Now, there is an inherent problem with containers, just like there is with virtual machines. That is the need to keep track of them.

Enter Container Orchestration.

If your current software infrastructure looks something like this — maybe Nginx/Apache + PHP/Python/Ruby/Node.js app running on a few containers that talk to a replicated DB — then you might not require container orchestration, you can probably manage everything yourself.

What if your application keeps growing? Let’s say you keep adding more and more functionality until it becomes a massive monolith that is almost impossible to maintain and eats way too much CPU and RAM. 

What we do is split the massive monolith into smaller chunks, each responsible for one specific task, maintained by a team, aka. microservices. 
You might want to run multiple instances of each microservice spanning multiple servers to make it highly available in a production environment.

You now have to think about challenges like Load Balancing, configuration/storage management, Health checks, Auto-[scaling/restart/healing] of containers and nodes. 

This is where container orchestration platforms become extremely useful and powerful, because they offer a solution for most of those challenges.
Container Orchestration refers to the automated arrangement, coordination, and management of software containers.

We have several choices for this. The main players are Kubernetes, AWS ECS and Docker Swarm.  Kubernetes has the largest community and is the most popular by a big margin. Kubernetes is based on Google's experience of running workloads at huge scale in production over the past 15 years.

This makes the ideology much more powerful and practical for real-life applications. Self Healing of failed nodes, load balancing, scaling, updates, rollbacks, you name it. 

This will be all for this article.

# Food for thought

### Welcome to the Era of Immutable Infrastructure 

With the recent “container revolution,” a seemingly new idea became popular: immutable infrastructure. In fact, it wasn’t particularly new, nor did it specifically require containers. However, it was through containers that it became more practical, understandable, and got the attention of many in the industry.

So, what is immutable infrastructure? 
The practice of making infrastructure changes only in production by replacing components instead of modifying them. More specifically, it means once we deploy a component, we don’t modify (mutate) it. 

You don’t push out new configurations, you build new images with the new configuration baked in and replace the existing nodes.
