# Docker Compose Microservices Scaling

Scalable microservices setup using Flask backend containers, Docker Compose, and Nginx reverse proxy/load balancing.

## Features

- Horizontal backend scaling
- Nginx reverse proxy + load balancing
- Docker bridge networking
- Healthchecks and restart policies
- Internal service discovery using Docker DNS
- Stateless containerized backend architecture

## Run

```bash
docker compose up --build --scale backend=3
```

Open:

```text
http://localhost
```

Refresh multiple times to observe requests being distributed across backend containers.
