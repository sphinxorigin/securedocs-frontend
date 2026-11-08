<script setup lang="ts">
import { computed, ref } from 'vue'
import type { Document } from '../types/Document'

// Die Elternkomponente App.vue übergibt die Dokumente als Prop.
const props = defineProps<{ documents: Document[] }>()
const search = ref('')

// computed berechnet die Treffer bei Änderungen an Suche oder Dokumenten neu.
const filteredDocuments = computed(() => {
  const query = search.value.trim().toLocaleLowerCase('de')
  return props.documents.filter((document) =>
    `${document.filename} ${document.description}`.toLocaleLowerCase('de').includes(query),
  )
})
</script>

<template>
  <section class="document-panel" aria-labelledby="list-title">
    <div class="panel-heading">
      <div>
        <h2 id="list-title">Dokumentenübersicht</h2>
        <p class="result-count" role="status">
          {{ filteredDocuments.length }} von {{ documents.length }} Dokumenten
        </p>
      </div>
      <div class="search-field">
        <label for="document-search">Dokumente durchsuchen</label>
        <input
          id="document-search"
          v-model="search"
          type="search"
          placeholder="Dateiname oder Beschreibung"
        />
      </div>
    </div>

    <ul v-if="filteredDocuments.length" class="document-list">
      <!-- M2: Eigene Unterkomponente rendert eine Liste mit v-for. -->
      <li v-for="document in filteredDocuments" :key="document.id" class="document-row">
        <span class="file-icon" aria-hidden="true">PDF</span>
        <div class="document-details">
          <h3>{{ document.filename }}</h3>
          <p>{{ document.description }}</p>
        </div>
        <span class="document-id">ID {{ document.id }}</span>
      </li>
    </ul>
    <p v-else class="empty-state">
      {{ documents.length ? 'Keine passenden Dokumente gefunden.' : 'Noch keine Dokumente vorhanden.' }}
    </p>
  </section>
</template>
