Web (local) — DM Console
========================

Objetivo
--------
Frontend React + Backend Node + Postgres para buscar/editar todo el lore desde DB.

Requisitos
----------
- Node.js (recomendado 18+)
- Docker (para Postgres) o Postgres local

1) Base de datos (Postgres)
---------------------------
En la raíz del repo:
- `docker compose up -d`

2) Backend (Node)
-----------------
En `back/`:
- `cp .env.example .env`
- Si tu Postgres es: user `postgres`, pass `admin`, db `dndEcos`, el `DATABASE_URL` queda:
  - `postgresql://postgres:admin@localhost:5432/dndEcos`
- `npm install`
- `npm run db:migrate`
- Import inicial (cargar docs a DB):
  - Opción A (CLI): `npm run db:seed:campaign`
  - Opción B (Web): botón “Importar campaign/” en el Dashboard (requiere backend arriba)
- `npm run dev`

API: `http://localhost:3001`

3) Frontend (React)
-------------------
En `front/`:
- `npm install`
- `npm run dev`

Web: `http://localhost:5173`

Notas
-----
- La web edita la DB (fuente de verdad). El importador solo sirve para “cargar” el estado inicial desde archivos.
- Para reimportar: correr `npm run db:seed:campaign` en `back/` o usar el botón.
- Si tu DB fue creada sin comillas, Postgres suele convertir nombres a minúscula; si `dndEcos` falla, probá `dndecos`.
