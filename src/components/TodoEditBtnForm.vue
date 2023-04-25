<template>
  <form @submit.prevent="onSubmit">
    <div class="edittask-form-input">
      <label class="edit-label">Edit task</label>
      <input 
        type="text"
        :id="id"
        name="edit-todo"
        autocomplete="off"
        maxLength="25"
        v-model.lazy.trim="newLabel" />
    </div>
    <button
      type="button"
      @click="deleteToDo"
      class="delete-btn">
      <img src="src/assets/trash-icon.svg" alt="" class="delete-icon"/>
      Delete
      <span class="sr-only">task</span>
    </button>
    <div class="edittask-form-btn-group">
      <button
        type="button"
        @click="onCancel"
        class="btn edit-task-cancel">
        Cancel
        <span class="sr-only">editing task</span>
      </button>
      <button
        type="submit"
        class="btn edit-task-save">
        Save Changes
        <span class="sr-only">to task</span>
      </button>
    </div>
  </form>
</template>


<script>
  export default {
    props: {
      label: { required: true, type: String },
      id: { required: true, type: String },
    },
    data() {
      return {
        newLabel: this.label,
      };
    },
    methods: {
      onSubmit() {
        if (this.newLabel && this.newLabel !== this.label) {
          this.$emit('item-edited', this.newLabel);
        }
      },
      onCancel() {
        this.$emit('edit-cancelled');
      },
      deleteToDo() {
        this.$emit('item-deleted');
      },
    },
  }
</script>


<style lang="scss" scoped>
  form {
    width: 90%;
    border-radius: $border-radius10;
    background: $todo-item-bg;
    margin: $space-base auto 0 auto;
    padding-top: 1rem;
    @include box-shadow;
    @include position(relative);
  }
  .delete-btn {
    all: unset;
    @include placement(flex, column);
    row-gap: calc(0.5 * $space-base);
    @include position(absolute, $top: calc(1.5 * $space-base), $right: $space-base);
    font-size: $action-font-sz;
    color: $delete-btn-color;
    cursor: pointer;
  }
  .edittask-form-input {
    width: inherit;
    padding: 0 calc(1.25 * $space-base);
    @include placement(flex, column, flex-start, center);
    label {
      font-weight: $font-wt-med;
      font-size: $form-font-sz;
      margin: 0 0 calc(0.5 * $space-base) calc(-1.75 * $space-base);
    }   
    input {
      width: 85%;
      height: 40px;
      border: none;
      border-bottom: 2px solid $accent-orange;
      font-size: $font-sz-base;
      padding-left: calc(0.5 * $space-base);
    }
  }
  .edittask-form-btn-group {
    width: 100%;
    border: 0.5px solid $form-btn-border;
    border-bottom-left-radius: $border-radius10;
    border-bottom-right-radius: $border-radius10;
    margin-top: calc(1.5 * $space-base);
    @include placement(flex);
    .btn {
      all: unset;
      width: 50%;
      height: 44px;
      font-weight: $font-wt-med;
      font-size: $form-font-sz;
      text-align: center;
      cursor: pointer;
    }
  }
  .btn.edit-task-save {
    @include button-colors($mt-button: false);
  }
  .btn.edit-task-cancel {
    @include button-colors($mt-button: true);
  }

</style>