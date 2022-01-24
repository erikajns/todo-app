<template>
  <div class="list-wrap">
    <table>
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
            <div class="list-item__edit">
              <font-awesome-icon :icon="['fa', 'pen']" />
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
import { faPen } from "@fortawesome/free-solid-svg-icons";

library.add(faTrashAlt);
library.add(faPen);

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
  border: 1px solid black;
  border-collapse: collapse;
  padding: 10px;
}

table {
  margin: 0 10px;
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
</style>
