<template>
  <div class="home">
    <div class="toolbar">
      <b-button pill variant="primary" v-b-modal.create-todo>+</b-button>
      <b-modal id="create-todo" title="Bootstrap Vue">
        <TodoForm v-model.lazy.trim="notStarted" @todo-added="addTodo" />
      </b-modal>
    </div>
    <div class="content">
      <div class="bucket">
        <h4>Not Started</h4>
        <div class="buckets">
          <draggable
            v-model="notStarted"
            group="people"
            @start="drag = true"
            @end="drag = false"
            class="todo-bucket"
            v-on:change="debug"
          >
            <TodoItem
              v-for="todoItem in notStarted"
              v-bind:key="todoItem.id"
              v-bind:todo="todoItem"
            />
          </draggable>
        </div>
      </div>
      <div class="bucket">
        <h4>In Progress</h4>
        <draggable
          v-model="inProgress"
          group="people"
          @start="drag = true"
          @end="drag = false"
          class="todo-bucket"
          v-on:change="debug"
        >
          <TodoItem
            v-for="todoItem in inProgress"
            v-bind:key="todoItem.id"
            v-bind:todo="todoItem"
          />
        </draggable>
      </div>
      <div class="bucket">
        <h4>Done xD</h4>
        <draggable
          v-model="done"
          group="people"
          @start="drag = true"
          @end="drag = false"
          class="todo-bucket"
          v-on:change="debug"
        >
          <TodoItem
            v-for="todoItem in done"
            v-bind:key="todoItem.id"
            v-bind:todo="todoItem"
          />
        </draggable>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import TodoItem from "@/components/TodoItem.vue";
import TodoForm from "@/components/TodoForm.vue";
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
    TodoForm,
    draggable,
  },
  methods: {
    addTodo(todoForm) {
      this.notStarted.push(todoForm);
      console.log("todo added", todoForm);
    },
    debug() {
      console.log(this.inProgress);
      console.log(this.notStarted);
      console.log(this.done);
    },
  },
};
</script>
<style scoped>
.content {
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-around;
}
.toolbar {
  display: flex;
  flex-flow: row nowrap;
  justify-content: flex-end;
  padding-right: 20px;
}
.bucket {
  margin: 20px;
  display: flex;
  flex-flow: column nowrap;
  justify-content: center;
}
.todo-bucket {
  border-style: solid;
  border-width: 1px;
  border-color: gray;
  border-radius: 5px;
  margin: 10px;
  min-height: 100px;
  max-width: 250px;
  min-width: 100px;
}
</style>
