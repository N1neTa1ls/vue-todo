<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox"
      v-on:change="todo.completed = !todo.completed"
      >
      <strong>{{index + 1}}</strong>
      {{todo.title}}
    </span>
    <button class="del"
    v-on:click="$emit('remove-todo', todo.id)"
    >&times;</button>
  </li>
</template>

<script>

export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  }
}
</script>

<style scoped>
li {
  border: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  padding: .5rem 2rem;
  margin-bottom: 1rem;
}
input {
  margin-right: 1rem;
}
.del {
  color: #fff;
  background: rgb(189, 22, 22);
  border-radius: 50px;
  font-weight: bold;
}
.done {
  text-decoration: line-through;
}
</style>