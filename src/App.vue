<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
    <header>
    <div class="header flex w-full justify-center">
      <nav class="flex flex-row items-center text-3xl gap-24 text-pink-100">
        <RouterLink to="/">início</RouterLink>
        <img class="w-32" src="../public/butterfly.png" alt="">
        <RouterLink to="/about">sobre</RouterLink>
      </nav>
    </div>
  </header>
  <RouterView />
</template>

<style scoped>
.header {
  margin-bottom: 2.5rem;
}
.router-link-exact-active {
  color: rgb(248, 125, 189);
}
</style>
