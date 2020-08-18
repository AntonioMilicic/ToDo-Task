<template>
  <div class="add-task">
    <form @submit="addTask">
      <input type="text" v-model="title" name="title" />
      <button type="submit" style="margin-left:10px;" :disabled="!title">Add</button>
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from "uuid";

export default {
  name: "app-add-task",
  data() {
    return {
      title: null,
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