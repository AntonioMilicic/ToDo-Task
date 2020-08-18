<template>
  <div class="search-tasks">
    <input
      type="text"
      placeholder="search..."
      v-model="searchTasksValue"
      name="search"
      @keyup="searchForTasks"
    />
  </div>
</template>

<script>
export default {
  name: "app-search-tasks",
  props: ["tasks"],
  data() {
    return {
      searchTasksValue: null,
    };
  },
  methods: {
    searchForTasks() {
      if (!this.searchTasksValue)
        return this.$emit("filtered-tasks", this.tasks);

      const filteredTasks = this.filterTasks();
      return this.$emit("filtered-tasks", filteredTasks);
    },
    filterTasks() {
      return this.tasks.filter((task) =>
        task.title.toLowerCase().includes(this.searchTasksValue.toLowerCase())
      );
    },
  },
};
</script>
<style scoped>
</style>