<template>
  <div v-if="!isAdding">
    <button type="button" @click="toggleTodoAddBtnForm" class="add-btn">
      Add New Task
    </button>
  </div>
  <TodoAddBtnForm v-else @todo-added="itemAdded" @add-cancelled="cancelAddToDo">
  </TodoAddBtnForm>
</template>

<script>
import TodoAddBtnForm from "./TodoAddBtnForm.vue";

export default {
  components: {
    TodoAddBtnForm,
  },
  data() {
    return {
      isAdding: false,
    };
  },
  methods: {
    toggleTodoAddBtnForm() {
      this.isAdding = true;
    },
    cancelAddToDo() {
      this.isAdding = false;
    },
    itemAdded() {
      this.isAdding = false;
    },
  },
};
</script>

<style lang="scss" scoped>
.add-btn {
  all: unset;
  display: block;
  width: 100%;
  height: 54px;
  border-radius: 10px;
  margin: 0 auto;
  background-color: $accent-orange;
  @include box-shadow;
  font-weight: $font-wt-med;
  color: $primary-wht;
  text-align: center;
  text-transform: uppercase;
  cursor: pointer;
}
</style>
