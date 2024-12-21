<script setup lang="ts">
let split = ref(0.5);

let initial_offset = 0;
let initial_parent_height = 0;
let initial_parent_y = 0;
function registerEvents(event: any) {
  let boundingRect = event.target?.getBoundingClientRect();
  initial_offset = event.y - boundingRect.y - 8;
  let pb = event.target?.parentElement.getBoundingClientRect();
  initial_parent_height = pb.height;
  initial_parent_y = pb.y;
  document.addEventListener("mousemove", move);
  document.addEventListener("mouseup", mouseUpEvent);
}

function mouseUpEvent() {
  document.removeEventListener("mousemove", move);
  document.removeEventListener("mouseup", mouseUpEvent);
}

function move(event: any) {
  split.value =
    (event.y - initial_offset - initial_parent_y - 4) / initial_parent_height;
}
</script>

<template>
  <div class="rows">
    <ElementsContainer :h="split" :w="1" />
    <div
      @mousedown="registerEvents"
      class="rows-resizer"
      :style="{ top: 'calc(' + 100 * split + '% - 4px)' }"
    />
    <ElementsContainer :h="1 - split" :w="1" />
  </div>
</template>

<style lang="scss">
.rows {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
  position: relative;

  .rows-resizer {
    height: 8px;
    width: calc(100% - 8px);
    display: block;
    position: absolute;
    content: " ";
    left: 4px;
    cursor: ns-resize;
    transition: background-color 0.2s;

    &:hover {
      background-color: #00000003;
    }
  }
}
</style>
