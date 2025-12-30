<script setup>
defineProps({
  message: {
    type: String,
    required: true,
  },
  tries: {
    type: Number,
    required: true,
  },
});
</script>

<template>
  <div class="mt-4 rounded-xl border border-slate-200 bg-slate-50 p-4">
    <p class="text-lg font-semibold text-slate-700">
      {{ message }}
    </p>
    <p class="mt-2 text-sm text-slate-500">Essais : {{ tries }}</p>
  </div>
</template>

<style scoped></style>
