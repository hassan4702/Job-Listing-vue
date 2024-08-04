<script setup>
import { onMounted, ref } from "vue";

const status = ref("active");
const message = "Hello Vue 3";
const tasks = ref(["task1", "task2", "task3"]);
const newTask = ref("");
const toggleStatus = () => {
  status.value = status.value === "active" ? "inactive" : "active";
};
const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};
const removeTask = (index) => {
  tasks.value.splice(index, 1);
};

onMounted(async () => {
  try {
    const res = await fetch("https://jsonplaceholder.typicode.com/todos");
    const data = await res.json();
    tasks.value = data.map((task) => task.title);
  } catch (error) {
    console.log(error);
  }
});
</script>

<template>
  <div id="app">{{ status }} {{ message }}</div>
  <ul>
    <li v-for="task in tasks" :key="task">
      <span>{{ task }}</span>
      <button @click="removeTask(tasks.indexOf(task))">Remove</button>
    </li>
  </ul>

  <form @submit.prevent="addTask">
    <label for="newTask">New Task</label>
    <input type="text" id="newTask" v-model="newTask" />
    <button type="submit">Add Task</button>
  </form>
  <button @click="toggleStatus">Toggle</button>
</template>
