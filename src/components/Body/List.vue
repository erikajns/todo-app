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
          <td>{{ item.task }}</td>
          <td>{{ item.status }}</td>
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
  methods: {
    deleteTask(index) {
      this.newTaskArray.splice(index, 1);
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

.list-item__delete,
.list-item__edit {
  cursor: pointer;
}
</style>
