<template>
  <div class="header">
    <div class="header-date">
      <h1 class="header-date__title">My Day</h1>
      <p class="header-date__day">{{ currentDateTime() }}</p>
    </div>
    <div class="header-add-task">
      <button><font-awesome-icon :icon="['fa', 'plus']" /></button>
    </div>
  </div>
</template>

<script>
import moment from "moment";
import { library } from "@fortawesome/fontawesome-svg-core";
import { faPlus } from "@fortawesome/free-solid-svg-icons";

library.add(faPlus);

export default {
  name: "date",
  methods: {
    currentDateTime() {
      return moment().format("MMMM Do YYYY");
    },
  },
};
</script>

<style lang="css">
.header {
  background: rgb(168, 28, 214);
  background: linear-gradient(
    90deg,
    rgba(168, 28, 214, 1) 6%,
    rgba(97, 20, 172, 1) 63%,
    rgba(66, 66, 187, 1) 100%
  );
  color: white;
  display: flex;
  flex-direction: row;
  height: auto;
  justify-content: space-between;
}
.header-date {
  margin: 0;
  padding: 10% 0 10px 50px;
  text-align: left;
}

.header-date__title {
  font-size: 50px;
  margin: 0;
}

.header-date__day {
  margin: 0;
}

.header-add-task {
  padding: 12% 50px 10px 0;
}

.header-add-task svg {
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 50%;
  box-shadow: 1px 1px rgba(41, 40, 40, 0.25);
  color: white;
  padding: 20px;
}

.header-add-task button {
    cursor: pointer;
    background: none;
    border: none;
    outline: none;
}
</style>
