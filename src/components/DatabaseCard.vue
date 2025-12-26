<script setup>
import StatusBadge from "./StatusBadge.vue";

defineProps({
  database: {
    type: Object,
    required: true,
  },
});

function formatDate(dateString) {
  const date = new Date(dateString);
  return date.toLocaleDateString();
}

function formatDuration(durationMs) {
  const duration = Math.round(durationMs / 1000);
  return `${duration}s`;
}
</script>

<template>
  <div class="border border-gray-800 rounded-2xl p-6 bg-gray-900">
    <div class="flex justify-between items-center mb-4">
      <h2 class="text-xl font-semibold text-amber-100">{{ database.name }}</h2>
      <span class="text-gray-400">{{ database.type }}</span>
    </div>

    <div class="space-y-3">
      <div class="flex justify-between text-green-50">
        <span>Last backup</span>
        <StatusBadge :status="database.last_backup.status" />
      </div>

      <div class="text-sm text-gray-400">
        {{ formatDate(database.last_backup.created_at) }} ·
        {{ formatDuration(database.last_backup.duration_ms) }}
      </div>

      <div class="flex justify-between mt-4 text-gray-50">
        <span>Last restore test</span>
        <StatusBadge :status="database.last_restore_test.status" />
      </div>

      <div class="text-sm text-gray-400">
        {{ formatDate(database.last_restore_test.created_at) }} ·
        {{ formatDuration(database.last_restore_test.duration_ms) }}
      </div>
    </div>
  </div>
</template>
