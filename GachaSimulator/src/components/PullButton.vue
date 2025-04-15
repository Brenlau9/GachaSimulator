<script setup>
import { characterPool } from '../data/characterPool'
const emit = defineEmits(['pulled'])

function performPull() {
  const roll = Math.random()
  let cumulative = 0

  for (const character of characterPool) {
    cumulative += character.rate
    if (roll < cumulative) {
      emit('pulled', character)
      break
    }
  }
}
</script>

<template>
  <div>
    <button @click="performPull">Pull!</button>
  </div>
</template>

<style scoped>
button {
  padding: 0.5rem 1.2rem;
  font-size: 1.2rem;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}
</style>
