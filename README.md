# Maestro Setup Guide

This repository contains the Docker Compose configuration and environment setup required to run **Maestro** along with its UI, Backend, Database, PhpMyAdmin, and the Knative serverless controller.

## Prerequisites

Before starting, ensure you have:

- Docker (20.x or newer)
- Docker Compose (v2 recommended)
- Linux-based host

## Project Structure

```
.
├── figures/
├── docker-compose.yml
├── .env.example
├── init-volume.sh
└── README.md
```

## Docker Compose Configuration

The system consists of the following services:

- **UI Frontend**
- **UI Backend**
- **MySQL Database**
- **PhpMyAdmin**
- **Knative Serverless Controller**

> ⚠️ Most services use `network_mode: "host"`. Make sure ports do not conflict with other services on the host.

### Services Overview

| Service                       | Description                    |
| ----------------------------- | ------------------------------ |
| ui-frontend                   | Maestro UI frontend            |
| ui-backend                    | Maestro backend REST API       |
| database                      | MySQL database                 |
| phpmyadmin                    | Database management UI         |
| knative-serverless-controller | API for serverless deployments |

---

## Environment Variables

Based on on `.env.example`, create a `.env` file in the project root.

## Volume Initialization

Before starting the services, initialize the required directories on the host with `init-volume.sh`

```
chmod +x init-volume.sh
./init-volume.sh
```

## Starting Maestro

From the project root, run:

```
docker compose up -d
```

To check running containers:

```
docker compose ps
```

Accessing Maestro UI:

```
http://<SERVER_IP>:3000
```

## Walkthrough

1. Login with user: admin pass: !1q2w3e!

2. Create a _Component_.

<p align="start">
  <img src="figures/components.png" alt="Component" width="600">
</p>

3. For serverless _Component_, you can edit the serverless properties tab.

<p align="start">
  <img src="figures/components_serverless.png" alt="Component" width="600">
</p>

4. Create an _Application_.

<p align="start">
  <img src="figures/application.png" alt="Component" width="600">
</p>

5. Create a _Resource_.

<p align="start">
  <img src="figures/resources.png" alt="Component" width="600">
</p>

6. Create an _Application Instance_ to deploy.

<p align="start">
  <img src="figures/application_instance.png" alt="Component" width="600">
</p>

7. Monitor deployed _Application Instance_.

<p align="start">
  <img src="figures/monitoring_deployed_application.png" alt="Component" width="600">
</p>

## todos

- prepare public docker images
