<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <h3>Shit fuck TODO list</h3>
    <ul>
      <TodoItem v-for="todoItem in todoList"
        v-bind:key="todoItem.id"
        v-bind:todo="todoItem">
      </TodoItem>
    </ul>
  </div>
</template>

<script>
// @ is an alias to /src
import TodoItem from "@/components/TodoItem.vue";

export default {
  name: "Home",
  // data function should likely make API calls for data
  data: function () {
        return {
          todoList: [
            { id: 1, name: "Learn Vue" },
            { id: 2, name: "Build cool apps" },
            { id: 3, name: "Get wins in Fall Guys" }
        ]
        }
  },
  components: {
    TodoItem
  }
};
</script>
