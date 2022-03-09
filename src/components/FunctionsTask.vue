<template>
<div class="functions">
    <input class="entry-search" placeholder="Search Title" type="text" v-on:keyup.enter="searchTitle">
    <button class="delete-all" v-on:click="removeAllTasks">Delete</button>
    <button class="filer-btn" v-on:click="filterDate">Filter</button>
</div>
</template>
<script>
export default{
    name: "FunctionsTask",
    methods:{
        removeAllTasks() {
            this.$emit('remove-tasks')
        },
        searchTitle(){
            this.$emit('search-title')
        },
        filterDate(){
            this.$emit('filter-date')
        },
    },
}
</script>


<style>
.functions{
    display: flex;
    flex-direction: row;
    align-items: center;
    margin-top: 10px;
}
.delete-all{
     margin-left: 3%;
    font-size: 1.4vw;
    color: white;
    background-color: #d02b2b;
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
.filer-btn{
     margin-left: 3%;
    font-size: 1.4vw;
    color: white;
    background-color: green;
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