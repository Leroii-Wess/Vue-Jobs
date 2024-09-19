<script setup>
import { ref } from "vue";

const name = ref("John Doe");
const status = ref("active");
const tasks = ref(["Task one", "Task two", "Task three"]);
const newTask = ref("");

const toggleStatus = () => {
  if (status.value === "active") {
    status.value = "pending";
  } else if (status.value === "pending") {
    status.value = "inactive";
  } else {
    status.value = "active";
  }
};

const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">Status is active</p>
  <p v-else-if="status === 'pending'">Status is pending</p>
  <p v-else>User is inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">New Task</label>
    <input id="newTask" type="text" v-model="newTask" />
    <button type="submit">add</button>
  </form>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="index">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">x</button>
    </li>
  </ul>

  <button @click="toggleStatus">Toggle status</button>
</template>
