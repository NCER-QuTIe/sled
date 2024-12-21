<template>
  <Pane class="slide-base">
    <slot />
  </Pane>
</template>

<style scoped lang="scss">
.slide-base {
  aspect-ratio: 16/9;
  width: 768px;
  /* display: flex;
  flex-direction: column; */
  padding: 4px;
}
</style>
