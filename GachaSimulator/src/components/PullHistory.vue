<script setup>
defineProps({
  history: Array
})
</script>

<template>
  <div class="history-wrapper">
    <h3>Pull History</h3>
    <div class="history-scroll">
      <div
        v-for="(char, index) in history"
        :key="index"
        class="history-entry"
        :class="`rarity-${char.rarity}`"
      >
        <img :src="char.image" :alt="char.name" />
        <p>{{ char.rarity }}★</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.history-wrapper {
  margin-top: 2rem;
}

.history-scroll {
  display: flex;
  gap: 12px;
  overflow-x: auto;
  padding: 10px 0;
}

.history-entry {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 60px;
  padding: 4px;
  border-radius: 6px;
  flex-shrink: 0;
}

.history-entry img {
  width: 50px;
  height: 50px;
  object-fit: contain;
  border-radius: 5px;
  margin-bottom: 0.5rem;
}

.rarity-5 {
  border: 2px solid gold;
}
.rarity-4 {
  border: 2px solid purple;
}
.rarity-3 {
  border: 2px solid blue;
}
</style>
