<script setup>
import { RouterLink, RouterView } from "vue-router";
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
main {
  width: 100%;
  min-height: 100vh;
  @include placement(flex, row, flex-start, center);
  @include bp(seed) {
    background: center / cover no-repeat url("./assets/bg-1.jpg");
  }
}
.todo-app {
  width: calc(23.4375 * $space-base);
  max-width: 100%;
  height: 100vh;
  background: $primary-wht;
  margin: $space-base auto;
  padding-bottom: calc(2 * $space-base);
  @include bp(seed) {
    height: 100%;
    min-height: 650px;
 }}
</style>
