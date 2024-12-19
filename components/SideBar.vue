<script setup>
import {
  ElementsListingsText,
  ElementsListingsColumns,
  ElementsListingsRows,
} from "#components";
let elements = [
  ElementsListingsText,
  ElementsListingsColumns,
  ElementsListingsRows,
];
</script>

<template>
  <Pane class="w-52 flex gap-2 flex-col">
    <component v-for="element in elements" :is="element" />
  </Pane>
</template>
