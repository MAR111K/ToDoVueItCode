<template>
<div class="functions">
    <button class="delete-all" v-on:click="removeAllTasks">delete</button>
    <input class="entry-search" type="text" v-on:keyup.enter="searchTitle">
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
        }

        },
        
    }
</script>
<style>
.functions{
    display: flex;
    flex-direction: row;
    align-items: center;
}
</style>