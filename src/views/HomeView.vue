<script setup>
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'

const paths = ref(['/refcounter', '/reactivecounter', '/todo'])
const titles = ref(['Contador - ref', 'Contador - reactive', 'To-do List'])
</script>

<template>
  <main>
    <div class="flex flex-col items-center justify-center gap-5">
      <h1 class="text-3xl text-pink-400">Projetos</h1>
      <TheDivider class="!w-2/6 opacity-30"/>
      <div class="flex flex-col text-xl gap-6 justify-center items-center">
        <RouterLink
          class="hover:text-customRed active:text-customRed active:underline hover:underline"
          v-for="(path, index) in paths"
          :key="path"
          :to="path"
        >
          {{ titles[index] }}
        </RouterLink>
      </div>
    </div>
  </main>
  <RouterView />
</template>
