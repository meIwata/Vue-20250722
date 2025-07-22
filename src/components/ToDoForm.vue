<template>
  <form @submit.prevent="onSubmit">
    <label for="todo-input">新增代辦事項：</label>
    <input id="todo-input" v-model="inputValue" required />
    <button type="submit">新增</button>
  </form>
</template>

<script>
export default {
  name: 'ToDoForm',
  data() {
    return {
      inputValue: ''
    };
  },
  methods: {
    onSubmit() {
      this.$emit('add-todo', this.inputValue);
      this.inputValue = '';
    }
  }
};
</script>

<style scoped>
form {
  margin-bottom: 1em;
}
label {
  margin-right: 0.5em;
}
input {
  margin-right: 0.5em;
}
</style>

