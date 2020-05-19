<template>
  <div id="app">
    <div class="todo-wrapper">
      <div class="todo-container">
        <TodoList :todos="todos"/>
        <div class="todo-create-btn-container">
           <TodoCreate @formSubmitted="createTodo"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import TodoCreate from '@/components/TodoCreate'
import store from '@/store'

export default {
  name: 'App',
  components: {
    TodoList,
    TodoCreate
  },
  data: () => ({
    todos: store.state.todos
  }),
  created() {
    this.todos = store.dispatch('initStore')
  },
  methods: {
    createTodo(todo){
      store.dispatch('createTodo', todo)
    }
  }
}
</script>

<style lang="scss">
$color-red: lightgray;

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.app-error {
  color: #ff1212;
}

.app-form {
  .label {
    display: block;
    font-size: 18px;
    font-weight: bold;
  }

  .form-input {
    padding: 10px;
    font-size: 17px;
    padding: 10px;
    font-size: 17px;
  }

  .form-control {
    margin-bottom: 10px;

    &-last {
      margin-bottom: 0;
    }
  }
}

.is-primary {
  background-color: green !important;
}

.is-warning {
  background-color: #ffa753 !important;
}

.is-danger {
  background-color: #ff5a5a !important;
}

.app-button {
  font-size: 20px;
  padding: 10px;
  border-radius: 5px;
  background-color: #795899;
  color: white;
  font-weight: bold;

  &:hover {
    cursor: pointer;
  }
}

.todo {
  &-wrapper {
    display: flex;
    justify-content: center;
    width: 100%;
  }

  &-container {
    display: flex;
    flex-direction: column;
    margin: 0 auto;
    width: 400px;
    min-height: 400px;
    background-color: $color-red;
    border-radius: 5px;
  }

  &-create-btn-container {
    margin: 10px;
  }
}
</style>
