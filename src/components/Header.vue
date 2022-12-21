<template>
    <header class="site-header">
        <h1>{{ title }}</h1>
        <Button  @toggle-add-task="$emit('toggle-add-task',)" :text="showAddTask ? 'Chiqish' : 'Add' " :color="showAddTask ? 'crimson' : 'green'"/>
    </header>
</template>


<script>
import Button from "./Button.vue";

export default {
    name: "Header",
    props: {
        title: String,
        showAddTask: Boolean
    },
    components: {
        Button
    }
}
</script>

<style>
  .site-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>