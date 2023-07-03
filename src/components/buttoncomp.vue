<template>
  <button class="addTaskButton" @click="addTask">{{ buttonText }}</button>
</template>

<script>
export default {
  props: ['addTask', 'buttonText'],
}

</script>
