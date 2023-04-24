<template>
  <div class="filter-btn-group">
    <button @click="updateFilter('all')" :class="{active: current === 'all'}">All</button>
    <button @click="updateFilter('completed')" :class="{active: current === 'completed'}">Completed</button>
    <button @click="updateFilter('active')" :class="{active: current === 'active'}">Active</button>
  </div>
</template>

<script>
  export default {
    props: 
      ['current'],
    methods: {
      updateFilter(by) {
        this.$emit('filterChange', by)
      },
    },
  }
</script>

<style lang="scss" scoped>
  button {
    all: unset;
    width: 80px;
    margin: calc(0.75 * $space-base) calc(0.5 * $space-base) $space-base calc(0.5 * $space-base);
    padding-bottom: calc(0.5 * $space-base);
    font-size: $action-font-sz;
    color: $filter-btn-inactive;
    text-align: center;
    border-bottom: 2px solid transparent;
    cursor: pointer;
    &.active {
      font-weight: $font-wt-bold;
      color: $body-txt-active;
      border-bottom: 2px solid $accent-lt-blue;
    }
  }
  
</style>