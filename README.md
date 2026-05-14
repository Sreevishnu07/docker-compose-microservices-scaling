# Docker Compose Microservices Scaling

A scalable microservices setup using **Flask**, **Docker Compose**, and **Nginx** as a reverse proxy and load balancer.

---

## Architecture

```
                    ┌─────────────────────────────────────┐
                    │          Docker Bridge Network      │
                    │                                     │
  Client ────────► Nginx (port 80)                        │
                    │   Load Balancer                     │
                    │         │                           │
                    │  ┌──────┴────────────┐              │
                    │  ▼        ▼          ▼              │
                    │ Flask    Flask      Flask           │
                    │ backend-1 backend-2 backend-3       │
                    │                                     │
                    └─────────────────────────────────────┘
```

Nginx distributes incoming requests across all running Flask containers using round-robin load balancing. Each backend is stateless, so any instance can handle any request.

---

## Features

- **Horizontal backend scaling** — spin up as many Flask instances as needed
- **Nginx reverse proxy + load balancing** — round-robin traffic distribution
- **Docker bridge networking** — containers communicate by service name
- **Healthchecks & restart policies** — automatic recovery on failure
- **Internal service discovery** — Docker DNS resolves backend replicas automatically
- **Stateless containerized backends** — no shared state between instances

---

## Run

```bash
docker compose up --build --scale backend=3

docker compose up --scale backend=5

docker compose up --build --scale backend=3 -d
```

Open **http://localhost** and refresh multiple times — each request is served by a different backend container, observable via the container hostname or instance ID in the response.

---

## Stop

```bash
docker compose down
```

---

## Tech Stack

| Component | Technology     |
|-----------|----------------|
| Backend   | Python / Flask |
| Gateway   | Nginx          |
| DevOps    | Docker Compose |

---

## License

[MIT](LICENSE)
