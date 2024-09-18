<script setup>
import { ref, computed, watch } from 'vue';
import { useToast } from 'primevue/usetoast';

const count = ref(0);
const toast = useToast();

const isMultipleOfTen = computed(() => count.value % 10 === 0);

const alertMessage = computed(() => {
  if (isMultipleOfTen.value && count.value !== 0) {
    return `O número ${count.value} é uma dezena!`;
  }
  return '';
});

const show = () => {
  toast.add({
    severity: 'secondary',
    summary: 'Atenção!!!!',
    detail: alertMessage.value,
    life: 3000
  });
};


watch(isMultipleOfTen, (newVal) => {
  if (newVal && count.value !== 0) {
    show();
  }
});

</script>

<template>
  <TheToast class="font-sans" />
  <main>
    <div class="flex flex-col gap-10 w-full h-full items-center justify-center">
      <span class="font-sans text-7xl">{{ count }}</span>
      <div class="flex flex-col gap-5">
        <div class="flex gap-10">
          <TheButton icon="pi pi-plus" @click="count++" :disabled="count >= 50" />
          <TheButton icon="pi pi-minus" @click="count--" :disabled="count <= 0" />
        </div>
        <div class="">
          <TheButton class="!font-sans w-full" @click="count = 0" :disabled="count === 0">Zerar</TheButton>
        </div>
      </div>
    </div>
  </main>
</template>
