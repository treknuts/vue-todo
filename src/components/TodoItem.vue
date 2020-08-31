<template>
  <li>{{ todo.name }}</li>
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