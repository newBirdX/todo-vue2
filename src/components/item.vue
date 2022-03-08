<template>
    <li :class="{completed:todo.hasCompleted,editing:editingTodo===todo}">
        <div class="view">
            <input type="checkbox" class="toggle" v-model="todo.hasCompleted">
            <label @dblclick="editTodo">{{todo.text}}</label>
            <button class="destroy" @click="delTodo(todo.id)"></button>    
        </div>
        <input type="text" class="edit"
        v-model.trim="editingTodo.text"
        v-focus
        @blur="doneTodo"
        @keyup.enter="doneTodo"
        @keyup.esc="cancelTodo(index)"
        >
    </li>
</template>

<script>
    export default {
        name:"itemComponent",
        props:['todo','index'],
        data(){
            return {
                editingTodo:"",
                value:""
            }
        },
        methods:{
            delTodo(id){
                this.$parent.todoDatas=this.$parent.todoDatas.filter(todo=>{
                    return !(todo.id===id)
                })
            },
            editTodo(){
                this.value=this.todo.text
                this.editingTodo=this.todo;
            },
            doneTodo(){
                this.editingTodo=""
            },
            cancelTodo(index){
                this.$parent.todoDatas[index].text=this.value;
                this.editingTodo=""
            }
        },
        //自定义指令
        directives:{
            focus(el,value){
                // console.log(el);
                el.focus()
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>