<template>
<div class="task" v-bind:class="{hide:task.completed}" >
    <div class="task_block">
        <p class="task__title">Title:{{task.title}}</p>
        <p class="task__desc">Description:{{task.desc}}</p>
    </div>
    <button class="done-task" v-on:click="doneTask" v-bind:class="{done_hide:task.completed}">done</button>
    <button class="delete"
        v-on:click="removeTask(index)"></button>
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
@import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');
.task{
    display: flex;
    flex-direction: row;
    font-family: 'Montserrat', sans-serif;
    padding-left: 2vw;
    font-size: 1.4vw;
    width: 90%;
    height: 10%;
    display: flex;
    text-align: center;
    align-items: center;
    border: 0;
    border-radius: 15px;
    background-color: white;
    margin-bottom: 10px;

}
.done-task.done_hide{ 
    background-color: green;
}
.done-task{
    margin-left: 3%;
    font-size: 1.4vw;
    color: black;
    background-color: rgba(204, 203, 203, 0.965);
    display: flex;
    font-family: 'Montserrat', sans-serif;
    display: flex;
    flex-flow: row wrap;
    align-items: center;
    justify-content: center;
    width: 8vw;
    height: 2.8vw;
    border: 1px solid #000;
    border-radius: 100px;
}
.task_list{
    margin-top:5px;
    width: 100%;
    display: flex;
    justify-content: center;
}
.task_block{
    text-align: left;
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
    margin-right: 10px;
    height: 2.6vw;
    width: 2.6vw;
    border-radius: 50%;
    border: 0px solid black;
    text-align: center;
    align-items: center;
}
.hide{
    background-color: rgb(180, 177, 177);;
}
</style>