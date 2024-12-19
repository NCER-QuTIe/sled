<template>
  <span>
    <slot />
  </span>
</template>

<style scoped lang="scss">
span {
  border: 1px solid gray;
  border-radius: 0.25rem;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0.25rem;
  height: 2.2rem;
  width: 2.2rem;
  box-sizing: border-box;
}
</style>
