
<script setup>
import { ref } from "vue";

const msg = 'Todo App';
const text = ref('');
const checked = ref(false);
const tasks = ref([])

function addTask() {
  tasks.value.push(text.value)
  text.value = " "
}
function deleteTask(){
  tasks.value.pop()
}
</script>

<style>
.title {
  font-size: 35px;
}
.deleteButton{
  font-size: 10px;

}

</style>
<template>
  <h1 class="font-bold title">{{ msg }}</h1>
  <div class="flex mt-[10px]">
    <input v-model="text" type="input" placeholder="Task here">
  </div>

  <div class="border border-gray-300 rounded-lg p-1 inline-block">
    <button
      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
      @click="addTask">Add Task</button>
  </div>
  <!--<div>{{ transferredText }} <input type="checkbox" id="checkbox" v-model="checked"></div>
  -->

  <div>
    <ul>
      <li v-for="task in tasks" :key="task">{{ task }} 
        <label v-if="task != ' '">
          <input type="checkbox" id="checkbox" v-model="task.checked">
          <button class="bg-red-500 hover:bg-red-700 text-white font-bold py-1 px-1 rounded deleteButton"
          @click="deleteTask()">Delete</button>
        </label>
    </li>
    </ul>
  </div>

</template>