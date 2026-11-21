<script setup lang="ts">
import DocumentList from "./components/DocumentList.vue";
import type { Document } from "./types/Document";
import { onMounted, ref } from "vue";

const documents = ref<Document[]>([]);
const loading = ref(true);
const error = ref("");
const backendUrl = (import.meta.env.VITE_BACKEND_URL || "http://localhost:8081").replace(/\/$/, "");

async function loadDocuments() {
  loading.value = true;
  error.value = "";
  try {
    const response = await fetch(`${backendUrl}/documents`);
    if (!response.ok) throw new Error(`HTTP ${response.status}`);
    documents.value = await response.json();
  } catch {
    error.value = "Die Dokumente konnten nicht geladen werden. Bitte versuche es erneut.";
  } finally {
    loading.value = false;
  }
}

onMounted(loadDocuments);
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
          Die Beispieldokumente werden vom Server geladen. Upload, Anmeldung und
          Freigaben folgen später.
        </p>
      </aside>
      <p v-if="loading" class="notice" role="status">
        Dokumente werden geladen … Beim ersten Aufruf kann der Server etwas Zeit benötigen.
      </p>
      <div v-else-if="error" class="notice" role="alert">
        <p>{{ error }}</p>
        <button type="button" class="retry-button" @click="loadDocuments">Erneut versuchen</button>
      </div>
      <DocumentList v-else :documents="documents" />
    </main>

  </div>
</template>
