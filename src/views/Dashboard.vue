<script setup>
import { onMounted, ref } from "vue";

import DatabaseCard from "./../components/DatabaseCard.vue";
import EmptyState from "./../components/EmptyState.vue";

const databases = ref([]);

onMounted(async () => {
  const res = await fetch("http://localhost:8080/databases");
  databases.value = await res.json();
});
</script>

<template>
  <div>
    <div class="max-w-6xl mx-auto px-6 py-10">
      <h1 class="text-3xl font-bold mb-8">Databases</h1>

      <div v-if="databases === null || databases.length === 0">
        <EmptyState />
      </div>

      <div class="grid md:grid-cols-2 gap-6">
        <DatabaseCard v-for="db in databases" :key="db.id" :database="db" />
      </div>
    </div>
  </div>
</template>
