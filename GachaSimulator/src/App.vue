<script setup>
import { ref } from 'vue'
import PullButton from './components/PullButton.vue'
import PullHistory from './components/PullHistory.vue'

const pullHistory = ref([])
const currentPull = ref(null)

function handlePull(character) {
  currentPull.value = character
  pullHistory.value.unshift({ ...character })
  if (pullHistory.value.length > 20) {
    pullHistory.value.pop()
  }
}
</script>

<template>
  <div class="container">
    <h1>Gacha Simulator</h1>

    <!-- Pull Button -->
    <PullButton @pulled="handlePull" />

    <!-- Current Pull Display -->
    <div class="current-pull" v-if="currentPull">
      <img :src="currentPull.image" :alt="currentPull.name" class="current-image" />
      <h2>{{ currentPull.name }} - {{ currentPull.rarity }}★</h2>
    </div>

    <!-- History Component -->
    <PullHistory :history="pullHistory" />
  </div>
</template>

<style scoped>
.container {
  max-width: 700px;
  margin: 0 auto;
  padding: 2rem;
  text-align: center;
  font-family: Arial, sans-serif;
}

.current-pull {
  margin: 2rem 0;
}

.current-image {
  width: 120px;
  height: 120px;
  object-fit: contain;
  border: 3px solid #333;
  border-radius: 10px;
  margin-bottom: 1rem;
}
</style>
