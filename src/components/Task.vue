<template>
  <div class="task">
    <p
      class="task-title"
      :class="{ 'completed': task.completed }"
      @click="markCompletedTask"
    >{{ task.title }}</p>
    <button class="task-delete" @click="deleteTask">Delete</button>
  </div>
</template>

<script>
export default {
  name: "app-task",
  props: ["task"],
  methods: {
    markCompletedTask() {
      this.task.completed = !this.task.completed;
    },
    deleteTask() {
      this.$emit("delete-task", this.task.id);
    },
  },
};
</script>

<style scoped>
.task {
  display: flex;
  flex-direction: row;
}
.completed {
  text-decoration: line-through;
  color: red;
}
.task-title {
  margin-left: 40%;
}
.task-title:hover {
  cursor: pointer;
}
.task-delete {
  margin: auto;
  margin-left: 20px;
}
</style>