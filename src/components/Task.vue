<template>
    <div @dblclick="taggleReminder(task.id)"  :class="[task.reminder ? 'reminder': '', 'task'] ">
        <h3>{{task.text}} <i @click="taskDelete(task.id)" class="fas fa-times"></i></h3>
        <p>{{task.day}}</p>
    </div>
  
</template>

<script>
export default {

    name: 'Task',

    props:{
        task: Object,
    },

    methods:{
        taskDelete(id){
            this.$emit('delete-task', id)
        },
        taggleReminder(id){
            this.$emit('taggle-reminder', id)
        },
    },
    // emits: ['delete-task'],

}
</script>

<style scped>
.task{
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}
.task.reminder{
    border-left: 5px solid green;
}
.task h3{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
i.fa-times{
    color: red;
}
</style>