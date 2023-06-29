
<script setup>
import { ref } from "vue";

const msg = 'Todo App';
const text = ref('');
const tasks = ref([])

function addTask() {
  tasks.value.push(text.value)
  text.value = " "
}
function deleteTask(index){
  tasks.value.splice(index, 1)
}
</script>

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
<template>
  <h1 class="title">{{ msg }}</h1>
  <div class="flex-container">
    <input v-model="text" type="input" placeholder="Task here">
    <button
      class="addTaskButton"
      @click="addTask">Add Task</button>
  </div>

  <div>
    <ul>
      <li v-for="task in tasks" :key="task">
        <div class="flex-container">
        <label v-if="task != ' '">
          <input class="larger" type="checkbox" id="checkbox" v-model="task.checked">
          {{ task }} 
          <button class="deleteButton"
          @click="deleteTask(index)">Delete</button>
        </label>
      </div>
    </li>
    </ul>
  </div>

</template>