<template>
  <div class="manager-wrapper">
    <Tasks :tasks="tasks" @delete-task="deleteTask" />
    <hr style="width:30%" />
    <AddTask @add-task="addTask" />
    <button class="delete-checked-button" @click="deleteChecked">Delete Checked</button>
  </div>
</template>

<script>
import Tasks from "../components/Tasks";
import AddTask from "../components/AddTask";

export default {
  name: "TaskManager",
  components: {
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [
        {
          id: 1,
          title: "To Do",
          completed: false,
        },
        {
          id: 2,
          title: "To Do",
          completed: false,
        },
        {
          id: 3,
          title: "To Do To Do To Do",
          completed: false,
        },
        {
          id: 4,
          title: "To Dooooo",
          completed: false,
        },
        {
          id: 5,
          title: "Tooo Dooo Dooo Dooo",
          completed: false,
        },
      ],
    };
  },
  methods: {
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask];
    },
    deleteTask(taskId) {
      this.tasks = this.tasks.filter((task) => task.id !== taskId);
    },
    deleteChecked() {
      this.tasks = this.tasks.filter((task) => task.completed === false);
    },
  },
};
</script>

<style scoped>
.delete-checked-button {
  margin-top: 16px;
}
</style>