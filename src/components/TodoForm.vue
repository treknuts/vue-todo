<template>
  <div>
    <b-form
      @submit.prevent="onSubmit"
      @reset="onReset"
      v-if="show"
      v-bind:value="form"
    >
      <b-form-group id="input-group-1" label="Title" label-for="input-1">
        <b-form-input
          id="todo-title"
          v-model="form.title"
          required
          placeholder="e.g. Pickup groceries"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Priority" label-for="input-2">
        <b-form-select
          id="input-2"
          v-model="form.priority"
          :options="priority"
          required
        ></b-form-select>
      </b-form-group>
      <b-form-group id="input-group-3" label="Description" label-for="input-3">
        <b-form-input id="input-3" v-model="form.description"></b-form-input>
      </b-form-group>
      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
  </div>
</template>

<script>
export default {
  name: "TodoForm",
  data() {
    return {
      form: {
        title: "",
        priority: null,
      },
      priority: [{ text: "Select One", value: null }, "High", "Medium", "Low"],
      show: true,
    };
  },
  methods: {
    onSubmit() {
      this.$emit("todo-added", this.form);
    },
    onReset(evt) {
      evt.preventDefault();
      // Reset our form values
      this.form.email = "";
      this.form.name = "";
      this.form.food = null;
      this.form.checked = [];
      // Trick to reset/clear native browser form validation state
      this.show = false;
      this.$nextTick(() => {
        this.show = true;
      });
    },
  },
};
</script>
