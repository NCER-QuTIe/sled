<script setup lang="ts">
defineEmits(["addSlide"]);
</script>

<template>
  <div id="new-slide-buttons">
    <button @click="$emit('addSlide')">Add Slide</button>
    <button @click="$emit('addSlide')">Link Slide</button>
  </div>
</template>

<style lang="scss">
#new-slide-buttons {
  width: 100%;
  flex-grow: 1;
  min-height: 14rem;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 0.5rem;
}
</style>
