<template>
  <div class="tasks">
    <ul style="listStyle: none;">
      <li :key="task.id" v-for="task in tasks">
        <app-task :task="task" @delete-task="$emit('delete-task', task.id)" />
      </li>
    </ul>
  </div>
</template>
<script>
import AppTask from "./Task";

export default {
  name: "app-tasks",
  components: {
    AppTask,
  },
  props: ["tasks"],
};
</script>
<style scoped>
</style>