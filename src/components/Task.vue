<template>
  <div class="task">
    <p
      class="task-title"
      :class="{ 'completed': task.completed }"
      @click="markCompleted"
    >{{ task.title }}</p>
    <button class="task-delete" @click="$emit('delete-task', task.id)">Delete</button>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: ["task"],
  methods: {
    markCompleted() {
      this.task.completed = !this.task.completed;
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