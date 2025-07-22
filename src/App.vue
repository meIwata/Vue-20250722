<template>
  <div>
    <h1>代辦清單</h1>
    <ToDoForm @add-todo="addTodo" />
    <div class="todo-status">
      已完成 {{ completedCount }} / 全部 {{ totalCount }} 項
    </div>
    <TodoItem
      v-for="item in ToDoItems"
      :key="item.id"
      :id="item.id"
      :label="item.label"
      :done="item.done"
      @change="updateTodoStatus"
    />
  </div>
</template>

<script>
import { nanoid } from 'nanoid';
import TodoItem from './components/TodoItem.vue';
import ToDoForm from './components/ToDoForm.vue';

export default {
  name: 'App',
  components: {
    TodoItem,
    ToDoForm
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
  },
  computed: {
    completedCount() {
      return this.ToDoItems.filter(item => item.done).length;
    },
    totalCount() {
      return this.ToDoItems.length;
    }
  },
  methods: {
    addTodo(label) {
      this.ToDoItems.push({
        id: 'todo-' + nanoid(),
        label,
        done: false
      });
    },
    updateTodoStatus({ id, done }) {
      const item = this.ToDoItems.find(item => item.id === id);
      if (item) item.done = done;
    }
  }
};
</script>

<style>
/* ...existing code... */
</style>
