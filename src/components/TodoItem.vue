<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input 
        type="checkbox" 
        v-on:change="todo.completed = !todo.completed"
        v-bind:checked="todo.completed"
      >
      <strong>{{ index + 1 }}</strong>
      {{ todo.title | uppercase }}
    </span>
    <button v-on:click="$emit('remove-todo', todo.id)">&times;</button>
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
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase()
    }
  }
}
</script>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>