<script setup>
import {ref} from "vue";
import clickButton from "./components/buttoncomp.vue";

const bobAge = ref(68);

const msg = 'Todo App';
</script>

<template>
  <h1 style="text-align: center;">
    {{ msg }}
  </h1>
  <div class ="flex mt-[10px]" >
    <clickButton @click="bobAge++"  :name="''" :age="bobAge">This is some text</clickButton>
  </div>
</template>

