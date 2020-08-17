<template>
  <div>
    <h2>My To Do To Dooo:</h2>
    <ul style="listStyle:none">
      <li :key="task.id" v-for="task in tasks">
        <Task :task="task" @delete-task="$emit('delete-task', task.id)" />
      </li>
    </ul>
  </div>
</template>
<script>
import Task from "./Task";

export default {
  name: "Tasks",
  components: {
    Task,
  },
  props: ["tasks"],
};
</script>
<style scoped>
</style>