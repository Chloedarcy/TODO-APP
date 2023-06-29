<script setup>
import {ref} from "vue";
import buttoncomp from "./components/buttoncomp.vue";

const task = ref(68);

const msg = 'Todo App';
const text = ref('Text');

function retrieveTask(){
  console.log(text)
  
}

</script>

<style>
.title {
  font-size: 35px;
}
</style>

<template>
   <h1 class="font-bold title" >
    {{ msg }}
  </h1>
  <div class ="flex mt-[10px]" >
    <input v-model="text" placeholder="Task here">
    <p>Message is: {{ text }}</p>
  </div>
 
  <div class="border border-gray-300 rounded-lg p-1 inline-block">
    <button
    class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
    @click="retrieveTask"
    
    >Add</button>
  </div>

  <div>
    <input type="checkbox" id="checkbox" v-model="checked">
  </div>

</template>


