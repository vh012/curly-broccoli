# Curly Broccoli

A full-stack web application for managing and sharing a personal book library. Track your reading, rate and review books, follow other readers, and discover new titles.

## Features

- **Book Management** — Create, edit, and organize your personal book collection (with ISBN validation)
- **Reading Tracker** — Track reading progress with sessions, states (reading, paused, finished), and duration logging
- **Ratings & Reviews** — Rate and review books in your collection
- **Social** — Follow other users, browse their public collections, and see activity feeds
- **Search** — Full-text search for books and users powered by Elasticsearch

## Tech Stack

**Backend:** Bun, Elysia, PostgreSQL (Drizzle ORM), Elasticsearch, MinIO (S3-compatible file storage), JWT auth

**Frontend:** React 18, Vite, React Router v7, TanStack Query, Tailwind CSS

**Infrastructure:** Docker Compose, PostgreSQL 16, Elasticsearch 9, MinIO

## Project Structure

```
├── backend/          # Bun/Elysia REST API
│   ├── src/
│   │   ├── api/      # Routes, guards, hooks, plugins
│   │   ├── services/ # Business logic (per entity)
│   │   ├── entities/ # Domain models
│   │   └── infra/    # DB, search, file storage, events
│   └── deployment/   # Docker Compose for dev services
│
├── frontend/         # React + Vite SPA
│   ├── src/
│   │   ├── app/      # Router, layouts, providers
│   │   ├── features/ # Feature modules (auth, books, reading, follows, etc.)
│   │   └── shared/   # Shared components and utilities
│
└── .github/          # CI/CD workflows
```

## Getting Started

### Prerequisites

- [Bun](https://bun.sh/)
- [Docker](https://www.docker.com/) & Docker Compose
- [Node.js](https://nodejs.org/) (for frontend)

### Backend

```bash
cd backend
make dev       # build image & start all services in dev mode (with logs)
```

Other useful targets:

```bash
make run               # start services without rebuilding
make stop              # stop services and remove volumes
make watch             # start with Docker Compose watch (hot-reload)
make logs              # show last 100 lines of logs
make logs-follow       # follow logs in real time
make hurl              # run Hurl integration tests
make test-unit         # run unit tests inside the container
make build             # build Docker image only
make help              # list all targets and flags
```

Flags: `PROFILE=<dev|db|elastic|storage|all>`, `PULL=true`, `NO_CACHE=true`, `ENV_FILE=<file>`

### Frontend

```bash
cd frontend
make dev       # build image & start in dev mode (with watch)
```

Other useful targets:

```bash
make prod              # build and start in production mode
make build             # build Docker image only
```
