<script setup>
defineProps({
  status: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <span
    :class="[
      'px-3 py-1 rounded-full text-sm font-semibold',
      status === 'success'
        ? 'bg-green-900 text-green-300'
        : 'bg-red-900 text-red-300',
    ]"
  >
    {{ status.toUpperCase() }}
  </span>
</template>
