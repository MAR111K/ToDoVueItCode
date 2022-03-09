<template>
<div class="task_list">
    <div class="task" v-bind:class="{hide:task.completed}" >
        <p class="task__title">Title:{{task.title}}</p>
        <p class="task__desc">Description:{{task.desc}}</p>
        <button v-on:click="doneTask">delete</button>
        <button class="delete"
         v-on:click="removeTask(index)">xtr</button>
    </div>
    
</div>
</template>


<script>

export default {
    name:"CardTask",
    props: {
        task:{type:Object},
        index:{type:Number},
    },
    methods:{
        removeTask(index){
            this.$emit('remove',this.task,index)
        },
        doneTask(){
            this.$emit('completed-task',this.task)
           
        }
    }
}
</script>



<style>

.task{
    display: flex;
    flex-direction: row;
    font-family: 'Montserrat', sans-serif;
    padding-left: 2vw;
    font-size: 1.4vw;
    width: 50%;
    height: 10%;
    display: flex;
    text-align: center;
    align-items: center;
    border: 0;
    border-radius: 15px;
    background-color: white;
    margin-bottom: 2px;

}
.task_list{
    margin-top:5px;
    width: 100%;
    display: flex;
    justify-content: center;
}
.delete{
     display: flex;
    font-size: 1.4vw;
    color: white;
    background: url(@/assets/cross.svg) no-repeat;
    background-size: 2.6vw;
    background-position-x: center;
    background-position-y: center;
    display: flex;
    font-family: "PT Sans Narrow";
    display: flex;
    margin-left: auto;
    margin-right: 0px;
    height: 2.6vw;
    width: 2.6vw;
    border-radius: 50%;
    border: 0px solid black;
    text-align: center;
    align-items: center;
}
.hide{
    text-decoration: line-through;
}
</style>