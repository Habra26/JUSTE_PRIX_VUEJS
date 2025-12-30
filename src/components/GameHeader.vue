<script setup>
defineProps({
  min: { type: Number, required: true },
  max: { type: Number, required: true },
});
</script>

<template>
  <header class="mb-8">
    <h1 class="text-3xl font-bold tracking-tight text-indigo-600">
      Juste Prix
    </h1>
    <p class="mt-2 text-sm text-slate-500">
      Devine le nombre entre {{ min }} et {{ max }}.
    </p>
  </header>
</template>

<style scoped></style>
