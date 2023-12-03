<template>
  <input :value="modelValue" @input="updateInputValue" />
</template>

<script>
  export default {
    props: {
      modelValue: [String, Number]
    },
    methods: {
      updateInputValue() {
        this.$emit("update:modelValue", event.target.value)
      }
    }
  }
</script>

<style>
input {
  outline-color: var(--main);
  background-image: radial-gradient(#fff, #e1f3ff)
}
</style>