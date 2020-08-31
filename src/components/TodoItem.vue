<template>
  <b-card no-body>
    <b-card-body>
      <h4>{{ todo.title }}</h4>
      <b-badge v-if="todo.priority == 'High'" variant="danger">{{ todo.priority }}</b-badge>
      <b-badge v-else-if="todo.priority == 'Medium'" variant="warning">{{ todo.priority }}</b-badge>
      <b-badge v-else variant="primary">{{ todo.priority }}</b-badge>
      <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
    </b-card-body>
  </b-card>
</template>

<script>
export default {
    name: "TodoItem",
    props: ['todo']
}
</script>

<style>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>