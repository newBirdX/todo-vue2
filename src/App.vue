<template>
   <section  class="todoapp">
     <header class="header">
       <h1>Todo</h1>
       <input type="text" placeholder="What need to be done?" class="new-todo" v-model="newTodo" @keyup.enter="addTodo">
     </header>
     <section class="main">
       <input type="checkbox" class="toggle-all" id="toggle-all" v-model="isAll">
       <label for="toggle-all"></label>
       <ul class="todo-list">
         <Item v-for="(item,index) in fliterTodoDatas" :key="item.id" :todo="item" :index="index"/>
       </ul>
     </section>
     <Footer :view="view"/>
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
        newTodo:"" ,//新建todo
        view:"all"
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
    },
    //使用计算属性来设置全选全不选
    computed:{
      isAll:{
        get(){
          return false
        },
        set(value){
          return this.todoDatas.map(item=>{
            item.hasCompleted=value
          })
        }
      },
      fliterTodoDatas(){
        switch(this.view){
          case 'all':
            return this.todoDatas;
          case 'active':
            return this.todoDatas.filter(value=>{
              return !value.hasCompleted
            })
          case 'completed':
            return this.todoDatas.filter(value=>{
              return value.hasCompleted
            })
          default :
            return this.todoDatas;
        }
      }
    }
  }
</script>

<style lang="css" scoped>

</style>