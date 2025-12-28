<script setup>
import { ref } from "vue";
import ActionButtons from "./components/ActionButtons.vue";

const min = 1;
const max = 100;
const guess = ref("");

const secret = ref(generateSecret());

// Générer le nombre secret
function generateSecret() {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

// Regénérer le nombre secret
function resetGame() {
  secret.value = generateSecret();
  guess.value = "";
}

// Valider
function submitGuess() {
  console.log("submit");
}
</script>

<template>
  <div class="min-h-screen bg-slate-50 text-slate-700">
    <div class="mx-auto max-w-xl px-4 py-16">
      <header class="mb-8">
        <h1 class="text-3xl font-bold tracking-tight text-indigo-600">
          Juste Prix
        </h1>
        <p class="mt-2 text-sm text-slate-500">
          Devine le nombre entre {{ min }} et {{ max }}.
        </p>
      </header>
      <main class="rounded-2xl border border-slate-200 bg-white p-5 shadow-sm">
        <!-- Input guess -->
        <div>
          <label class="text-sm text-slate-600">Ta proposition ici :</label>
          <input
            v-model="guess"
            type="number"
            :min="min"
            :max="max"
            placeholder="Ex: 42"
            class="mt-1 w-full rounded-xl border border-slate-300 bg-white px-3 py-2 outline-none focus:ring-2 focus:ring-indigo-500"
          />
        </div>

        <p class="mt-3 text-sm text-slate-400">
          Ton choix : {{ guess || "" }}
        </p>

        <!-- Valider + Rejouer -->
        <ActionButtons @submit="submitGuess" @reset="resetGame" />

        <!-- Consignes -->
        <div class="mt-4 rounded-xl border border-slate-200 bg-slate-50 p-4">
          <p class="text-lg font-semibold text-slate-700">
            Entre un nombre et clique sur "Valider"
          </p>
          <p class="mt-2 text-sm text-slate-500">Essais : 0</p>
        </div>

        <!-- Historique -->
        <div class="mt-5">
          <h2 class="text-sm font-semibold text-slate-700">Historique</h2>
          <p class="mt-2 text-sm text-slate-500">Aucune tentative</p>
        </div>
      </main>
    </div>
  </div>
</template>

<style scoped></style>
