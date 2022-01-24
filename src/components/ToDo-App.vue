<template>
  <div>
    <date @onAddTask="addTaskArray"></date>
    <list :newTaskArray="taskArray"></list>
  </div>
</template>

<script>
import List from "./Body/List.vue";
import Date from "./Header/Date.vue";

export default {
  components: { List, Date },
  name: "toDoApp",
  data() {
    return {
      task: "",
      taskArray: [],
    };
  },
  methods: {
    addTaskArray(data) {
      this.task = data;
      this.taskArray.push({
        task: this.task,
        status: "To-do",
      });
    },
  },
};
</script>

<style lang="css"></style>
