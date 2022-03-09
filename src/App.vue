<template>
  <div id="app">
     <h1>To Do List</h1>
    <AddTask 
    @add-task="saveNewTask"
    ></AddTask>

    <FunctionsTask 
    @remove-tasks="removeTasks"
    @search-title="searchTitle"
    ></FunctionsTask>
    
    <CardTask 
    @remove="remove(index)"
    @completed-task="completTask"
    v-for="(task,index) in tasks"
    :key="index" 
    :task="task"
    :index="index">
    </CardTask>


    <CardTask
    @remove="remove(index)"
    @completed-task="completTask"
    v-for="(task,index) in tasks_completed"
    :key="`task-${index}`" 
    :task="task"
    :index="index">
    </CardTask>
    
  </div>
</template>

<script>

import AddTask from  './components/AddTask.vue';
import CardTask from './components/CardTask.vue';
import FunctionsTask from './components/FunctionsTask.vue';

export default {
  name:'App',
  data(){
    return {
      tasks:[],
      tasks_completed:[],
      'id':Number,
    }

  },
  components:{
    AddTask,
    FunctionsTask,
    CardTask,
  },
  methods:{
    saveNewTask(data){
      this.tasks.push(data)
    },
    remove(index){
      console.log(index)
      this.tasks.splice(index,1)

    },
    removeTasks(){
      this.tasks = []
    },
    completTask(task){
       if (task.completed){
         this.tasks.push(task)
         this.tasks_completed=this.tasks_completed.filter(item=>item!==task)
         }else{
           this.tasks_completed.push(task)
           this.tasks=this.tasks.filter(item=>item!==task)
           
         }
         task.completed=!task.completed
       
    },
    searchTitle(){
       let query = document.querySelector(".entry-search").value
        let generalTasks = this.tasks.concat(this.tasks_completed)
        let neededTask = generalTasks.find(task => task.title == query)
        alert(`
        Search results
        Name of task:${neededTask.title}
        Description of task${neededTask.desc}
        ${neededTask.completed ? 'Task completed' : 'Task active'}
        `)
    }
  }
}

</script>

<style>

body {
    background: #F5EbE0;
    max-width: 2560%;
    overflow-x: hidden;
}
input{
  border: 1px solid black;
}
h1, h2 {
    display: flex;
    justify-content: center;
    align-items: center;
    display: flex;
    width: 100%;
    font-size: 5vw;
    font-family: 'Montserrat', sans-serif;
    color: black;
    font-weight: bold;
    align-items: center;
    justify-content: center
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

</style>
