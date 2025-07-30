<template>
  <form @submit.prevent="handleAdd">
    <label for="todo-input">待辦事項：</label>
    <input id="todo-input" v-model.lazy.trim="inputValue" type="text" />
    <button type="submit">新增</button>
  </form>
</template>

<script>
export default {
  name: 'ToDoForm',
  data() {
    return {
      inputValue: ''
    }
  },
  methods: {
    handleAdd() {
      if (this.inputValue) {
        this.$emit('資料新增', this.inputValue)
        this.inputValue = ''
      }
    }
  }
}
</script>

