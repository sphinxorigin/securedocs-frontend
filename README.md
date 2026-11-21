# SecureDocs Frontend

This is the frontend for SecureDocs, my Web Technologies project at HTW Berlin. I'm using Vue 3, TypeScript and Vite.

The goal is a portal where users can upload PDFs and share them with other users. At the moment, the app displays sample documents loaded from the Spring Boot backend.

## Links

- [Live app](https://securedocs-dh61.onrender.com)
- [Backend repository](https://github.com/sphinxorigin/securedocs-backend)
- [Backend API](https://securedocs-api-dh61.onrender.com/documents)

## Current status — Milestone 3

- Loads documents from `GET /documents` using `fetch`.
- Displays them in a separate `DocumentList.vue` component using props, `v-for` and stable keys.
- Filters the list by filename or description.
- Shows a loading message and an error message with a retry button if the request fails.

Uploads, login, sharing and database storage are planned for later milestones. The current data comes from the backend's sample list.

## Run locally

You need Node.js 22.12+ or Node.js 24 LTS. From the repo root, run:

```sh
npm ci
npm run dev
```

Open the address shown in the terminal. The backend needs to run separately and defaults to `http://localhost:8081`. Its default CORS configuration allows the frontend at `http://localhost:5173`.

To use a different backend, create a `.env.local` file. There is also a `.env.example` file as a starting point.

```dotenv
VITE_BACKEND_URL=https://securedocs-api-dh61.onrender.com
```

Restart the dev server after changing this value. Use only the backend's base URL, without `/documents`.

## Production build

```sh
npm run build
```

This checks the TypeScript types and builds the app into `dist/`.

## Render deployment

The frontend runs as the static site `securedocs-dh61`. It uses this repo and the `main` branch.

| Setting | Value |
|---|---|
| Root directory | Leave empty — repo root |
| Build command | `npm ci && npm run build` |
| Publish directory | `dist` |
| `NODE_VERSION` | `24` |
| `VITE_BACKEND_URL` | `https://securedocs-api-dh61.onrender.com` |

Vite reads `VITE_BACKEND_URL` during the build, so changing it requires a new build. The site is connected through the public Git URL, so I use **Manual Deploy** in Render after pushing changes.

The free backend instance can go to sleep when inactive. The loading message stays visible while it starts up.

## Repository history

The frontend used to be in the `frontend/` folder of the main SecureDocs repo. I moved it into this separate repo and kept its commit history, including the Milestone 2 version. Both Render URLs stayed the same.
