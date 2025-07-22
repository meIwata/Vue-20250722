<template>
  <form @submit.prevent="onSubmit">
    <label for="todo-input">新增代辦事項：</label>
    <input id="todo-input" v-model.lazy.trim="label" required/>
    <button type="submit">新增</button>
  </form>
</template>

<script>
export default {
  name: 'ToDoForm',
  data() {
    return {
      label: ''
    };
  },
  methods: {
    onSubmit() {
      if (this.label.trim() === '') return;
      this.$emit('add-todo', this.label);
      this.label = '';
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
