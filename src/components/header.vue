<template>
  <header>
      <h1>{{ titleTag }}</h1>
      <Button  @taggle-add-task="$emit('taggle-add-task')" :text="showAddTask ? 'Close': 'Add Task'" :color="showAddTask ? '#aa0000': 'green'"/>
  </header>
</template>

<script>
import Button from "./Button.vue"
export default {
    name:'HeaderComp',


    props:{
        titleTag: String,
        showAddTask: Boolean,
    },

    components:{
        Button,
    },
    emits:['taggle-add-task'],
  

}
</script>

<style scoped>
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>