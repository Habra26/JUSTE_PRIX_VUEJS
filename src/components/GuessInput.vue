<script setup>
import { ref } from 'vue';

const inputRef = ref(null);

function focus() {
  inputRef.value?.focus();
}

defineExpose({ focus });

defineProps({
  modelValue: { type: [String, Number], default: "" },
  min: { type: Number, required: true },
  max: { type: Number, required: true },
});

defineEmits(["update:modelValue", "submit"]);
</script>

<template>
  <div>
    <label class="text-sm text-slate-600">Ta proposition ici :</label>
    <input
      ref="inputRef"
      type="number"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      @keydown.enter.prevent="$emit('submit')"
      :min="min"
      :max="max"
      placeholder="Ex: 42"
      class="mt-1 w-full rounded-xl border border-slate-300 bg-white px-3 py-2 outline-none focus:ring-2 focus:ring-indigo-500"
    />
  </div>
</template>

<style scoped></style>
