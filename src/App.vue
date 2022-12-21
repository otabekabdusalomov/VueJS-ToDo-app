<template>
   <div class="container">
     <Header @toggle-add-task="toggleAddTask" title="Todo" :showAddTask="showAddTask" />
         <div v-if="showAddTask">
          <AddTask @add-task="addTask" />
        </div>
        <Task @toggle-reminder="toggleReminder" @delete-task="deleteTask" :rasks="tasks"/>
   </div>
</template>

<script>
import Header from "./components/Header.vue";

  export default {
        components:{
          Header,

        }    
  }
</script>

<style scoped>

</style>