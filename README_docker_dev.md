# Dev stack (NGINX + React + Flask + MySQL)

This spins up four containers on one Docker network:
- `nginx` (public entry, port 80)
- `frontend` (Vite dev server with HMR)
- `backend` (Flask dev server with auto-reload)
- `db` (MySQL 8, with schema seeded from `mysql-db/`)

## 1) One-time setup

1. Create env files at the repo root:
   - `.env.db` — copy from `.env.db.example` and set passwords.
   - `.env.backend` — copy from `.env.backend.example`.

2. **Important:** Make the frontend call the API at **`/api`** (same-origin via NGINX).  
   Update your frontend service code so its base is:
   ```ts
   const API_URL = '/api/';
