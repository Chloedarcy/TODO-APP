<script setup>
    import {ref} from "vue"
    const count = ref(0)
    const props = defineProps(["task", "status"])
</script>
<template>
  <div class="border border-gray-300 rounded-lg p-4 inline-block">
    <button class="bg-green-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
      {{ props.task }}<br>{{ props.status }}
    </button>
  </div>
</template>