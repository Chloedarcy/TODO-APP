<script setup>
import clickButton from "./components/buttoncomp.vue"

const msg = 'Todo App';
</script>

<template>
  <h1 style="text-align: center;">
    {{ msg }}
  </h1>
  <div class ="flex mt-[10px]" >
    <clickButton/>
  </div>
</template>

