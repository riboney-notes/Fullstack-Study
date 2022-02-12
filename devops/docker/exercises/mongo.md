# Docker Exercises!

This repository serves to give people a way to learn and practice docker

**NOTE:** *this is a work in progress. I am still learning Docker so the solutions/ steps may be wrong. If you find any issues or have any suggestions, please create a git issue and/or contact me on discord!*

## Getting Started

### Prerequisites

* Docker Engine
* Docker CLI
* Docker-compose
* git

## Exercise #1: Dockerize NodeJS/ Express API & MongoDB

**Task #1: Setup MongoDB in container**
<details>

  <summary>1. See what containers are currently running</summary>

  `docker container ls`
</details>

<details>

  <summary>1a. Stop all containers if they are running</summary>

  `docker container stop $(docker container ls -aq)`
</details>

<details>

  <summary>2. Create docker-compose.yml file for mongodb in project's root directory </summary>

  `touch docker-compose.yml`
</details>

<details>

  <summary>2a. In the `docker-compose.yml` file, define the mongodb service; be sure to include: volume for persisting data, ports to expose (use default for mongo), and restart policy </summary>

```yml
version: "3.8"
services:
  mongodb:
    image : mongo
    container_name: mongo
    volumes:
    - ./data:/data/db
    ports:
    - 27017:27017
    restart: always
```
</details>

<details>

  <summary>3. Run mongo with docker, in the background </summary>

  `docker-compose up -d`
</details>

<details>

  <summary>4. Verify mongo is running by viewing its logs</summary>

  `docker container logs mongo`
</details>

<details>

  <summary>5. SSH into container</summary>

  `docker container exec -it mongo bash`
</details>

<details>

  <summary>5a. Connect to mongo </summary>

  `mongo`
</details>


<details>

  <summary>5b. create a `food` database and use it </summary>

  `use food`
</details>

<details>

  <summary>5c. Create collection candy </summary>

  `db.createCollection("candy")`
</details>

<details>

  <summary>5d. Insert many `candy` documents </summary>

  ```js
  db.candy.insertMany([
      {name: "kit-kat", type: "chocolate"},
      {name: "starbursts", type: "fruit"},
      {name: "wrigleys", type: "gum"}
  ])
  ```
</details>

<details>

  <summary>5e. Exit mongo </summary>

  `exit`
</details>

<details>

  <summary>5f. Exit container </summary>

  `exit`
</details>

<details>

  <summary>6. Shut down and remove container </summary>

  `docker-compose down`
</details>

<details>

  <summary>7. Check if container is running </summary>

  `docker container ls`
</details>

<details>

  <summary>8. Start up container again </summary>

  `docker-compose up -d`
</details>

<details>

  <summary>9. Connect to container</summary>

  `docker container exec -it mongo bash`
</details>

<details>

  <summary>10. Connect to mongo and view the food.candy collection </summary>

  * `mongo`
  * `use food`
  * `db.candy.find().pretty()`
</details>

```docker
version: "3.8"
services:
  mongodb:
    image : mongo
    container_name: mongo
    volumes:
    - ./data:/data/db
    ports:
    - 27017:27017
    restart: always
```
