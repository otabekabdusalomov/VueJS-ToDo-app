<template>
  <div class="container">
   <Header @toggle-add-task="toggleAddTask" title="Todo" :showAddTask="showAddTask" />
   <div v-if="showAddTask">
       <AddTask @add-task="addTask"/>
   </div>
   <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
   </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';

export default {
   name: "App",
   components: {
   Header,
   Tasks,
   AddTask
},
   data() {
       return {
           tasks: [],
           showAddTask: false
       }
   },
   methods: {
       toggleAddTask() {
           this.showAddTask = !this.showAddTask
       },
       addTask(task) {
           this.tasks = [...this.tasks, task]
       },
       deleteTask(id) {
           if(confirm("O'chirib tashlashga rozimisiz!")) {
               this.tasks = this.tasks.filter((tasks) => tasks.id !== id)
           }
       },
       toggleReminder(id) {
           if(confirm("Asosiy rejani belgilash")) {
               this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder : !task.reminder} : task)
           }
       }
   },
   created() {
       this.tasks = [
           {
               id:1,
               text: "Topshiriqlar ro'yhati",
               day: "Habar qo'shish uchun 'Add' tugmasini bosing",
               reminder: false
           },
       ]
   },
};
</script>

<style>
   *{
   box-sizing: border-box;
   padding: 0;
   margin: 0;
}

body{
   font-family:  'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif
}

.container{
   max-width: 500px;
   margin: 30px auto;
   overflow: auto;
   min-height: 300px;
   border: 1px solid steelblue;
   padding: 30px;
   border-radius: 5px;
}

.btn{
   display: inline-block;
   background-color: #000;
   color: #fff;
   border: none;
   padding: 10px 20px;
   margin: 5px;
   border-radius: 5px;
   cursor: pointer;
   text-decoration: none;
   font-size: 15px;
   font-family: inherit;
   border: 1px solid transparent;
}

.btn:hover{
   background-color: transparent !important;
   border: 1px solid black !important;
}

.btn:focus{
   transform: scale(0.98);
}
.btn-block{
   display: block;
   width: 100%;
}
</style>