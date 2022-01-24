<template>
  <div>
    <button class="task-bar__button" @click="onAdd">
      <font-awesome-icon :icon="['fa', 'plus']" />
    </button>
    <div class="task-bar" v-if="showBar">
      <button class="task-bar__button task-bar__button--close" @click="closeAdd">
        <font-awesome-icon :icon="['fa', 'long-arrow-alt-left']" />
      </button>
      <input
        type="text"
        class="task-bar__input"
        id="myInput"
        placeholder="Enter task..."
        v-model="task"
        @keypress="onWrittenEnter"
      />
      <button class="task-bar__submit" @click="onWritten">Submit</button>
    </div>
  </div>
</template>

<script>
import { library } from "@fortawesome/fontawesome-svg-core";
import { faPlus } from "@fortawesome/free-solid-svg-icons";
import { faLongArrowAltLeft } from "@fortawesome/free-solid-svg-icons";

library.add(faPlus);
library.add(faLongArrowAltLeft);
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
    closeAdd() {
      this.showBar = false;
    },
    onWritten() {
      this.$emit("onWritten", this.task);
      this.showBar = false;
    },
    onWrittenEnter(e) {
      if (e.key == "Enter") {
        this.$emit("onWrittenEnter", this.task);
        this.showBar = false;
      }
    },
  },
};
</script>

<style lang="css">
.task-bar {
  align-items: center;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  height: 100vh;
  justify-content: center;
  left: 0%;
  position: absolute;
  top: 0%;
  width: 100vw;
}

.task-bar__input {
  appearance: none;
  background: none;
  background-color: rgba(255, 255, 255, 0.5);
  border: none;
  border-radius: 0 16px 0 16px;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.25);
  color: #313131;
  display: block;
  font-size: 20px;
  outline: none;
  padding: 15px;
  transition: 0.4s;
  width: 50%;
}

.task-bar__input:focus {
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 16px 0 16px 0;
  box-shadow: 0 0 16px rgba(0, 0, 0, 0.25);
}

.task-bar__submit {
  color: white;
  background: blueviolet;
  border-radius: 16px;
  font-size: 20px;
  margin-left: 10px;
  padding: 15px 25px;
}

.task-bar__button {
  background: none;
}

.task-bar__button--close svg {
    background-color: blueviolet !important;
}
</style>
