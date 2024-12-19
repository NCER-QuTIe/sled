<template>
  <div draggable="true">
    <Icon>
      <slot name="icon" />
    </Icon>
    <slot name="name" />
  </div>
</template>

<style scoped lang="scss">
div {
  padding: 0.5rem;
  border-radius: 0.25rem;
  background-color: white;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
</style>
