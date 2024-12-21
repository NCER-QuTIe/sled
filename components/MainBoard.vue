<script setup>
//

const numberOfSlides = ref(1);
</script>

<template>
  <Pane class="main-board">
    <div class="h-0">
      <div class="flex flex-col gap-2 pb-2">
        <SlideBase v-for="i in numberOfSlides" :key="i">
          <ElementsContainer />
        </SlideBase>
        <SlideNewSlideButtons @addSlide="numberOfSlides++" />
      </div>
    </div>
  </Pane>
</template>

<style scoped lang="scss">
.main-board {
  overflow: auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;

  flex-grow: 1;

  max-height: 100%;
  min-width: fit-content;
}
</style>
