<template>
    <div class="new-task">
        <input id="title" type="text" v-on:keyup.enter="addTask" placeholder="Title">
        <input id="desc" type="text" v-on:keyup.enter="addTask" placeholder="Description">
        <button class="btn-add" v-on:click="addTask">Add</button>
    </div>
</template>


<script>
export default{
    name: "AddTask",
    methods:{
        addTask(){
            let inputTitle=document.querySelector('#title')
            let inputDesc=document.querySelector('#desc')
            if ((inputTitle.value=='')){
                inputTitle.classList.add('red')
            }
            else if (inputDesc.value==''){
            inputDesc.classList.add('red')
            } 
            else {
                inputTitle.classList.remove('red')
                inputDesc.classList.remove('red')
            
                this.$emit('add-task',{
                    title:inputTitle.value,
                    desc:inputDesc.value,
                    completed:false,
                    date: new Date(),
                })
                inputTitle.value='',
                inputDesc.value=''
            }
        }
    },
}

</script>


<style>
.red{
    border: 3px solid red;
}
.new-task{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}
input{
    font-size: 1.6vw;
    font-family: 'Montserrat', sans-serif;
    width: 20vw;
    padding-left: 2vw;
    height: 3vw;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 0;
    border-radius: 100px;
}
input:nth-child(2){
    margin-left: 10px;
}
.btn-add{
     margin-left: 3%;
    font-size: 1.4vw;
    color: white;
    background-color: #51ADBB;
    display: flex;
    font-family: 'Montserrat', sans-serif;
    display: flex;
    flex-flow: row wrap;
    align-items: center;
    justify-content: center;
    width: 10vw;
    height: 2.8vw;
    border: 0;
    border-radius: 100px;
}
</style>
