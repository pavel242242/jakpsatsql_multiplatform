<template>
  <div id="app">
    <h1>Todos</h1>
    <ul>
      <li v-for="todo of todos" :key="todo.id">
        {{todo.name}}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'app',
  data() {
    return {
      todos: []
    }
  },
  async created() {
    try {
      const res = await axios.get(`https://8080-ae824467-344c-46b2-8adf-c18a6d5f27c9.ws-eu01.gitpod.io/todos`)

      this.todos = res.data;
    } catch(e) {
      console.error(e)
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #6c5ce7;
  margin-top: 60px;
}

li {
  list-style: none;
}

h1 {
  color: #a29bfe
}
</style>