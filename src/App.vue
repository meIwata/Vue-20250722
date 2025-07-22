<template>
  <div>
    <h1>代辦清單</h1>
    <TodoItem
      v-for="item in ToDoItems"
      :key="item.id"
      :id="item.id"
      :label="item.label"
      :done="item.done"
    />
  </div>
</template>

<script>
import { nanoid } from 'nanoid';
import TodoItem from './components/TodoItem.vue';

export default {
  name: 'App',
  components: {
    TodoItem
  },
  data() {
    return {
      ToDoItems: [
        { id: 'todo-' + nanoid(), label: '買牛奶', done: false },
        { id: 'todo-' + nanoid(), label: '寫作業', done: true },
        { id: 'todo-' + nanoid(), label: '運動30分鐘', done: false },
        { id: 'todo-' + nanoid(), label: '閱讀10頁', done: false }
      ]
    };
  }
};
</script>

<style>
/* ...existing code... */
</style>
