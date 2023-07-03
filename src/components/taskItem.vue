<template>
    <li>
      <div class="flex-container">
        <label v-if="task.task !== ' '">
          <input class="larger" type="checkbox" id="checkbox" v-model="task.checked" @change="updateForm('checkbox', task.checked)">
          {{ task.task }} 
          <button class="deleteButton" @click="deleteTask(index)">Delete</button>
        </label>
      </div>
    </li>
  </template>
  
  <script>
  export default {
    props: ['task', 'index',],
    
    methods: {
    deleteTask() {
      this.$emit('delete-task', this.index);
      this.$emit('save-storage'); 
    },
    updateForm(input, value) {
      this.task.checked = value;
      this.$emit('save-storage'); 
    }
  },
}
</script>