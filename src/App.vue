<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>


<template>
  <h1 class="sr-only">To Do App</h1>
  <main>
    <article class="todo-app">
      <RouterLink to="/"></RouterLink>
      <RouterView></RouterView>
    </article>
  </main>

  
</template>


<style lang="scss" scoped>
  .todo-app {
    width: calc(23.4375 * $space-base);
    max-width: 100%;
    min-height: 623px;
    background: $primary-wht;
    margin: calc($space-base) auto;
    padding-bottom: calc(2 * $space-base);
  }
</style>
