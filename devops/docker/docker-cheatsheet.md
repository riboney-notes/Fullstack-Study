**Cheatsheet**
<details>
  <summary>Create a container without running it/ Create a container in a stopped state</summary>
  
  `docker container create <container>`
</details>

<details>
  <summary>Create container and save container id into local env variable</summary>
  
  * `CID=$(docker container create <image>)`
  * `CID` can now be used in place of long ID value or name
</details>

<details>
  <summary>Save container id into file upon container creation</summary>
  
  * `docker container create --cidfile <filename> <container>`
  * NOTE: if the file already exists, then docker won't create a new container
  * Benefit of CID files? You can reuse them
</details>

<details>
  <summary>Inject env variables into container upon creation</summary>
  
  * `docker container create -e <ENV=your_env_value_here> <image>`
  * `docker container create --env-file <filename> <container>`
</details>

<details>
  <summary>Start a stopped container</summary>
  
  `docker container start <container>`
</details>

<details>
  <summary>Inject env variables into container and run container</summary>
  
  * `docker container run -e <ENV=your_env_value_here> <image>`
  * `docker container run --env-file <filename> <container>`
</details>

<details>
  <summary>Restart a container</summary>
  
  `docker container restart <container>`
</details>

<details>
  <summary>Run a detached container</summary>

  `docker container run -d <image>`
</details>

<details>
  <summary>Run a interactive container</summary>
  
  `docker container run -it <image>`
</details>

<details>
  <summary>Run container with restart policy</summary>
  
  * `docker container run --restart <restart policy> <container>`
  * By default, restart policy is "never"
</details>

---
<details>
  <summary>Stop a container</summary>
  
  `docker container stop <container>`
</details>

<details>
  <summary>Shut down an interactive container</summary>
  
  Just type `exit` in the terminal thats connected to the container
</details>

<details>
  <summary>Detach terminal from interactive container</summary>
  
*  Press: CTRL+PQ
*  *Note*: Only works if you used `--tty` option
</details>

<details>
  <summary>Reattach terminal to container/ Connect to container</summary>
  
  `docker exec -it <image> bash`
</details>

<details>
  <summary>Remove container from computer</summary>
  
  * `docker container rm <container>`
</details>

<details>
  <summary>Set container to remove itself upon being stopped</summary>
  
  * `docker container run --rm <image>`
</details>

---

<details>
  <summary>List all currently running containers on your system</summary>
  
  `docker ps`
</details>

<details>
  <summary>View a container's logs</summary>
  
  `docker logs <image>`
</details>

<details>
  <summary>View a container's logs continuously</summary>
  
  * `docker logs -f <image>`
  * The `-f`/`--follow` flag will display logs and then continue watching and updating the display with changes to the log as they occur
  * Press CTRL-C to exit
</details>

<details>
  <summary>Show all running processes in a container</summary>
  
  * `docker exec <container> ps`
  * `docker container top <container>`
</details>

<details>
  <summary>Rename container</summary>
  
  `docker container rename <current name> <new name>`
</details>

<details>
  <summary>Get container id of the last container created</summary>
  
  `docker container ls -lq`
</details>

<details>
  <summary>Show all created containers</summary>
  
  `docker container ls -a`
</details>

<details>
  <summary>Check if certain container is running</summary>
  
  * `docker container inspect -f "{{.State.Running}}" <container>` 
</details>

<details>
  <summary>Display changes made to container's files</summary>
  
  `docker container diff <container>`
</details>
