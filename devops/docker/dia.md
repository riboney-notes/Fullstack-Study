# Docker In Action Notes

## CH 1

**Architecture**
* Docker runs in the app layer in a computer system
  * Consists of:
    * Docker CLI
      * Interface for users to interact with Docker engine
    * Docker engine/ daemon
      * Background process that manages containers
    * Docker containers
      * Individual processes that run isolated environments for apps

**VM vs Docker**

* What is VM?
  * Software that provides virtual hardware on which programs and OS can be installed
* What are the cons of VM?
  * Long startup time
  * Significant resource overhead
* How does Docker compare with VMs?
  * Runs directly on host's linux kernal 
    * *So no overhead from running a separate OS and having long startup tme from running full boot sequences*
  * **NOTE** - on macOS and Windows, docker runs inside a linux VM


## CH2 Running apps in containers

**Objectives**
* Running interactive and daemon terminal programs in containers
* Basic Docker operations and commands
* Isolating programs from each other and injecting configuration
* Running multiple programs in a container
* Durable containers and the container life cycles
* Cleaning up containers on a system


**Concepts**
* Detached vs attached vs interactive containers
* PID Namespace
* Linking containers
* Difference between `docker rm -f` and `docker stop`
* CID vs Names

**Exercises**
* NodeJS/ Mongo app
  * Create nodejs app
    * Should accept values from CLI
    * Should save some data
    * Should output some data into CLI
  * Create mongodb
    * Create schemas for the entities
    * Create collections
  * Docker stuff
    * Setup and run mongodb in container
    * SSH into container and interact with mongodb
    * Detach container from terminal
    * Setup and run nodejs app in container
      * app should accept console input and save input to database
    * Link nodejs app container with mongodb container
    * Create script file to run both containers
    * Interact with app to have it save your inputs
    * SSH into mongodb container and view your inputs
* JShell
  * Install OpenJDK 11 in container
  * SSH into container and execute jshell commands
  * Get java programs from host computer to run in JShell

## CH3 Softare installation simplified

**OBJECTIVES**
* Identifying software
* Finding and installing software with Docker Hub
* Installing software from alternative sources
* Understanding filesystem isolation
* Working with images and layers

**CONCEPTS**
* Three main ways to install Docker images
  * From docker hub/ registry?
  * From image file?
* What is image?
  * What does it consist of?
  * Global unique identifier? Does it change?
* What is a named repository?
* How to save image to a file?
* How to remove image from Docker?
* How to load image from file into Docker?
* Using dockerfile to build image
* What are some cons to dockerfile
* What image properties factor into download and installation speeds?
* What are all these unnamed images that are listed when I used the `docker images` command?
* Why does `docker pull` command include messages about pulling dependent layers
* Where are the files that I wrote to my container's file systems
* What is a layer?
  - A: set of files and file metadata that is packaged and distrubted as an atomic unit
  - A: An image is a collction of image layers; they are called intermediate images
  - A: Mosy layers build upon a parent layer by applying filesystem changes to the parent
* How to view every image and layer

## CH4: Working with storage and volumes

**Objectives**
* Mount points
* Sharing data between host and container
* How to share data between containers
* Using temp, in-memory filesystems
* Managing data with volumes
* Advanced storage with volume plugins

**Links**
* [Union Filesystems](https://www.terriblecode.com/blog/how-docker-images-work-union-file-systems-for-dummies/)

**Concepts**
* What is the union file system?
  * Its like a virtual directory where its based on a real directory, but that directory is read-only; Changes are made to a `diff` layer which is not permanent
* What is linux file tree?
  * Where all storage (external, USB, etc) belong to a single directory tree, attached at certain locations called *mount points*
* What is a mount point?
  * Defines the location in the file tree, the access properties to the data at that mount point (ex: READ, WRITE, etc), and the source of the data mounted at that point (ex: USB, external HDD, etc)
  * Alows users/ software to use the file tree in a linux environment w/o knowing exactly how the tree is mapped into specific storage devices
* Bind Mounts
  * mount points used to remount parts of a filesysem tree (host) onto other locations (container)
  * Useful when you need bidirectional (read and write) data usage between host and container
* Volume overrides default content in the container
  * 
