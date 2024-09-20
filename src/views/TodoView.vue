<script setup>
import CustomTodoComponent from '@/components/CustomTodoComponent.vue'
import { ref, provide } from 'vue'

const newTodo = ref('')
const todos = ref([])

provide('deleteTodo', deleteTodo)
provide('editTodo', editTodo)

const handleInsert = () => {
  if (newTodo.value) {
    todos.value.push({
      id: Date.now(),
      title: newTodo.value
    })
    newTodo.value = ''
  }
}

function deleteTodo(id) {
  const todoIndex = todos.value.findIndex(todo => todo.id === id)
  if (todoIndex !== -1) {
    todos.value.splice(todoIndex, 1)
  }
}

function editTodo(id, newTitle) {
  const todoIndex = todos.value.findIndex(todo => todo.id === id)
  if (todoIndex !== -1) {
    todos.value[todoIndex].title = newTitle
  }
}


</script>

<template>
  <TheToast class="font-sans" />
  <ConfirmDialog class="font-sans"></ConfirmDialog>
  <main class="flex flex-col items-center justify-center font-sans gap-12">
    <section>
      <InputGroup>
        <InputText type="text" v-model="newTodo" placeholder="Adicionar to-do..." />
        <TheButton icon="pi pi-plus" @click="handleInsert" />
      </InputGroup>
    </section>
    <section>
      <CustomTodoComponent v-for="todo in todos" :key="todo.id" :text="todo.title" :id="todo.id"/>
    </section>
  </main>
</template>
