# SecureDocs Frontend

Vue 3 und TypeScript für Milestone 2 im Modul Webtechnologien.
Einzelteam: Danial Heidari, Gruppe 61, 2. Zug / 1. Gruppe, Prof. Wider.

## Voraussetzungen und Start

Node.js 22.12+ oder eine aktuelle Node.js-24-LTS-Version installieren.
Im Projektordner ausführen:

```sh
npm ci
npm run dev
```

Die im Terminal ausgegebene lokale URL im Browser öffnen.

## Prüfung

```sh
npm run build
```

Prüft die TypeScript-Typen und erzeugt die Produktionsdateien in `dist/`.

## M2-Anforderungen

- Vue-App: `src/App.vue`
- Eigene Unterkomponente: `src/components/DocumentList.vue`
- Liste von Beispiel-Entitäten: zwei Dokumente in `src/App.vue`, passend zum Backend
- Darstellung mit `v-for`: in `DocumentList.vue`, mit eindeutiger `:key="document.id"`
- GitHub: Dieses Projekt muss noch in ein eigenes Frontend-Repository gepusht werden.
  Anschließend dessen URL als M2-Abgabe einreichen.

## Aufbau und Erklärung

`main.ts` startet Vue und setzt `App.vue` in das HTML-Element mit ID `app` ein.
`App.vue` enthält die Beispieldaten und bindet `DocumentList` ein.
`:documents="documents"` übergibt die Daten als Prop an die Unterkomponente.
`defineProps` beschreibt den Typ der angenommenen Daten.
`v-for` erstellt für jedes gefilterte Dokument einen Listeneintrag.
`:key` identifiziert jeden Eintrag über seine stabile ID.
`v-model` verbindet das Suchfeld mit `search`. `computed` aktualisiert die Treffer.
Die Suche ist eine kleine Zusatzfunktion, keine zusätzliche M2-Anforderung.

## Geplanter GitHub-Upload

Ein leeres Repository namens `securedocs-frontend` auf GitHub erstellen.
Danach im entpackten Projektordner ausführen:

```sh
git init
git add .
git commit -m "Add Vue frontend for milestone 2"
git branch -M main
git remote add origin https://github.com/sphinxorigin/securedocs-frontend.git
git push -u origin main
```

Die URL ist das vorgeschlagene neue Ziel. Das Repository wurde durch dieses Paket
weder erstellt noch auf GitHub hochgeladen. Falls du einen anderen Namen oder
Account wählst, passe die Remote-URL an.

Backend: https://github.com/sphinxorigin/securedocs
Referenz des Dozenten: https://github.com/ProfWider/thing-frontend

## Stand und Grenzen

Die Daten sind lokal und werden bei Änderungen nicht gespeichert.
Noch keine Backend-Anbindung, Datei-Uploads, Downloads, Anmeldung oder
Zugriffskontrolle. Diese Ansicht bietet daher noch keine sichere Dateiablage.
M3 ergänzt Backend-Kommunikation und Deployment, M4 die Datenbankanbindung.
Für die Endabgabe sind zusätzlich Tests und GitHub Actions erforderlich.

## Grundlage

Moodle-Screenshots zu M2: eigene Unterkomponente und Liste mit v-for,
Abgabe des Frontend-Repository-Links am 08.11.2026.
`npm-jest-vue-init.pdf`, Folien 10-13: Vue-Einrichtung, TypeScript und Start.
Die Struktur wurde für den aktuellen M2-Umfang vereinfacht.
