<template>
  <div>
    <form @submit="addTask">
      <input type="text" v-model="title" name="title" />
      <button type="submit">Add</button>
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from "uuid";

export default {
  name: "AddTask",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTask(event) {
      event.preventDefault();
      const createdTask = {
        id: uuidv4(),
        title: this.title,
        completed: false,
      };
      this.$emit("add-task", createdTask);
      this.title = "";
    },
  },
};
</script>
<style scoped>
</style>