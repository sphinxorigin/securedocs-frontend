# SecureDocs Frontend

Vue-3-Anwendung mit TypeScript und Vite für das SecureDocs-Projekt im Modul Webtechnologien.

## Links

- Live-Anwendung: https://securedocs-dh61.onrender.com
- Backend-Repository: https://github.com/sphinxorigin/securedocs-backend
- Backend-API: https://securedocs-api-dh61.onrender.com/documents

## Stand: Milestone 3

- Dokumentenliste wird mit `fetch` über `GET /documents` vom Spring-Boot-Backend geladen.
- Eigene Unterkomponente `DocumentList.vue` mit Props, `v-for`, stabilen Keys und Suchfilter.
- Ladehinweis, Fehleranzeige und erneuter Ladeversuch.
- Upload, Anmeldung, Freigaben und Datenbank folgen später. Die Daten stammen aktuell aus dem Backend-Beispieldatensatz.

## Lokal starten

Voraussetzung: Node.js 22.12+ oder Node.js 24 LTS. Im Repository-Hauptordner:

```sh
npm ci
npm run dev
```

Die im Terminal angezeigte Adresse öffnen. Das Backend läuft standardmäßig unter `http://localhost:8081` und muss separat gestartet werden.
Für die lokale Frontend-Adresse `http://localhost:5173` ist CORS im Backend standardmäßig freigegeben.

Für ein anderes Backend eine `.env.local` anlegen (Vorlage: `.env.example`):

```dotenv
VITE_BACKEND_URL=https://securedocs-api-dh61.onrender.com
```

Danach den Entwicklungsserver neu starten. `VITE_BACKEND_URL` enthält nur die Basisadresse, ohne `/documents`.

## Produktionsbuild

```sh
npm run build
```

Dies prüft TypeScript und erstellt die Produktionsdateien unter `dist/`.

## Render

Die bestehende Static Site `securedocs-dh61` verwendet dieses Repository, Branch `main`:

| Einstellung | Wert |
|---|---|
| Root Directory | leer (Repository-Hauptordner) |
| Build Command | `npm ci && npm run build` |
| Publish Directory | `dist` |
| `NODE_VERSION` | `24` |
| `VITE_BACKEND_URL` | `https://securedocs-api-dh61.onrender.com` |

Nach Änderungen an `VITE_BACKEND_URL` ist ein neuer Build nötig. Bei Einbindung über die öffentliche Git-URL Änderungen mit „Manual Deploy“ bereitstellen.
Der kostenlose Backend-Dienst kann nach Inaktivität schlafen; der erste Aufruf benötigt dann mehr Zeit.

## Historie

Dieses Repository wurde aus dem bisherigen `frontend/`-Unterordner ausgegliedert. Die zugehörige Git-Änderungshistorie einschließlich des M2-Stands bleibt erhalten.
