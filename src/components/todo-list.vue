<template>
  <div>
    <ul>
      <TodoItem
      v-for="(todo, i) of todos"
      :key="todo.id"
      v-bind:todo="todo"
      v-bind:index="i"
      v-on:remove-todo="removeTask"
       />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'
export default {
  props: ['todos'],
components: {
  TodoItem
  },
  methods: {
    removeTask(id) {
      this.$emit('removeTask', id);
    }
  }
}
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>