<script setup lang="ts">
import type { ConcreteComponent } from "vue";

const { w = 1, h = 1 } = defineProps<{ w?: number; h?: number }>();

const child = ref<ConcreteComponent | string | null>(null);
const disabled = ref(false);

function drop(event: DragEvent) {
  event.preventDefault();

  console.log(event);

  let x = event.dataTransfer?.getData("name");
  if (x) {
    child.value = x;
    console.log(x);
    console.log(child.value);
  }
}
</script>

<template>
  <div
    class="drop-area"
    v-if="child == null && !disabled"
    :style="{
      width: 'calc(' + 100 * w + '% - 8px)',
      height: 'calc(' + 100 * h + '% - 8px)',
    }"
    @drop="drop"
    @dragover="$event.preventDefault()"
  >
    <b>Drop here</b>
    <i @click="disabled = true">remove</i>
  </div>
  <div
    v-if="child != null"
    class="container resize"
    :style="{ width: 100 * w + '%', height: 100 * h + '%' }"
  >
    <component :is="child"></component>
  </div>
</template>

<style lang="scss">
.container {
  /* height: 100%;
  width: 100%; */
  display: flex;
  flex-direction: column;
}

.drop-area {
  flex-grow: 1;
  width: calc(100% - 8px);
  height: calc(100% - 8px);
  margin: 4px;

  color: lightgray;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 0.5em;

  border: dashed 1px lightgray;
  border-radius: 0.25rem;
  background-color: #eee;
  box-sizing: border-box;
  user-select: none;

  i {
    font-size: 0.7em;
    cursor: pointer;
    :hover {
      font-weight: bold;
    }
  }
}
</style>
