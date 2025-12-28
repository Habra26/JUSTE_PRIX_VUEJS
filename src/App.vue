<script setup>
const min = 1;
const max = 100;
</script>

<template>
  <div class="min-h-screen bg-slate-50 text-slate-700">
    <div class="mx-auto max-w-xl px-4 py-16">
      <header class="mb-8">
        <h1 class="text-3xl font-bold text-indigo-600">
          Juste Prix
        </h1>
        <p class="mt-2 text-sm text-slate-500">
          Devine le nombre entre {{ min }} et {{ max }}.
        </p>
      </header>
    </div>
  </div>
</template>

<style scoped></style>
