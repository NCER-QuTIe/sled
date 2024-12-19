<script setup lang="ts">
function drag(event: DragEvent) {
  event.dataTransfer?.setData("name", "ElementsRows");
}
</script>

<template>
  <ElementsListingsBase @dragstart="drag">
    <template v-slot:icon>
      <div class="row-element-icon">
        <div>1</div>
        <div>2</div>
      </div>
    </template>
    <template v-slot:name> Rows </template>
  </ElementsListingsBase>
</template>

<style scoped lang="scss">
div.row-element-icon {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  gap: calc(0.25rem - 1px);
  align-items: stretch;

  div {
    height: 100%;
    flex-grow: 1;
    border: 1px solid black;
    border-radius: 2px;
    font-size: 0.5rem;
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
    box-sizing: border-box;
    height: fit-content;
  }
}
</style>
