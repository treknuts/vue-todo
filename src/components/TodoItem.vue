<template>
  <b-card no-body>
    <b-card-body>
      <h4>{{ todo.title }}</h4>
      <b-badge v-if="todo.priority == 'High'" variant="danger">{{
        todo.priority
      }}</b-badge>
      <b-badge v-else-if="todo.priority == 'Medium'" variant="warning">{{
        todo.priority
      }}</b-badge>
      <b-badge v-else variant="primary">{{ todo.priority }}</b-badge>
      <p>{{ todo.status }}</p>
      <p class="card-text">
        Some quick example text to build on the card title and make up the bulk
        of the card's content.
      </p>
    </b-card-body>
  </b-card>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
};
</script>

<style>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
  display: flex;
  flex-flow: row wrap;
  justify-content: center;
}
li {
  margin: 10px;
}
a {
  color: #42b983;
}
b-card {
  max-width: 50px;
  margin: 20px;
}
.card-text {
  max-width: 200px;
  display: flex;
  flex-flow: row wrap;
}
</style>
