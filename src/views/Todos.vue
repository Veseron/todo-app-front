<template>
  <div class="about">
    <h1>This is an Todos page</h1>
    <AddTodo
      @add-todo="addTodo"
    />
    <div>
      <select v-model="filter">
        <option value="all">All</option>
        <option value="completed">Completed</option>
        <option value="not-completed">Not completed</option>
      </select>
    </div>
    <h2>Todo List on <date :date="Date.now()"/></h2>
    <Loader
      v-if="loading"
    />
    <TodoList
      v-else
      v-bind:todos="filteredTodos"
      @remove-todo="removeTodo"
      @change-status="changeStatus"
    />
    <h2 v-if="filteredTodos.length == 0 && loading == false" class="text-center" style="margin-top: 20px;">
      No todos today!
    </h2>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
import Loader from '@/components/Loader'
import Date from '@/components/simple-components/Date'

const useTestData = false

export default {
  name: 'todos-page',
  data() {
    return {
      todos: [],
      loading: true,
      filter: "all",
    }
  },
  computed: {
    filteredTodos() {
      if (this.filter === 'all') {
        return this.todos
      } 

      if (this.filter === 'completed') {
        return this.todos.filter(t => t.completed)
      }

      if (this.filter === 'not-completed') {
        return this.todos.filter(t => !t.completed)
      }
    }
  },
  mounted() {
    fetch('http://localhost:3000/todos')
      .then(response => response.json())
      .then(json => {
        setTimeout(
          () => {
            this.todos = json
            this.loading = false
          }, 500
        )
      })
  },
  components: {
    TodoList,
    AddTodo,
    Loader,
    date: Date
  },
  methods: {
    removeTodo(id) {
      fetch(`http://localhost:3000/todos/${id}`, {
        method: 'DELETE'
      })
        .then(response => response.json())
        .then(json => {
          if (json) this.todos = this.todos.filter(t => t._id != id)
        })
    },
    addTodo(todo) {
      fetch('http://localhost:3000/todos', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(todo)
      })
        .then(response => response.json())
        .then(json => {
          if (json) this.todos.push(json)     
        })
    },
    changeStatus(todo) {
      console.log(todo)
      fetch(`http://localhost:3000/todos/${todo._id}`, {
          method: 'PUT',
          body: JSON.stringify(todo),
          headers: {
            'Content-Type': 'application/json'
          }          
        })
          .then(response => response.json())
          .then(json => console.log(json))
    }
  }
}
</script>

<style scoped>

</style>