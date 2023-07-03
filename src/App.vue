<template>
  <greet /> 
  <h1 class="title">{{ msg }}</h1>

  <!-- Container containing the text box and add task button -->
  <div class="flex-container">
    <input v-model="text" type="input" placeholder="Task here" @input="updateForm('task', $event.target.value)">
    <button-comp :addTask="addTask" buttonText="Add Task" />
  </div>

  <div>
    <ul>
      <!-- Adds a delete button and checkbox next to each task (separately linked) -->
      <task-item v-for="(task, index) in tasks" :key="index" :task="task" :index="index" @delete-task="deleteTask" @save-storage="saveStorage" />
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import ButtonComp from './components/buttonComp.vue';
import taskItem from './components/taskItem.vue';

const msg = 'Todo App';
const text = ref('');
const tasks = ref([]);
const form = ref({});

// Create functions and set up for local storage
function addTask() {
  tasks.value = [...tasks.value, { task: text.value, checked: false }];
  saveStorage();
  text.value = '';
}
function updateForm(input, value) {
  form.value[input] = value;
  saveStorage();
}
function deleteTask(index) {
  tasks.value.splice(index, 1);
  saveStorage();
}
function openStorage() {
  const storedTasks = localStorage.getItem('tasks');
  return storedTasks ? JSON.parse(storedTasks) : [];
}

function saveStorage() {
  localStorage.setItem('tasks', JSON.stringify(tasks.value));
}

onMounted(() => {
  tasks.value = openStorage();
});
</script>

<!-- Set up styling -->
<style>
.title {
  display: flex;
  font-size: 35px;
  justify-content: center;
  font-weight: bold;
}
.deleteButton{
  font-size: 10px;
}
.larger {
  width: 20px;
  height: 20px;
  margin-top: 20px;
}
.flex-container{
  display: flex;
  justify-content: center;

}
.addTaskButton{
  background-color: rgb(20, 50, 218);
  padding: 8px; 
  border-radius: 5px;
  font-family: verdana;
  color: white
}
.addTaskButton:hover{
  background-color: rgb(10, 38, 109);
}
.deleteButton{
  background-color: red;
  padding: 4px;
  border-radius: 2px;
  font-family: verdana;
  color: white;
}
.deleteButton:hover{
  background-color: rgb(194, 14, 14);

}
</style>