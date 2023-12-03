<template>
  <div class="todo">
    <p class="todo__text" v-if="!isEditing">{{ text }}</p>
    <Input v-else v-model="text" />
    <div class="buttons">
      <Button v-if="!this.isEditing" @click="this.isEditing = true">Редактировать</Button>
      <Button v-else @click="this.emitSaveEdited">Сохранить</Button>
      <Button @click="emitDelete">Удалить</Button>
    </div>
  </div>
</template>

<script>
  import Button from '../ui/Button.vue';
  import Input from '../ui/Input.vue';
  export default {
    components: {
      Button: Button,
      Input: Input
    },
    props: {
      todo: Object
    },
    data() {
      return {
        isEditing: false,
        text: this.todo.text
      }
    },
    methods: {
      emitSaveEdited() {
        console.log(this.text)
        this.$emit("saveEdited", {
          id: this.todo.id,
          text: this.text
        })
        this.isEditing = false;
      },
      emitDelete() {
        this.$emit("delete", this.todo.id);
      }
    }
  }
</script>

<style scoped lang="scss">
.todo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: min-content;
  gap: 10px;
  border-bottom: 1px solid var(--main);
  padding: 10px;

  &__text {
    margin: 0;
  }
  .buttons {
    display: flex;
    gap: 4px;
  }
}
</style>