<template>
    <div @dblclick="$emit('toggle-reminder', task.id
    )" :class="[task.reminder ? 'reminder' : '', 'task']">
       <div class="d-flex align-items-center justify-content-between">
        <h3>{{task.text}}</h3>
        <span @click="$emit( 'delete-task', task.id)" class="close-btn">❌</span>
       </div>
       <p class="m-0">{{task.day}}</p>
    </div>
</template>

<script>
export default {
    name: "Task",
    props: {
        task: Object
    },
}
</script>

<style scoped>
    .task{
        background-color: #f4f4f4;
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
    }
    .task.reminder{
        border-left: 5px solid green;
    }

    .task h3 {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

</style>