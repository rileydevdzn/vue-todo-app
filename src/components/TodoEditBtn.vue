<template class="edit-btn-template">
  <div v-if="!isEditing">
      <button 
        type="button"
        @click="toggleTodoEditBtnForm"
        class="edit-btn">
        <img src="src/assets/edit-icon.svg" alt="" class="edit-icon"/>
        Edit
      </button>
    </div>
    <TodoEditBtnForm
      v-else
      :id="id"
      :label="label"
      @item-edited="itemEdited"
      @edit-cancelled="cancelEditToDo">
    </TodoEditBtnForm>
</template>


<script>
  import TodoEditBtnForm from './TodoEditBtnForm.vue';
  
  export default {
    components: {
      TodoEditBtnForm,
    } ,
    data() {
      return {
        isEditing: false,
      }; 
    },
    methods: {
      toggleTodoEditBtnForm() {
        this.isEditing = true;
      },
      cancelEditToDo() {
        this.isEditing = false;
      },
      itemEdited(newLabel) {
        this.$emit('item-edited', newLabel);
        this.isEditing = false;
      },
    },
  }
</script>


<style lang="scss" scoped>
  .edit-btn {
    all: unset;
    width: 90%;
    height: 100%;
    margin: 0 auto;
    padding-right: calc(1.5 * $space-base);
    background: transparent;
    font-size: $progress-font-sz;
    color: $primary-dk-blue;
    border: $border-radius10;
    @include placement(flex, column, flex-end, center);
    row-gap: calc(0.25 * $space-base);
    cursor: pointer;
    opacity: 0.7;
  }
  .edit-icon {
    padding-right: 3px;
  }
</style>