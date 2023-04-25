<template>
  <header>
    <div>
      <h2>Today</h2>
      <p class="todays-date">{{ displayTodayDate }}</p>
    </div>
    <div class="progress-tracking">
      <div class="progress-visual">
        <div class="progress-bar-track"></div>
        <div class="progress-bar" :style="{ width: displayProgressBar }"></div>
        <p class="progress-percent">{{ displayProgressPercent }}%</p>
      </div>
      <div class="progress-text">
        <p>Completed</p>
        <p>{{ displayProgressSummary }}</p>
      </div>
    </div>
  </header>
  <section class="todo-list-section">
    <FilterBtns
      @filterChange="current = $event"
      :current="current"
      class="home-filter-btns"></FilterBtns>
    <ul class="home-todo-list">
      <li v-for="item in filterTodos" :key="item.id">
        <TodoItem 
            :label="item.label"
            :done="item.done"
            :id="item.id"
            @checkbox-changed="updateDoneStatus(item.id)"
            @item-edited="editToDo(item.id, $event)"
            @item-deleted="deleteToDo(item.id)">
        </TodoItem>
      </li>
    </ul>
    <TodoAddBtn
        @todo-added="addToDo"
        class="home-addtodo-btn">
    </TodoAddBtn>
  </section>
</template>


<script>
  import FilterBtns from '../components/FilterBtns.vue';
  import TodoItem from '../components/TodoItem.vue';
  import TodoAddBtn from '../components/TodoAddBtn.vue';
  import uniqueId from "lodash.uniqueid";

  export default {
    components: {
      FilterBtns,
      TodoItem,
      TodoAddBtn,
    },
    data() {
      return {
        ToDoItems: [
          { id: uniqueId("todo-"), label: "Get groceries", done: false },
          { id: uniqueId("todo-"), label: "Water plants", done: false },
        ],
        current: 'all'
      };
    },
    methods: {
      addToDo(toDoLabel) {
        this.ToDoItems.push({id:uniqueId('todo-'), label: toDoLabel, done: false})
      },
      updateDoneStatus(toDoId) {
        const toDoToUpdate = this.ToDoItems.find((item) => item.id === toDoId)
        toDoToUpdate.done = !toDoToUpdate.done
      },
      editToDo(toDoId, newLabel) {
        const toDoToEdit = this.ToDoItems.find((item) => item.id === toDoId);
        toDoToEdit.label = newLabel;
      },
      deleteToDo(toDoId) {
        const itemIndex = this.ToDoItems.findIndex((item) => item.id === toDoId);
        this.ToDoItems.splice(itemIndex, 1);
      },
    },
    computed: {
      filterTodos() {
        if(this.current === 'completed') {
          return this.ToDoItems.filter((item) => item.done);
        }
        if(this.current === 'active') {
          return this.ToDoItems.filter((item) => !item.done);
        }
        return this.ToDoItems;
      },
      displayProgressSummary() {
        const numCompletedItems = this.ToDoItems.filter((item) => item.done).length;
        return `${numCompletedItems} / ${this.ToDoItems.length}`;
      },
      displayProgressPercent() {
        const numCompletedItems = this.ToDoItems.filter((item) => item.done).length;
        const percentProgress = Math.floor((`${numCompletedItems}` / `${this.ToDoItems.length}`) * 100);
        return `${percentProgress}`; 
      },
      displayProgressBar() {
        const numCompletedItems = this.ToDoItems.filter((item) => item.done).length;
        const percentProgress = Math.floor((`${numCompletedItems}` / `${this.ToDoItems.length}`) * 100);
        function formatAsPercent(num) {
          return new Intl.NumberFormat('default', {
            style: 'percent',
            minimumFractionDigits: 0,
            maximumFractionDigits: 0,
          }).format(num / 100);
        }
        return formatAsPercent(`${percentProgress}`);
      },
      displayTodayDate() {
        const date = new Date();
        const options = { year: 'numeric', month: 'long', day: 'numeric'};
        return `${date.toLocaleDateString('en-GB', options)}`;
      }
    },
  }
</script>


<style lang="scss" scoped>
  header {
    width: 100%;
    height: 174px;
    padding: calc(1.5 * $space-base);
    background: $primary-dk-blue; 
    color: $header-wht90;
    @include placement(flex, column, flex-start, space-between);
    
  }
  h2 {
    font-weight: $font-wt-med;
    font-size: $h2-font-sz;
    margin-bottom: calc(0.75 * $space-base);
  }
  .todays-date {
    font-weight: $font-wt-light;
    color: $header-wht80;
  }
  .home-todo-list {
    width: 100%;
    list-style: none;
    li {
      margin-bottom: calc(1.5 * $space-base);
    }
  }
  .progress-tracking {
    width: 100%;
    @include position(relative);
  }
  .progress-visual {
    width: inherit;
  }
  .progress-bar-track {
    width: inherit;
    height: 6px;
    border-radius: 3px;
    background: $header-wht80;
    opacity: 0.3;
  }
  .progress-bar {
    height: 6px;
    border-radius: 3px;
    background: $header-wht90;
    @include position(absolute, $top: 0, $left: 0);
  }
  .progress-percent {
    font-size: $action-font-sz;
    @include position(absolute, $top: calc(-1.3 * $space-base), $left: 0);
  }
  .progress-text {
    font-size: $progress-font-sz;
    @include placement(flex, column);
    row-gap: calc(0.5 * $space-base);
    @include position(absolute, $top: calc(-4 * $space-base), $right: 0);
  }

  .todo-list-section {
    width: 100%;
    min-height: 204px;
    @include placement(flex, column, center, space-between)
  }
  .home-filter-btns {
    width: 100%;
  }
  .home-addtodo-btn {
    width: 90%;
  }
</style>