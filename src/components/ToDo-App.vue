<template>
  <div>
    <date></date>
    <list></list>
  </div>
</template>

<script>
import List from "./Body/List.vue";
import Date from "./Header/Date.vue";

export default {
  components: { List, Date },
  name: "toDoApp",
};
</script>

<style lang="css"></style>
