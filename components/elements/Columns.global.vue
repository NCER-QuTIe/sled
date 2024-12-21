<script setup lang="ts">
let split = ref(0.5);

let initial_offset = 0;
let initial_parent_width = 0;
let initial_parent_x = 0;
function registerEvents(event: any) {
  let boundingRect = event.target?.getBoundingClientRect();
  initial_offset = event.x - boundingRect.x - 8;
  let pb = event.target?.parentElement.getBoundingClientRect();
  initial_parent_width = pb.width;
  initial_parent_x = pb.x;
  document.addEventListener("mousemove", move);
  document.addEventListener("mouseup", mouseUpEvent);
}

function mouseUpEvent() {
  document.removeEventListener("mousemove", move);
  document.removeEventListener("mouseup", mouseUpEvent);
}

function move(event: any) {
  split.value =
    (event.x - initial_offset - initial_parent_x - 4) / initial_parent_width;
}
</script>

<template>
  <div class="columns">
    <ElementsContainer :w="split" :h="1" />
    <div
      @mousedown="registerEvents"
      class="column-resizer"
      :style="{ left: 'calc(' + 100 * split + '% - 4px)' }"
    />
    <ElementsContainer :w="1 - split" :h="1" />
  </div>
</template>

<style lang="scss">
.columns {
  flex-grow: 1;
  height: 100%;
  display: flex;
  position: relative;

  .column-resizer {
    width: 8px;
    height: calc(100% - 8px);
    display: block;
    position: absolute;
    content: " ";
    top: 4px;
    cursor: ew-resize;
    transition: background-color 0.2s;

    &:hover {
      background-color: #00000003;
    }
  }
}
</style>
