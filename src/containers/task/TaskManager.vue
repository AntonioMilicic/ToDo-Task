<template>
  <div class="task-manager">
    <h2>My To Do To Dooo:</h2>
    <app-search-tasks :tasks="tasks" @filtered-tasks="filterTasks" />
    <app-tasks :tasks="filteredTasks" @delete-task="deleteTask" />
    <hr style="width:30%" />
    <app-add-task @add-task="addTask" />
    <button
      class="delete-checked-button"
      @click="deleteChecked"
      :disabled="shouldShowDelete()"
    >Delete Checked</button>
  </div>
</template>

<script>
import AppTasks from "../../components/task/Tasks";
import AppAddTask from "../../components/task/TaskAdd";
import AppSearchTasks from "../../components/task/TasksSearch";

export default {
  name: "app-task-manager",
  components: {
    AppTasks,
    AppAddTask,
    AppSearchTasks,
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
      filteredTasks: null,
      searchTasksValue: null,
    };
  },

  methods: {
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask];
      this.filteredTasks = this.tasks;
    },
    deleteTask(taskId) {
      this.tasks = this.deleteFilterHelper(taskId);
      this.filteredTasks = this.tasks;
    },
    deleteFilterHelper(taskId) {
      return this.tasks.filter((task) => task.id !== taskId);
    },
    deleteChecked() {
      const filterDeleted = this.deleteHelper();
      this.tasks = filterDeleted;
      this.filteredTasks = this.tasks;
    },
    deleteHelper() {
      return this.tasks.filter((task) => task.completed === false);
    },
    filterTasks(filteredTasks) {
      this.filteredTasks = filteredTasks;
    },
    shouldShowDelete() {
      const filteredTasks = this.deleteHelper();
      return this.tasks.length === filteredTasks.length;
    },
  },

  created() {
    this.filteredTasks = this.tasks;
  },
};
</script>

<style scoped>
.delete-checked-button {
  margin-top: 16px;
}
</style>