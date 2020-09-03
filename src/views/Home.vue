<template>
  <div class="home">
    <h3>Shit fuck TODO list</h3>
    <div class="not-started">
      <ul>
        <draggable v-model="notStarted">
          <TodoItem
            v-for="todoItem in notStarted"
            v-bind:key="todoItem.id"
            v-bind:todo="todoItem"
          />
        </draggable>
      </ul>
    </div>
    <div class="todo-buckets">
      <div class="in-progress">
        <ul>
          <draggable v-model="inProgress">
            <TodoItem
              v-for="todoItem in inProgress"
              v-bind:key="todoItem.id"
              v-bind:todo="todoItem"
            />
          </draggable>
        </ul>
      </div>
      <div class="done">
        <ul>
          <draggable v-model="done">
            <TodoItem
              v-for="todoItem in done"
              v-bind:key="todoItem.id"
              v-bind:todo="todoItem"
            >
            </TodoItem>
          </draggable>
        </ul>
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
      done: [{ id: 3, title: "Win in Fall Guys", priority: "Low" }],
    };
  },
  components: {
    TodoItem,
    draggable,
  },
  methods: {
    debug() {
      console.log(this.todoList);
    },
  },
};
</script>
<style scoped>
.todo-buckets {
  display: flex;
  flex-flow: row nowrap;
}
</style>
