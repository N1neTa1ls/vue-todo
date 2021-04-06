<template>
  <div>
    <!-- <h1>Todo application</h1> -->   
    <AddTask 
      @add-task="addNewTask"
    />
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not completed</option>
    </select>
    <hr>
    <TodoList
    v-if="filteredTodos.length"
    v-bind:todos = "filteredTodos"
    @removeTask="removeTask"
     />
     <p v-else>Нет текущих задач</p>
    <router-link to="/">Открыть Home page</router-link>
  </div>
</template>

<script>
import TodoList from '@/components/todo-list'
import AddTask from '@/components/addTask'
export default {
  name: 'App',
  data() {
    return {
      todos: [
        {id:1, title: 'купить хлеб', completed: false},
        {id:2, title: 'купить масло', completed: false},
        {id:3, title: 'купить фантазию', completed: false}
      ],
      filter: 'all'
    }
  },
  methods: {
    removeTask(id) {
      this.todos = this.todos.filter(t => t.id !== id);
    },
    addNewTask(todo) {
      this.todos.push(todo);
    }
  },
  computed: {
  filteredTodos() {
    if (this.filter==='all') {
      return this.todos
    }
    if (this.filter==='completed') {
      return this.todos.filter(t=> t.completed)
    }
    if (this.filter==='not-completed') {
      return this.todos.filter(t=> !t.completed)
    }
  }
},
  components: {
    TodoList,
    AddTask
  }
}
</script>

<style scoped>
select {
  margin-top: 10px;
}
</style>