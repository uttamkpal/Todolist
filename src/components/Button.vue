<template>
  <button @click="taggleAddTask" class="btn" :style='{background:color}' >{{text}}</button>
</template>

<script>
export default {
    name:'Button',


    props:{
        text: String,
        color: String,
    },
    methods:{
      taggleAddTask(){
        this.$emit('taggle-add-task')
      }
    }

}
</script>

<style>

</style>