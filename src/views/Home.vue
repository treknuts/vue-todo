<template>
  <div class="home">
    <h3>Shit fuck TODO list</h3>
    <h3>Not Started</h3>    
    <div class="todo-bucket">
    <draggable v-model="notStarted" group="people" @start="drag=true" @end="drag=false">
          <TodoItem v-for="todoItem in notStarted" v-bind:key="todoItem.id" v-bind:todo="todoItem" />
    </draggable>
    </div>
    <div class="todo-bucket">
      <h3>In Progress</h3>
      <div>
      <draggable v-model="inProgress" group="people" @start="drag=true" @end="drag=false">
          <TodoItem v-for="todoItem in inProgress" v-bind:key="todoItem.id" v-bind:todo="todoItem" />
      </draggable>
    </div>
      <h3>Done xD</h3>
      <div class="todo-bucket">
      <draggable v-model="done" group="people" @start="drag=true" @end="drag=false">
          <TodoItem v-for="todoItem in done" v-bind:key="todoItem.id" v-bind:todo="todoItem" />
      </draggable>
      </div>
  </div>
  </div>
</template>

<script>
// @ is an alias to /src
import TodoItem from "@/components/TodoItem.vue";
import draggable from "vuedraggable";

export default {
  name: "Home",
  // data function should likely make API calls for data
  data: function() {
    return {
      notStarted: [{ id: 2, title: "Build cool apps", priority: "Medium" }],
      inProgress: [{ id: 1, title: "Learn Vue", priority: "High" }],
      done: [{ id: 3, title: "Win in Fall Guys", priority: "Low" }]
    };
  },
  components: {
    TodoItem,
    draggable
  },
  methods: {
    debug() {
      console.log(this.todoList);
    }
  }
};
</script>
<style scoped>
.todo-bucket {
  margin: 10px;
  border-style: solid;
  border-width: 2px;
  min-height: 100px;
}
</style>
