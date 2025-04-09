<template>
  <div class="text-center">
    <button @click="performPull" class="px-4 py-2 bg-indigo-600 text-white rounded">
      Pull
    </button>
    <div v-if="result" class="mt-4">
      <h2>You pulled: {{ result.name }} ({{ result.rarity }}★)</h2>
      <img :src="result.image" :alt="result.name" class="w-32 h-32 mx-auto mt-2" />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { characterPool } from '../data/characterPool'

const result = ref(null)

function performPull() {
  const roll = Math.random()
  let cumulative = 0

  for (const character of characterPool) {
    cumulative += character.rate
    if (roll < cumulative) {
      result.value = character
      break
    }
  }
}
</script>

<style scoped>
img {
  border-radius: 8px;
}
</style>
