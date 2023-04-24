<template>
  <div class="todo-item">
    <input
      type="checkbox"
      :id="id"
      :checked="isDone"
      @change="$emit('checkbox-changed')" />
    <label :for="id">{{label}}</label>
    <div class="todo-item-bg"></div>
    <div class="edit-btn-placeholder"></div>
  </div>
</template>

<script>
  

  export default {
    props: {
      label: { required: true, type: String },
      done: { default: false, type: Boolean },
      id: { required: true, type: String },
    },
    data() {
      return {
        isDone: this.done,
      }; 
    },
  }
</script>

<style lang="scss">
.todo-item {
  width: 90%;
  height: 60px;
  border-radius: $border-radius10;
  margin: 0 auto;
  
  @include placement(flex, row, center, flex-start);
  @include position(relative);
}
label {
  margin-left: calc(2 * $space-base);
  z-index: 4;
  cursor: pointer;
}
.todo-item-bg {
  width: 100%;
  height: 100%;
  border-radius: $border-radius10;
  background: linear-gradient(to right, $primary-dk-blue, $primary-dk-blue 18%, $todo-item-bg 18%, $todo-item-bg);
  @include box-shadow;
  @include position(absolute, $top: 0, $left: 0);
  z-index: 2;
  @include transition(background-color);
}
input[type="checkbox"] {
  appearance: none;
  background-color: #fff;
  margin: 0;
  width: calc(1.25 * $space-base);
  height: calc(1.25 * $space-base);
  border: 1.5px solid $accent-orange;
  border-radius: 50%;
  margin-left: Calc(1.25 * $space-base);
  display: grid;
  place-content: center;
  z-index: 4;
  cursor: pointer;
}
input[type="checkbox"]:checked {
  border: 1.5px solid $primary-dk-blue;
  + label {
    color: $body-txt-completed;
    text-decoration: line-through;
  }
  ~ .todo-item-bg {
    background: $todo-item-bg-completed;
    box-shadow: none;
  }
}
input[type="checkbox"]::before {
  content: url(../assets/checkmark-icon.svg);
  width: calc(0.65 * $space-base);
  height: calc(0.65 * $space-base);
  @include placement(flex);
  border-radius: 50%;
  transform: scale(0);
  @include transition(transform, $dur: 0.15s);
  box-shadow: inset 0 0 0 calc(1.25 * $space-base) $primary-dk-blue;
}
input[type="checkbox"]:checked::before {
  transform: scale(1.75);
}

</style>