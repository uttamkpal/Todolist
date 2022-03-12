<template>
    <div v-for="task in tasks" :key='task.id'>
        <Task @taggle-reminder="$emit('taggle-reminder', task.id)" @delete-task="$emit('task-delete', task.id)" :task="task" />
    </div>

</template>

<script>
import Task from "./Task.vue"
export default {
    name: 'Tasks',

    props:{
        tasks : Array,
    },
    components:{
        Task,
    },
    emits: ['task-delete', 'taggle-reminder'],
    methods: {
    
    },

}
</script>

<style>

</style>