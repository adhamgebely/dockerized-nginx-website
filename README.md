# 🐳 Dockerized Nginx Website

<p align="center">
  <img src="https://img.shields.io/badge/Docker-Containerized-2496ED?logo=docker&logoColor=white" alt="Docker">
  <img src="https://img.shields.io/badge/Nginx-Web%20Server-009639?logo=nginx&logoColor=white" alt="Nginx">
</p>

A simple DevOps project that demonstrates how to serve a static website using **Nginx inside a Docker container**, expose it through a host port, and publish the Docker image to **Docker Hub**.

---

## 📌 Architecture

<p align="center">
  <img src="screenshots/Architecture.png" width="850" alt="Project Architecture">
</p>

```text
Website Files → Docker Image → Nginx Container → Browser → Docker Hub
```

---

## 🛠 Technologies

- Docker
- Nginx
- Git & GitHub
- Docker Hub
- HTML / CSS / JavaScript

---

## ✅ Prerequisites

Make sure **Git** and **Docker** are installed:

```bash
git --version
docker --version
```

---

## 📥 Clone the Repository

```bash
git clone https://github.com/adhamgebely/dockerized-nginx-website.git
cd dockerized-nginx-website
```

---

## 🐳 Dockerfile

The project uses the official Nginx image:

```dockerfile
FROM nginx

COPY ./Course-Docker/sample-website /usr/share/nginx/html/

EXPOSE 80
```

<p align="center">
  <img src="screenshots/Dockerfile.png" width="850" alt="Dockerfile">
</p>

The Dockerfile:

- Uses the official **Nginx** image.
- Copies the static website files into the Nginx web directory.
- Exposes port `80`.

> [!IMPORTANT]
> The current Dockerfile expects the website files to exist at:
>
> ```text
> Course-Docker/sample-website
> ```
>
> Make sure this directory exists inside the Docker build context before building the image.

The expected build context should look like:

```text
dockerized-nginx-website/
├── Course-Docker/
│   └── sample-website/
│       ├── index.html
│       ├── css/
│       ├── js/
│       └── ...
├── screenshots/
├── Dockerfile
└── README.md
```

---

## 🏗 Build the Docker Image

Build the image:

```bash
docker build -t website .
```

Check that the image was created:

```bash
docker images
```

<p align="center">
  <img src="screenshots/build-image.png" width="850" alt="Docker Build">
</p>

---

## ▶️ Run the Container

Run the website container and map host port `3000` to Nginx port `80`:

```bash
docker run -d --rm -p 3000:80 --name web website
```

Check the running container:

```bash
docker ps
```

<p align="center">
  <img src="screenshots/docker-run.png" width="850" alt="Docker Run">
</p>

---

## 🌐 Access the Website

If Docker is running on your local machine, open:

```text
http://localhost:3000
```

If Docker is running on a remote server or cloud VM, open:

```text
http://YOUR_SERVER_PUBLIC_IP:3000
```

> Make sure port `3000` is allowed by the server firewall or cloud security group.

<p align="center">
  <img src="screenshots/browser.png" width="850" alt="Website Running">
</p>

---

## ☁️ Push to Docker Hub

Login to Docker Hub:

```bash
docker login
```

Tag the image:

```bash
docker tag website:latest YOUR_DOCKERHUB_USERNAME/dockerized-nginx-website:latest
```

Push it:

```bash
docker push YOUR_DOCKERHUB_USERNAME/dockerized-nginx-website:latest
```

> Replace `YOUR_DOCKERHUB_USERNAME` with your own Docker Hub username.

### Docker Hub

<p align="center">
  <img src="screenshots/dockerhub-before-push.png" width="850" alt="Docker Hub Before Push">
</p>

<p align="center">
  <img src="screenshots/dockerhub-after-push.png" width="850" alt="Docker Hub After Push">
</p>

---

## 📦 Pull and Run from Docker Hub

Anyone can pull the published image using:

```bash
docker pull YOUR_DOCKERHUB_USERNAME/dockerized-nginx-website:latest
```

Then run it:

```bash
docker run -d --rm -p 3000:80 --name web YOUR_DOCKERHUB_USERNAME/dockerized-nginx-website:latest
```

Open:

```text
http://localhost:3000
```

---

## 📋 Useful Commands

Check running containers:

```bash
docker ps
```

View container logs:

```bash
docker logs web
```

Stop the container:

```bash
docker stop web
```

Remove the container manually if needed:

```bash
docker rm -f web
```

---

## 📁 Repository Structure

```text
dockerized-nginx-website/
├── Dockerfile
├── README.md
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
