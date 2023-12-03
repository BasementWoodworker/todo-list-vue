<template>
  <form class="form" @submit.prevent="emitAdd">
    <h1 class="form__title">Создать новый элемент</h1>
    <Input v-model="text" />
    <Button type="primary" size="lg">Добавить</Button>
    <span class="form__error">{{ error }}</span>
  </form>
</template>

<script>
  import Input from '../ui/Input.vue';
  import Button from '../ui/Button.vue';
  export default {
    components: {
      Input: Input,
      Button: Button
    },
    data() {
      return {
        text: "",
        error: ""
      }
    },
    methods: {
      emitAdd() {
        if (this.text === "") {
          this.error = "Text is required";
          return;
        }
        this.$emit("add", this.text);
        this.text = "";
        this.error = "";
      }
    }
  }
</script>

<style scoped lang="scss">
.form {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: min-content;
  gap: 10px;
  padding: 10px;
  box-shadow: 0 0 10px grey;

  &__title {
    font-size: 20px;
    white-space: nowrap;
    margin: 0;
  }

  &__error {
  color: orangered;
  white-space: nowrap;
}
}
</style>