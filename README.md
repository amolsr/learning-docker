# Docker Learning Roadmap with Assignments (2025)

A structured roadmap with practical tasks for each milestone.

---

## 1. Foundations

**Learn:**
- What are containers vs. VMs?
- Linux basics: users, permissions, processes, package managers.
- Core container tech: namespaces, cgroups, union filesystems.

**Assignments:**
- [ ] Write a short comparison table of Bare Metal vs VM vs Container.
- [ ] Install a Linux VM (Ubuntu) and practice:
  - `ls`, `chmod`, `chown`, `ps`, `kill`, `apt`/`yum` commands.
- [ ] Research and write a 1-page note on how `cgroups` and `namespaces` isolate containers.

---

## 2. Docker Installation & Basic Usage

**Learn:**
- Install Docker Desktop or Docker Engine.
- Run your first container.
- Understand container lifecycle (start, stop, restart, remove).

**Assignments:**
- [ ] Install Docker on your machine.
- [ ] Run `docker run hello-world`.
- [ ] Run `docker run -it alpine sh` and:
  - Create a file inside the container.
  - Stop and restart the container.
  - Check if the file persists.
- [ ] Use `docker ps`, `docker ps -a`, `docker logs`, and `docker inspect` to explore container states.

---

## 3. Working with Images

**Learn:**
- Pull and explore images.
- Use Docker Hub.
- Write Dockerfiles.

**Assignments:**
- [ ] Run a container from `nginx:latest` and expose port 8080 → visit it in browser.
- [ ] Write a **Dockerfile** for a Python script that prints `"Hello Docker"`.
- [ ] Build and run the image with `docker build` and `docker run`.
- [ ] Try to reduce image size by switching base image (e.g., `python:3.12` → `python:3.12-alpine`).

---

## 4. Advanced Image & Registry Management

**Learn:**
- Layer caching, multi-stage builds.
- Pushing to Docker Hub.

**Assignments:**
- [ ] Build an image with multiple RUN instructions and use `docker history` to see layers.
- [ ] Optimize Dockerfile by combining RUN instructions.
- [ ] Create a multi-stage Dockerfile for a Node.js or Go app.
- [ ] Create a Docker Hub account, tag your image, and push it:
  ```sh
  docker tag myapp:latest <username>/myapp:1.0
  docker push <username>/myapp:1.0

[Some Important Command](Docker_Quick_Commands.md)
