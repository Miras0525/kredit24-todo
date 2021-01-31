<template>
  <div id="app" class="container">
    <CompletedTodos v-if="completedTasks.length"></CompletedTodos>
    <GetTodo></GetTodo>
    <CurrentTodos></CurrentTodos>
  </div>
</template>

<script>
  import GetTodo from './components/GetTodo.vue'
  import CurrentTodos from './components/CurrentTodos.vue'
  import CompletedTodos from './components/CompletedTodos.vue'

  export default {
    components: {
      GetTodo,
      CurrentTodos,
      CompletedTodos
    },
    computed: {
      completedTasks(){
        return this.$store.getters.completedTodos
      }
    }
  }
</script>

<style lang="scss">
  body {
    font-family: Helvetica, sans-serif;
  }

  .ct--lists {
    margin: 0;
    padding: 0;
  }

  .ct--list {
    list-style: none;
    display: flex;
    align-items: center;
    box-shadow: 0px 1px 4px rgba(0, 0, 0, 0.01), 0px 4px 8px rgba(0, 0, 0, 0.02), 0px 1px 12px rgba(0, 0, 0, 0.12);
    background: #fff;
    border-radius: 4px;
    padding: 8px 14px;
    margin-bottom: 12px;

    &:last-child {
      margin-bottom: 0;
    }

    &-title {
      flex-grow: 1;
    }
  }

  .ct--buttons {
    & button {
      margin: 4px 0;
    }
  }
</style>