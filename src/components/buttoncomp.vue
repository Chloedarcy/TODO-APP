<template>
  <button class="addTaskButton" @click="addTask">{{ buttonText }}</button>
</template>

<script>
export default {
  props: ['addTask', 'buttonText'],
}
function addTask() {
  tasks.value = [...tasks.value, { task: text.value, checked: false }];
  text.value = '';
  saveStorage();
}
</script>
