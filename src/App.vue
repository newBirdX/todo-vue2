<template>
   <section  class="todoapp">
     <header class="header">
       <h1>Todo</h1>
       <input type="text" placeholder="What need to be done?" class="new-todo" v-model="newTodo" @keyup.enter="addTodo">
     </header>
     <section class="main">
       <input type="checkbox" class="toggle-all" id="toggle-all">
       <label for="toggle-all"></label>
       <ul class="todo-list">
         <Item v-for="item in todoDatas" :key="item.id" :todo="item"/>
       </ul>
     </section>
     <Footer/>
  </section> 
</template>

<script>
import './css/index.css'
import Item from './components/item.vue'
import Footer from './components/footer.vue'
  export default {
    name:"App",
    components:{Item,Footer},
    data(){
      return {
        todoDatas:[] ,//存放所有todo
        newTodo:"" //新建todo
      }
    },
    methods:{
      addTodo(){
        if(this.newTodo==="") return ;
        let todo={};
        todo.id=new Date().getTime();
        todo.text=this.newTodo;
        todo.hasCompleted=false;
        this.todoDatas.push(todo);
        this.newTodo="";
      }
    }
  }
</script>

<style lang="css" scoped>

</style>