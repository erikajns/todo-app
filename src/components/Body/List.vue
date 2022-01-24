<template>
  <div class="list-wrap">
    <div class="list-wrap__default-message" v-if="this.emptyArray">
      <span class="list-wrap__default-message-icon"
        ><font-awesome-icon :icon="['fa', 'exclamation']"
      /></span>
      <h1>HEY THIS IS EMPTY!</h1>
      <p>
        Hello there, your To-do List for today is empty. Click on the "+" icon
        to add a new task in your qeue.
      </p>
      <p>
        <b>Instructions: </b> Once you add a new task, to change its status
        click on the status word. There are 3 different status: To-Do (the
        default), In-Progress, and Done.
      </p>
      <p>Or when you are done, just click the check to set a task as Done</p>
    </div>
    <table v-if="!this.emptyArray">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col">Status</th>
          <th scope="col">#</th>
          <th scope="col">#</th>
        </tr>
      </thead>
      <tbody>
        <tr
          class="list-item"
          v-for="(item, index) in this.newTaskArray"
          :key="index"
        >
          <td>
            <span :class="{ finished: item.status === 'Done' }">{{
              item.task
            }}</span>
          </td>
          <td class="list-item__status" @click="changeStatus(index)">
            <span
              :class="{
                success: item.status === 'Done',
                warning: item.status === 'In-progress',
                danger: item.status === 'To-do',
              }"
            >
              {{ item.status }}
            </span>
          </td>
          <td>
            <div class="list-item__delete" @click="deleteTask(index)">
              <font-awesome-icon :icon="['fa', 'trash-alt']" />
            </div>
          </td>
          <td>
            <div class="list-item__done" @click="doneTask(index)">
              <font-awesome-icon :icon="['fa', 'check']" />
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { library } from "@fortawesome/fontawesome-svg-core";
import { faTrashAlt } from "@fortawesome/free-solid-svg-icons";
import { faCheck } from "@fortawesome/free-solid-svg-icons";
import { faExclamation } from "@fortawesome/free-solid-svg-icons";

library.add(faTrashAlt);
library.add(faCheck);
library.add(faExclamation);

export default {
  name: "list",
  props: {
    newTaskArray: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  data() {
    return {
      statusArray: ["To-do", "In-progress", "Done"],
      emptyArray: true,
    };
  },
  methods: {
    deleteTask(index) {
      this.newTaskArray.splice(index, 1);
    },
    changeStatus(index) {
      let newIndex = this.statusArray.indexOf(this.newTaskArray[index].status);
      if (++newIndex > 2) newIndex = 0;
      this.newTaskArray[index].status = this.statusArray[newIndex];
    },
    doneTask(index) {
      this.newTaskArray[index].status = this.statusArray[2];
    },
  },
  watch: {
    newTaskArray: {
      handler() {
        if (this.newTaskArray == 0) {
          this.emptyArray = true;
        } else {
          this.emptyArray = false;
        }
      },
      deep: true,
    },
  },
};
</script>

<style lang="css">
.list-wrap {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}
.list-wrap__item {
  align-items: center;
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.list-item,
th {
  text-align: left;
}

table,
th,
td {
  padding: 10px;
}

table {
  margin: 0 10px;
}

 table {
        border-collapse: collapse;
        border-radius: 3px;
        border-style: hidden;
        box-shadow: 0 0 0 1px #ccc;
    }

    td {
        border: 1px solid #ccc;
    }

.list-item__delete,
.list-item__edit,
.list-item__status {
  cursor: pointer;
}

.list-item__status {
  width: 120px;
}

.finished {
  text-decoration: line-through;
}

.success {
  color: green;
}

.warning {
  color: darkgoldenrod;
}

.danger {
  color: red;
}

.list-wrap__default-message-icon {
  font-size: 50px;
}

.list-wrap__default-message {
  margin: 15px 20px;
  max-width: 80%;
}

.list-wrap__default-message p {
  text-align: left;
}

@media only screen and (min-width: 900px) {
  .list-wrap__default-message {
    max-width: 40%;
  }
}
</style>
