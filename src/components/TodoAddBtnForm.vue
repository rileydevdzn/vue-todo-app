<template>
  <form @submit.prevent="onSubmit">
    <div class="addtask-form-input">
      <label for="new-todo-input">New Task</label>
      <input
        type="text"
        id="new-todo-input"
        name="new-todo"
        autocomplete="off"
        maxLength="25"
        v-model.lazy.trim="label"
      />
    </div>
    <div class="addtask-form-btn-group">
      <button type="button" @click="onCancel" class="btn add-task-cancel">
        Cancel
        <span class="sr-only">new task</span>
      </button>
      <button type="submit" class="btn add-task-save">
        Save
        <span class="sr-only">and add to task list</span>
      </button>
    </div>
  </form>
</template>

<script>
export default {
  methods: {
    onSubmit() {
      if (this.label === "") {
        return;
      }
      this.$emit("todo-added", this.label);
      this.label = "";
    },
    onCancel() {
      this.$emit("add-cancelled");
    },
  },
  data() {
    return {
      label: "",
    };
  },
};
</script>

<style lang="scss" scoped>
form {
  width: 90%;
  border-radius: $border-radius10;
  background: $todo-item-bg;
  margin: $space-base auto 0 auto;
  padding-top: 1rem;
  @include box-shadow;
  @include placement(flex, column);
}
.addtask-form-input {
  width: inherit;
  padding: 0 calc(1.25 * $space-base);
  @include placement(flex, column, flex-start, center);
  label {
    font-weight: $font-wt-med;
    font-size: $form-font-sz;
    margin-left: calc(-1.75 * $space-base);
  }
  input {
    width: 100%;
    height: 40px;
    border: none;
    border-bottom: 2px solid $accent-orange;
    font-size: $font-sz-base;
    padding-left: calc(0.5 * $space-base);
  }
}
.addtask-form-btn-group {
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
.btn.add-task-save {
  @include button-colors($mt-button: false);
}
.btn.add-task-cancel {
  @include button-colors($mt-button: true);
}
</style>
