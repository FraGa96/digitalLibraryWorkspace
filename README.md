# 📚Digital Library - Infrastructure

Local infrastructure for managing, searching, and storing a digital library.

## 🚀 Tech Stack
* **Database:** PostgreSQL 17.4
* **Search Engine:** OpenSearch (Distributed search & analytics)
* **Object Storage:** MinIO (S3-Compatible)
* **Admin UIs:** pgAdmin 4 & OpenSearch Dashboards

---

## 🛠️ Prerequisites
1. **Docker** and **Docker Compose** installed.
2. **Node.js** installed (to run the convenience scripts via npm).
3. Create `.env.dev` and `.env.prod` files based on the provided templates.

---

## ⌨️ Available Commands

From the project root, you can use the following `npm` shortcuts to manage your environment:

| Command | Description |
| :--- | :--- |
| `npm run docker:dev` | Starts the full stack with **development profiles** (includes pgAdmin & Dashboards). |
| `npm run docker:prod` | Starts only the core services (DB, MinIO, Search) with **security enabled**. |
| `npm run docker:down` | Stops and removes containers (data in volumes is preserved). |
| `npm run docker:logs` | Streams real-time logs from all running services. |

---

## 🌐 Ports & Access (Dev Mode)

| Service | URL / Host | Credentials |
| :--- | :--- | :--- |
| **PostgreSQL** | `localhost:5432` | See `.env.dev` |
| **pgAdmin** | [http://localhost:8080](http://localhost:8080) | `admin@admin.com` |
| **MinIO Console** | [http://localhost:9001](http://localhost:9001) | `minio_admin` |
| **MinIO API (S3)** | `localhost:9000` | Access/Secret Keys in `.env` |
| **Search UI** | [http://localhost:5601](http://localhost:5601) | No security (Dev mode) |

---

## ⚠️ Architecture Notes
* **Persistence:** Data is stored in Docker named volumes (`postgres_data`, `minio_data`, etc.). It will **not** be deleted when running `docker:down`.
* **Isolation:** The `COMPOSE_PROJECT_NAME` variable in your `.env` ensures that development databases do not interfere with production-like environments on the same machine.
