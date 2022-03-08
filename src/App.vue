<template>
   <section  class="todoapp">
     <header class="header">
       <h1>Todo</h1>
       <input type="text" placeholder="What need to be done?" class="new-todo">
     </header>
     <section class="main">
       <input type="checkbox" class="toggle-all" id="toggle-all">
       <label for="toggle-all"></label>
       <ul class="todo-list">
         <Item/>
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
    components:{Item,Footer}
  }
</script>

<style lang="css" scoped>

</style>