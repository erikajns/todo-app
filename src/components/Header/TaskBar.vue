<template>
  <div>
    <button @click="onAdd">
      <font-awesome-icon :icon="['fa', 'plus']" />
    </button>
    <div class="task-bar" v-if="showBar">
      <input
        type="text"
        class="task-bar__input"
        placeholder="Enter task..."
        v-model="task"
      />
      <button @click="onWritten">Submit</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "taskBar",
  data() {
    return {
      showBar: false,
      task: "",
    };
  },
  methods: {
    onAdd() {
      this.showBar = true;
    },
    onWritten(){
        this.$emit("onWritten", this.task);
        this.showBar = false;
    }
  },
};
</script>

<style lang="css"></style>
