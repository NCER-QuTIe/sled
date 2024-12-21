<script setup>
import Quill from "quill";
import "quill/dist/quill.core.css";
import "quill/dist/quill.bubble.css";

const item = useTemplateRef("editor");

let quill;
onMounted(
  () =>
    (quill = new Quill(item.value, {
      // debug: "info",
      modules: {
        toolbar: true,
      },
      placeholder: "ტექსტი ...",
      theme: "bubble",
    })),
);
</script>

<template>
  <div ref="editor"></div>
</template>

<style lang="scss">
.ql-container {
  margin: 4px;
  box-sizing: border-box;
  border: 1px solid gray;
  border-radius: 3px;
  height: 100%;
  max-height: 100%;
  overflow: hidden;

  .ql-editor {
    padding: 6px 12px;
    max-height: 100%;
  }

  .ql-toolbar {
    z-index: 100;
  }
}
</style>
