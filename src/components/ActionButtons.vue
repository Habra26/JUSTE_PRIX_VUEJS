<script setup>
defineEmits(["submit", "reset"]);
</script>

<template>
  <div class="mt-4 flex flex-col gap-3 sm:flex-row sm:items-center">
    <button
      type="button"
      @click="$emit('submit')"
      class="rounded-xl bg-indigo-600 px-4 py-2 font-semibold text-white hover:bg-indigo-700 active:scale-[0.99]"
    >
      Valider
    </button>

    <button
      type="button"
      @click="$emit('reset')"
      class="rounded-xl border border-slate-300 px-4 py-2 font-semibold text-slate-700 hover:bg-slate-100 active:scale-[0.99]"
    >
      Rejouer
    </button>
  </div>
</template>

<style scoped></style>