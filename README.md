# api-gateway

A single-node **Kong API Gateway** demo showcasing routing, service management, and administration through Konga, fronting multiple backend services (Nginx, Apache, HTTPBin, and two custom Flask apps).

## What this project demonstrates

- Setting up **Kong** (API Gateway) with a Postgres-backed database
- Managing Kong via the **Konga** admin GUI
- Routing/proxying requests to multiple backend services:
  - **Nginx** web server
  - **Apache** web server
  - **HTTPBin** (request/response testing service)
  - **app-service-a** and **app-service-b** (custom Flask applications)

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Getting started

1. Clone the repository:
   ```bash
   git clone https://github.com/adisakshya/api-gateway.git
   cd api-gateway/single-node-kong-gateway
   ```

2. Start all services:
   ```bash
   docker compose up
   ```

3. Wait for the `kong-migrations` service to complete before Kong becomes available.

## Exposed ports

| Service         | Port(s)          | Description                          |
|-----------------|------------------|---------------------------------------|
| Kong Proxy      | `8000`, `8443`   | Main gateway entrypoint (HTTP/HTTPS)  |
| Kong Admin API  | `8001`, `8444`   | Kong administration API (HTTP/SSL)    |
| Konga           | `1337`           | Web GUI for managing Kong             |
| Postgres        | `5432`           | Kong's backing database               |

## Configuring Kong (Services & Routes)

Once the stack is running, use the Postman collection to configure Kong Services and Routes for each backend:

```
single-node-kong-gateway/postman-collection/api-gateway.postman_collection
```

Import this collection into [Postman](https://www.postman.com/) to see example requests for registering each service (Nginx, Apache, HTTPBin, app-service-a, app-service-b) with Kong, and creating routes to expose them through the gateway.

Alternatively, you can access the Konga GUI at `http://localhost:1337` to configure services and routes visually.

## License

See [LICENSE](./LICENSE).
