<script setup lang="ts">
defineProps({
  class: {
    type: String,
    default: "",
  },
});
</script>

<template>
  <div :class="class">
    <slot />
  </div>
</template>

<style lang="scss" scoped>
div {
  padding: 0.5rem;
  border-radius: 0.25rem;
  border: 1px solid gray;
  background-color: #eee8;
}
</style>
