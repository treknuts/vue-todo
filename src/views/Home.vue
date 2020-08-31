<template>
  <div class="home">
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
            { id: 1, title: "Learn Vue", priority: "High" },
            { id: 2, title: "Build cool apps", priority: "Medium"},
            { id: 3, title: "Get wins in Fall Guys", priority: "Low" }
        ]
        }
  },
  components: {
    TodoItem
  }
};
</script>
