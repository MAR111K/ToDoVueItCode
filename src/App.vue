<template>
  <div id="app">
     <h1>To Do List</h1>
    <div class="input_wrapper">
      <AddTask 
      @add-task="saveNewTask"
      ></AddTask>

      <FunctionsTask 
      @remove-tasks="removeTasks"
      @search-title="searchTitle"
      @filter-date="filterDate"
      ></FunctionsTask>
    </div>
    <div class="list_task">
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
      let listTask=document.querySelector('.list_task')
      listTask.classList.add('list_border')
    },
    remove(index){
      console.log(index)
      this.tasks.splice(index,1)

    },
    removeTasks(){
      this.tasks = []
    },
    completTask(task){
        if (task.completed)
          {
          this.tasks.push(task)
          this.tasks_completed=this.tasks_completed.filter(item=>item!==task)
          }
        else
          {
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
        Results:
        Title:${neededTask.title}
        Description:${neededTask.desc}
        ${neededTask.completed ? 'Task completed' : 'Task active'}
        `)
    },
    filterDate(){
      this.tasks.sort((a,b)=>a.date>b.date ? 1:-1)
      this.tasks_completed.sort((a,b)=>a.date>b.date ? 1:-1)
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
.list_task{
  margin-top: 30px;
  padding: 10px 10px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 60%;
  border-radius: 10px;
}
.list_border{
   border: 1px solid rgb(116, 114, 114);
}
.input_wrapper{
  display: flex;
  flex-direction: column;
  align-content: space-between;
  border: 1px solid rgb(112, 111, 111);
  border-radius: 10px;
  padding: 10px;
}
</style>
