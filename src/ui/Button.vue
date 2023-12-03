<template>
  <button :class="(type || 'secondary') + ' ' + (size || 'md')">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    type: "primary" | "secondary",
    size: "md" | "lg"
  }
}
</script>

<style scoped lang="scss">
  button {
    padding: 4px 8px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: transform 0.1s;
    width: min-content;

    &:active {
      transform: scale(0.98);
    }
  }
  .primary {
    color: white; 
    background-color: var(--main);
  }

  .secondary {
    color: var(--main);
    background-color: white;
    border: 1.5px solid var(--main);
  }

  .lg {
    font-size: 20px;
  }
</style>