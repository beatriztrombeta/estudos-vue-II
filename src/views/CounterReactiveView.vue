<script setup>
import { reactive, computed, watchEffect } from 'vue';
import { useToast } from 'primevue/usetoast';

const state = reactive({ count: 0 })
const toast = useToast();

const isMultipleOfTen = computed(() => state.count % 10 === 0);

const alertMessage = computed(() => {
  if (isMultipleOfTen.value && state.count !== 0) {
    return `O número ${state.count} é uma dezena!`;
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

watchEffect(() => {
  if (isMultipleOfTen.value && state.count !== 0) {
    show();
  }
})

</script>

<template>
  <TheToast class="font-sans" />
  <main>
    <div class="flex flex-col gap-10 w-full h-full items-center justify-center">
      <span class="font-sans text-7xl">{{ state.count }}</span>
      <div class="flex flex-col gap-5">
        <div class="flex gap-10">
          <TheButton icon="pi pi-plus" @click="state.count++" :disabled="state.count >= 50" />
          <TheButton icon="pi pi-minus" @click="state.count--" :disabled="state.count <= 0" />
        </div>
        <div class="">
          <TheButton class="!font-sans w-full" @click="state.count = 0" :disabled="state.count === 0">Zerar</TheButton>
        </div>
      </div>
    </div>
  </main>
</template>
