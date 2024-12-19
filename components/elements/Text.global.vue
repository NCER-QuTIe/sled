<script setup lang="ts">
//
import { QuillEditor } from "@vueup/vue-quill";
import "@vueup/vue-quill/dist/vue-quill.bubble.css";
</script>

<template>
  <div class="flex-grow box-border border border-solid border-gray-200 rounded">
    <QuillEditor theme="bubble"> </QuillEditor>
  </div>
  <ElementsContainer />
</template>

<style lang="scss">
.ql-editor {
  padding: 6px 12px;
}
</style>
