<template>
  <form @submit.prevent="handleSave">
    <input v-model.lazy.trim="editValue" type="text" />
    <button type="submit">儲存</button>
    <button type="button" @click="handleCancel">取消</button>
  </form>
</template>

<script>
export default {
  name: 'ToDoItemEditForm',
  props: {
    value: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      editValue: this.value
    }
  },
  methods: {
    handleSave() {
      this.$emit('edit-todo', this.editValue)
    },
    handleCancel() {
      this.$emit('cancel-edit')
    }
  }
}
</script>
