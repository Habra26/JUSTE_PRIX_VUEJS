<script setup>
defineProps({
  history: {
    type: Array,
    required: true,
  },
});
</script>

<template>
  <div class="mt-5">
    <h2 class="text-sm font-semibold text-slate-700">Historique</h2>
    <ul v-if="history.length" class="mt-2 space-y-1">
      <li v-for="item in history" :key="item" class="text-sm text-slate-600">
        {{ item.value }} - {{ item.result }}
      </li>
    </ul>

    <p v-else class="mt-2 text-sm text-slate-500">
      Aucune tentative pour l'instant.
    </p>
  </div>
</template>

<style scoped></style>
