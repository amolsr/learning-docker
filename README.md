# 🚀 Docker Learning Roadmap with Assignments (2025)

A structured roadmap with practical tasks for each milestone.  

---

## 1. Foundations

### Learn
- **Containers vs. Virtual Machines (VMs):**
  - **Bare Metal:** Directly runs on physical hardware. No abstraction. Fastest but least flexible.
  - **VMs:** Each VM runs a full OS with its own kernel on top of a hypervisor. Heavy but isolated.
  - **Containers:** Share the host OS kernel. Lightweight, portable, start in seconds.

- **Linux Basics:**
  - Users, groups, file permissions (`chmod`, `chown`).
  - Process management (`ps`, `top`, `kill`).
  - Package managers (`apt`, `yum`).

- **Container Internals:**
  - **Namespaces:** Provide isolation (PID, network, mount, IPC).
  - **cgroups (Control Groups):** Limit and account for resource usage (CPU, RAM).
  - **Union Filesystems:** Layered filesystems enabling image layers and copy-on-write.

### Assignments
- Write a comparison table of **Bare Metal vs VM vs Container**.
- Install a Linux VM (Ubuntu) and practice:
  ```bash
  ls, chmod, chown, ps, kill, apt-get install <package>
  ```
- Research and write a 1-page note on how **cgroups** and **namespaces** isolate containers.

---

## 2. Docker Installation & Basic Usage

### Learn
- Install **Docker Desktop** (Mac/Windows) or **Docker Engine** (Linux).
- Understand **container lifecycle**:
  - `create → start → stop → restart → remove`.

### Assignments
- Install Docker on your system.
- Run:
  ```bash
  docker run hello-world
  ```
- Start an interactive container:
  ```bash
  docker run -it alpine sh
  ```
  Inside container:
  - Create a file.
  - Exit, stop, restart the container.
  - Check if file persists.
- Explore container states using:
  ```bash
  docker ps
  docker ps -a
  docker logs <container>
  docker inspect <container>
  ```

---

## 3. Working with Images

### Learn
- Images are **blueprints** for containers.
- Docker Hub is the public registry.
- Dockerfile defines custom images.

### Assignments
- Run an **nginx** container and expose port `8080`:
  ```bash
  docker run -d -p 8080:80 nginx:latest
  ```
- Write a Dockerfile for a Python script:
  ```dockerfile
  FROM python:3.12
  COPY hello.py /
  CMD ["python", "/hello.py"]
  ```
- Build and run:
  ```bash
  docker build -t hello-docker .
  docker run hello-docker
  ```
- Optimize image size by using `python:3.12-alpine`.

---

## 4. Advanced Image & Registry Management

### Learn
- **Layer caching:** Each Dockerfile instruction creates a layer.
- **Multi-stage builds:** Useful for building small production images.
- **Docker Hub Push/Pull.**

### Assignments
- Create an image with multiple `RUN` instructions and check layers:
  ```bash
  docker history <image>
  ```
- Optimize Dockerfile by combining `RUN` commands with `&&`.
- Create a **multi-stage build** for Node.js or Go app.
- Push to Docker Hub:
  ```bash
  docker tag myapp:latest <username>/myapp:1.0
  docker push <username>/myapp:1.0
  ```

---

## 5. Docker Container Management (Basics)

### Learn
- **Run modes:**
  - `docker run` → starts a new container.
  - `docker exec` → runs a command in a running container.
  - `docker attach` → attaches to running container terminal.
- **Resource limits:**
  - `--memory` → limit RAM.
  - `--cpus` → limit CPU.
- **Restart policies:**
  - `--restart always` ensures containers auto-restart.

### Assignments
- Run a container in detached mode:
  ```bash
  docker run -d nginx
  docker logs <container>
  ```
- Enter a running container:
  ```bash
  docker exec -it <container> bash
  ```
- Limit container resources:
  ```bash
  docker run -d --memory=256m --cpus=1 nginx
  docker stats
  ```
- Test restart policies by stopping Docker service and starting again.

---

## 6. Docker Networking

### Learn
- **Default networks:**
  - `bridge`: Default, container-to-container with IP.
  - `host`: Shares host’s network namespace.
  - `none`: Isolated.
  - `overlay`: Multi-host networking.
- **User-defined networks:** Easier container DNS-based communication.

### Assignments
- Run 2 containers in default bridge network, test connectivity:
  ```bash
  docker run -dit --name alpine1 alpine sh
  docker run -dit --name alpine2 alpine sh
  docker exec -it alpine1 ping alpine2
  ```
- Create custom bridge network:
  ```bash
  docker network create mynet
  docker run -dit --name app1 --network mynet alpine sh
  docker run -dit --name app2 --network mynet alpine sh
  docker exec -it app1 ping app2
  ```
- Run a container in `host` mode and check ports.
- Inspect network:
  ```bash
  docker network inspect mynet
  ```

---

## 7. Docker Volumes & Storage

### Learn
- **Volumes:** Managed by Docker, best for databases.
- **Bind Mounts:** Link host directory to container.
- **tmpfs:** In-memory storage.

### Assignments
- Create a named volume:
  ```bash
  docker volume create mydata
  ```
- Run a Postgres container with a volume:
  ```bash
  docker run -d --name pg -e POSTGRES_PASSWORD=pass -v mydata:/var/lib/postgresql/data postgres
  ```
- Stop and remove container, restart with same volume → data persists.
- Create a bind mount:
  ```bash
  docker run -v $(pwd):/app -it alpine sh
  ```
- Inspect volumes:
  ```bash
  docker volume inspect mydata
  ```

---

✅ By completing these steps, you’ll move from **zero to practical Docker usage** — mastering images, containers, networks, and persistent storage.  


[Some Important Command](Docker_Quick_Commands.md)
