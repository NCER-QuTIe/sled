<script setup>
//

const numberOfSlides = ref(1);
</script>

<template>
  <Pane
    class="min-w-96 flex flex-col gap-2 flex-grow main-board max-h-full overflow-y-scroll"
  >
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
/* .main-board {
  overflow: scroll;
} */
</style>
