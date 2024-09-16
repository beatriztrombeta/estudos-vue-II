<script setup>
import { ref, inject } from 'vue'
import { useConfirm } from 'primevue/useconfirm'
import { useToast } from 'primevue/usetoast'

//--------------CONSTANTES-----------------

const props = defineProps({
  id: Number,
  text: String
})

const checked = ref(false)
const visible = ref(false)
const isEditing = ref(false)
const newTitle = ref(props.text)

const confirm = useConfirm()

const toast = useToast()

const editTodo = inject('editTodo')
const deleteTodo = inject('deleteTodo')

//-----------------FUNÇÕES-------------------

const handleEdit = () => {
  if (isEditing.value) {
    if (newTitle.value.trim()) {
      editTodo(props.id, newTitle.value)  
      isEditing.value = false
      visible.value = false
    }
  } else {
    isEditing.value = true
    visible.value = true
  }
}

const handleDelete = () => {
  confirm.require({
    message: `Do you want to delete this record?`,
    header: 'Danger Zone',
    icon: 'pi pi-info-circle',
    rejectProps: {
      label: 'Cancel',
      severity: 'secondary',
      outlined: true
    },
    acceptProps: {
      label: 'Delete',
      severity: 'danger'
    },
    accept: () => {
      deleteTodo(props.id)
      toast.add({ severity: 'info', summary: 'Confirmed', detail: 'Record deleted', life: 3000 })
    }
  })
}
</script>

<template>
  <TheDialog
    class="font-sans"
    v-model:visible="visible"
    modal
    header="Edit To-do"
    :style="{ width: '25rem' }"
  >
    <span class="text-surface-500 dark:text-surface-400 block mb-8">Update your information.</span>
    <div class="flex items-center mb-4">
      <label for="title" class="font-semibold w-24">To-do</label>
      <InputText id="title" class="flex-auto" autocomplete="off" v-model="newTitle" />
    </div>
    <div class="flex justify-end gap-2">
      <TheButton
        type="button"
        label="Cancel"
        severity="secondary"
        @click="visible = false"
      ></TheButton>
      <TheButton type="button" label="Save" @click="handleEdit"></TheButton>
    </div>
  </TheDialog>
  <main class="flex flex-col gap-5 items-start">
    <section class="flex flex-row items-center justify-between gap-4">
      <div class="flex flex-row gap-4">
        <TheCheckbox v-model="checked" :binary="true" />
        <label>{{ props.text }}</label>
      </div>
      <div class="flex flex-row">
        <TheButton icon="pi pi-pencil" aria-label="edit" @click="handleEdit" text />
        <TheButton icon="pi pi-trash" aria-label="delete" @click="handleDelete" text />
      </div>
    </section>
  </main>
</template>

<style></style>
