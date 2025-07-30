<template>
  <div v-if="!isEditing">
    <input type="checkbox" :id="id" :checked="isDone" @change="handleCheckboxChange" />
    <label :for="id">{{ label }}</label>
    <button @click="isEditing = true">編輯</button>
    <button @click="handleDelete">刪除</button>
  </div>
  <ToDoItemEditForm
    v-else
    :value="label"
    @清單編輯="handleEdit"
    @取消編輯="handleCancelEdit"
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
    handleCheckboxChange() {
      this.isDone = !this.isDone
      this.$emit('checkbox變更', this.id)
    },
    handleDelete() {
      this.$emit('清單刪除', this.id)
    },
    handleEdit(newLabel) {
      this.$emit('清單編輯', { id: this.id, label: newLabel })
      this.isEditing = false
    },
    handleCancelEdit() {
      this.isEditing = false
    }
  }
}
</script>
