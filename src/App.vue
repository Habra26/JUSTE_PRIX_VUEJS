<script setup>
import { ref } from "vue";
import ActionButtons from "./components/ActionButtons.vue";
import InstructionsTries from "./components/InstructionsTries.vue";
import GameHeader from "./components/GameHeader.vue";
import GuessInput from "./components/GuessInput.vue";
import GuessHistory from "./components/GuessHistory.vue";

const min = 1;
const max = 100;
const guess = ref("");

const tries = ref(0);
const message = ref('Entre un nombre et clique sur "Valider"');
const win = ref(false);

const secret = ref(generateSecret());

const history = ref([]);

const guessInputRef = ref(null);

// Générer le nombre secret
function generateSecret() {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

// Regénérer le nombre secret
function resetGame() {
  secret.value = generateSecret();
  guess.value = "";
  tries.value = 0;
  history.value = [];
  message.value = 'Nouvelle partie ! Entre un nombre et clique sur "Valider"';
  win.value = false;
}

// Valider
function submitGuess() {
  if (win.value) return;

  const n = Number(guess.value);

  if (!Number.isInteger(n)) {
    message.value = "Entre un nombre entier";
    return;
  }

  if (n < min || n > max) {
    message.value = `Choisis un nombre entre ${min} et ${max}.`;
    return;
  }

  tries.value += 1;

  if (n < secret.value) {
    message.value = "Trop petit";
    history.value.unshift({ value: n, result: "Trop petit" });
    guess.value = "";
    guessInputRef.value?.focus();
  } else if (n > secret.value) {
    message.value = "Trop grand";
    history.value.unshift({ value: n, result: "Trop grand" });
    guess.value = "";
    guessInputRef.value?.focus();
  } else {
    message.value = `Bravo, trouvé en ${tries.value} essais !`;
    history.value.unshift({ value: n, result: "Bravo !" });
    win.value = true;
    guess.value = "";
    guessInputRef.value?.focus();
  }
}
</script>

<template>
  <div class="min-h-screen bg-slate-50 text-slate-700">
    <div class="mx-auto max-w-xl px-4 py-16">
      <GameHeader :min="min" :max="max" />
      <main class="rounded-2xl border border-slate-200 bg-white p-5 shadow-sm">
        <!-- Input guess -->
        <GuessInput
          ref="guessInputRef"
          v-model="guess"
          :min="min"
          :max="max"
          @submit="submitGuess"
        />

        <!-- Valider + Rejouer -->
        <ActionButtons @submit="submitGuess" @reset="resetGame" />

        <!-- Consignes -->
        <InstructionsTries :message="message" :tries="tries" />

        <!-- Historique -->
        <GuessHistory :history="history" />
      </main>
    </div>
  </div>
</template>

<style scoped></style>
