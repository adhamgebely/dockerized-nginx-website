# 🐳 Dockerized Nginx Website

<p align="center">
  <img src="https://img.shields.io/badge/Docker-Containerized-2496ED?logo=docker&logoColor=white" alt="Docker">
  <img src="https://img.shields.io/badge/Nginx-Web%20Server-009639?logo=nginx&logoColor=white" alt="Nginx">
</p>

A simple DevOps project that demonstrates how to serve a static website using **Nginx inside a Docker container** and publish the Docker image to **Docker Hub**.

---

## 📌 Architecture

<p align="center">
  <img src="screenshots/Architecture.png" width="850" alt="Project Architecture">
</p>

```text id="jg9b3r"
Website Files → Docker Image → Nginx Container → Browser → Docker Hub
```

---

## 🛠 Technologies

* Docker
* Nginx
* Git & GitHub
* Docker Hub
* HTML / CSS / JavaScript

---

## ✅ Prerequisites

Make sure Git and Docker are installed:

```bash id="d004dy"
git --version
docker --version
```

---

## 📥 Clone the Repository

```bash id="kvf0z5"
git clone https://github.com/adhamgebely/nginx-website.git
```

```bash id="twabzs"
cd nginx-website
```

---

## 🐳 Dockerfile

```dockerfile id="v5ct6y"
FROM nginx

COPY ./Course-Docker/sample-website /usr/share/nginx/html/

EXPOSE 80
```

<p align="center">
  <img src="screenshots/Dockerfile.png" width="850" alt="Dockerfile">
</p>

The Dockerfile:

* Uses the official Nginx image.
* Copies the static website into the Nginx web directory.
* Exposes port `80`.

> Make sure `Course-Docker/sample-website` exists inside the Docker build context before building the image.

---

## 🏗 Build the Docker Image

```bash id="g5n57i"
docker build -t website .
```

Check the image:

```bash id="ogfhle"
docker images
```

<p align="center">
  <img src="screenshots/build-image.png" width="850" alt="Docker Build">
</p>

---

## ▶️ Run the Container

```bash id="pt0qjg"
docker run -d --rm -p 3000:80 --name web website
```

Check the running container:

```bash id="7dyi6k"
docker ps
```

<p align="center">
  <img src="screenshots/docker-run.png" width="850" alt="Docker Run">
</p>

---

## 🌐 Open the Website

For a local machine:

```text id="n36obt"
http://localhost:3000
```

For a remote server:

```text id="6gkj12"
http://YOUR_SERVER_PUBLIC_IP:3000
```

<p align="center">
  <img src="screenshots/browser.png" width="850" alt="Website Running">
</p>

---

## ☁️ Push to Docker Hub

Login:

```bash id="ppid1m"
docker login
```

Tag the image:

```bash id="59nu2o"
docker tag website:latest YOUR_DOCKERHUB_USERNAME/nginx-website:latest
```

Push the image:

```bash id="1v617y"
docker push YOUR_DOCKERHUB_USERNAME/nginx-website:latest
```

> Replace `YOUR_DOCKERHUB_USERNAME` with your Docker Hub username.

### Docker Hub

<p align="center">
  <img src="screenshots/dockerhub-before-push.png" width="850" alt="Docker Hub Before Push">
</p>

<p align="center">
  <img src="screenshots/dockerhub-after-push.png" width="850" alt="Docker Hub After Push">
</p>

---

## 📦 Pull and Run from Docker Hub

Pull the image:

```bash id="sc33an"
docker pull YOUR_DOCKERHUB_USERNAME/nginx-website:latest
```

Run it:

```bash id="ijtu4b"
docker run -d --rm -p 3000:80 --name web YOUR_DOCKERHUB_USERNAME/nginx-website:latest
```

Then open:

```text id="soic6f"
http://localhost:3000
```

---

## 📋 Useful Commands

Check running containers:

```bash id="18bymz"
docker ps
```

View logs:

```bash id="3o96mm"
docker logs web
```

Stop the container:

```bash id="mkyrhw"
docker stop web
```

Remove a container manually:

```bash id="94zve9"
docker rm -f web
```

---

## 📁 Project Structure

```text id="cww3p6"
dockerized-nginx-website/
│
├── Dockerfile
├── README.md
│
└── screenshots/
    ├── Architecture.png
    ├── Dockerfile.png
    ├── browser.png
    ├── build-image.png
    ├── docker-run.png
    ├── dockerhub-after-push.png
    ├── dockerhub-before-push.png
    └── git clone.png
```

---

## 👨‍💻 Author

**Adham Gebely**

GitHub: [@adhamgebely](https://github.com/adhamgebely)

---

## ⭐ Support

If you found this project useful, consider giving the repository a ⭐.
