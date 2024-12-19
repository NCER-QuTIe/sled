<script setup lang="ts">
function drag(event: DragEvent) {
  event.dataTransfer?.setData("name", "ElementsText");
}
</script>

<template>
  <ElementsListingsBase @dragstart="drag">
    <template v-slot:icon>
      <b class="h-fit underline"> T </b>
    </template>
    <template v-slot:name> Text </template>
  </ElementsListingsBase>
</template>
