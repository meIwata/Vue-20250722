<template>
  <div v-if="!isEditing">
    <input type="checkbox" :id="id" :checked="isDone" @change="handleToggle" />
    <label :for="id">{{ label }}</label>
    <button class="pure-button button-success" @click="isEditing = true">編輯</button>
    <button class="pure-button button-error" @click="handleDelete">刪除</button>
  </div>
  <ToDoItemEditForm
    v-else
    :value="label"
    @edit-todo="handleEdit"
    @cancel-edit="handleCancelEdit"
  />
</template>

<script>
import ToDoItemEditForm from './ToDoItemEditForm.vue'
export default {
  name: 'TodoItem',
  components: { ToDoItemEditForm },
  props: {
    label: {
      type: String,
      required: true
    },
    done: {
      type: Boolean,
      required: true
    },
    id: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      isDone: this.done,
      isEditing: false
    }
  },
  methods: {
    handleToggle() {
      this.isDone = !this.isDone
      this.$emit('toggle-todo', this.id)
    },
    handleDelete() {
      this.$emit('delete-todo', this.id)
    },
    handleEdit(newLabel) {
      this.$emit('edit-todo', { id: this.id, label: newLabel })
      this.isEditing = false
    },
    handleCancelEdit() {
      this.isEditing = false
    }
  }
}
</script>
