<script>
import HeaderComp from "./components/header.vue"
import Tasks from "./components/Tasks.vue"
import addTaskForm from "./components/addTask.vue"
export default{
  name: 'App',

  data(){
    return{
      tasks: [],
      showAddTask: false,
    }
  },

  components:{
    HeaderComp,
    Tasks,
    addTaskForm 
  },
  methods :{
    taggleTaskForm(){
      this.showAddTask = !this.showAddTask
    },
    addTask(task){
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id){
      if(confirm("Are you sure to delete?")){
        this.tasks = this.tasks.filter((task) => task.id !==id)
      }
      
    },
    taggleRemainder(id){
      console.log(id);
      this.tasks= this.tasks.map((task) => task.id === id ? {...task, reminder:!task.reminder} : task )
    },
  },
  // emits: ['task-delete'],
  created(){
    this.tasks = [
      {
        id: 1,
        text:'Doctors Appointment',
        day: 'March 1st at 2:30PM',
        reminder: true,
      },
      {
        id: 2,
        text:'Boss Appointment',
        day: 'March 2st at 2:30PM',
        reminder: false, 
      },
      {
        id: 3,
        text:'Client Appointment',
        day: 'March 3st at 2:30PM',
        reminder: true,
      },
    ]
  }
  

}

</script>

<template>
<div class="container">
 <HeaderComp :showAddTask='showAddTask' @taggle-add-task='taggleTaskForm' titleTag="Task Tracker" />
 <div v-show='showAddTask'>
   <addTaskForm @add-task='addTask' />
 </div>
 
 <Tasks @taggle-reminder="taggleRemainder" @task-delete="deleteTask" :tasks="tasks" />
</div>
</template>

<style>
/* @import './assets/base.css'; */

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 400px;
  margin: 30px auto;
  overflow: auto;
  min-height: 400px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html,
body {
  font-family: Arial, Helvetica, sans-serif;
}



h1,
h3 {
  margin-bottom: 1rem;
  font-weight: normal;
}

img {
  border-radius: 100%;
  border: 5px #333 solid;
  margin-bottom: 1rem;
  height: 150px;
  width: 150px;
}

.male {
  border-color: steelblue;
  background-color: rgb(70, 131, 180);
}

.female {
  border-color: pink;
  background-color: pink;
  color: #333;
}

button {
  cursor: pointer;
  background: #333;
  color: white;
  font-size: 18px;
  border: 0;
  padding: .3rem .5rem;
}

button:focus {
  outline: none;
}

button:hover {
  transform: scale(0.98);
}


</style>
