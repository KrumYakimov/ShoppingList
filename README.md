# React + Node.js + MongoDB Application Deployment via Docker and Docker Compose

## Description

This project is part of an exercise for the **Regular Exam – 12 April 2025** from the _Containers and Cloud_ course at **SoftUni** (February 2025).

The task is to containerize and run a full-stack web application composed of a React frontend, a Node.js backend, and a MongoDB database using **Docker** and **Docker Compose**.

The application consists of:

- A frontend built with **React**
- A backend API built with **Node.js**
- A database powered by **MongoDB**

---

## Deployment Goal

Use Docker and Docker Compose to:
- Build and run the three application components as separate containers.
- Push the frontend and backend Docker images to Docker Hub.
- Configure and run the system using a single `docker-compose.yml` file.

The following file renaming and structure conventions were followed:

- `Dockerfile-fe` – for the React frontend
- `Dockerfile-be` – for the Node.js backend
- `docker-compose.yml` – for service orchestration
- Folder: `krumyakimov-task-1` containing all deployment files

---

## Technologies Used

- React
- Node.js
- MongoDB
- Docker
- Docker Compose
- Docker Hub
- Localhost (development environment)

---

## How to Deploy

### 1. Clone the repository

```bash
git clone https://github.com/your-username/your-repo.git
cd krumyakimov-task-1
````

### 2. Run Docker Compose

```bash
docker compose up --build
```

This will:

* Build the frontend and backend services from the provided Dockerfiles
* Pull MongoDB image from Docker Hub
* Create and mount the required volumes
* Launch all services in a shared Docker network

---

## Volumes and Configuration

The following volumes were created via Docker Compose:

* `data` → mounted to `/data/db` in the MongoDB container
* `logs` → mounted to `/app/logs` in the backend container
* `node_modules` → mounted to `/app/node_modules` in the backend container
* `frontend/src` → bind-mounted to `backend/src` for shared source development

Services were exposed on:

* Frontend: `http://localhost:3000`
* Backend: `http://localhost:80`

**Note:** The MongoDB connection string in the backend was modified to connect to the `mongo` service within the Docker network.

---

## Docker Hub

The following Docker images were built and pushed:

* Frontend: `docker.io/<your-username>/react-app`
* Backend: `docker.io/<your-username>/node-api-app`

These are referenced in the `docker-compose.yml` file.

---

## Outputs

After running the deployment:

* All services are accessible and functional
* A screenshot of the application running is included as `screenshot.png`

---

## Security Notice

This project does not include any sensitive environment variables or secrets in version control. The MongoDB connection uses the default unsecured setup for development purposes only.
