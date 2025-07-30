<template>
  <div>
    <h1>代辦清單</h1>
    <ToDoForm @資料新增="addTodo" />
    <div class="todo-status">
      已完成 {{ completedCount }} 項 / 全部 {{ totalCount }} 項
    </div>
    <TodoItem
      v-for="item in ToDoItems"
      :key="item.id"
      :id="item.id"
      :label="item.label"
      :done="item.done"
      @資料改變="updateTodoStatus"
      @清單完成編輯="finishEditTodo"
      @清單編輯="editTodo"
      @清單刪除="deleteTodo"
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
      })
    },
    updateTodoStatus(id) {
      const item = this.ToDoItems.find(i => i.id === id)
      if (item) item.done = !item.done
    },
    editTodo({ id, label }) {
      const item = this.ToDoItems.find(i => i.id === id)
      if (item) item.label = label
    },
    finishEditTodo(id) {
      // 可根據需求擴充，暫不需額外處理
    },
    deleteTodo(id) {
      this.ToDoItems = this.ToDoItems.filter(i => i.id !== id)
    }
  }
};
</script>

<style>
/* ...existing code... */
</style>
