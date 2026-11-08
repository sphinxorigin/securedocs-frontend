<script setup lang="ts">
import DocumentList from "./components/DocumentList.vue";
import type { Document } from "./types/Document";

// Lokale Beispieldaten
const documents: Document[] = [
  {
    id: 1,
    filename: "studienbescheinigung.pdf",
    description: "Studienbescheinigung für das Wintersemester",
  },
  {
    id: 2,
    filename: "projektbeschreibung.pdf",
    description: "Beschreibung des SecureDocs-Projekts",
  },
];
</script>

<template>
  <div class="page">
    <header class="site-header">
      <a class="brand" href="./" aria-label="SecureDocs Startseite">
        <span class="brand-icon" aria-hidden="true">S</span>
        SecureDocs
      </a>
    </header>

    <main>
      <section class="intro" aria-labelledby="page-title">
        <h1 id="page-title">Meine Dokumente</h1>
        <p class="intro-text">
          Alle Dokumente auf einen Blick. Klar geordnet und schnell auffindbar.
        </p>
      </section>
      <aside class="notice" aria-label="Entwicklungsstand">
        <strong>Demo mit Beispieldaten</strong>
        <p>
          Diese Ansicht zeigt lokale Beispieldaten. Upload, Anmeldung und
          Freigaben werden noch implementiert ...
        </p>
      </aside>
      <DocumentList :documents="documents" />
    </main>

  </div>
</template>
