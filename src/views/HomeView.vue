<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <main>
    <div class="flex flex-col items-center justify-center gap-5">
      <h1 class="text-3xl text-pink-400">Projetos</h1>
      <TheDivider class="!w-2/6 opacity-30"/>
      <div class="flex flex-col text-xl gap-6">
        <RouterLink to="/counter">Contador</RouterLink>
        <RouterLink to="/todo">To-do list</RouterLink>
      </div>
    </div>
  </main>
  <RouterView />
</template>
