<script setup lang="ts">
import type { ConcreteComponent } from "vue";

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
    @drop="drop"
    @dragover="$event.preventDefault()"
  >
    <b>Drop here</b>
    <i @click="disabled = true">remove</i>
  </div>
  <div v-if="child != null" class="flex-grow w-full flex flex-col gap-2">
    <component :is="child"></component>
  </div>
</template>

<style lang="scss">
.drop-area {
  width: 100%;
  flex-grow: 1;
  /* height: 100%; */
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

  i {
    font-size: 0.7em;
    cursor: pointer;
    :hover {
      font-weight: bold;
    }
  }
}
</style>
