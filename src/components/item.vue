<template>
    <li>
        <div class="view">
            <input type="checkbox" class="toggle">
            <label>{{todo.text}}</label>
            <button class="destroy" @click="delTodo(todo.id)"></button>    
        </div>
        <input type="text" class="edit">
    </li>
</template>

<script>
    export default {
        name:"itemComponent",
        props:['todo'],
        methods:{
            delTodo(id){
                this.$parent.todoDatas=this.$parent.todoDatas.filter(todo=>{
                    return !(todo.id===id)
                })
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>