<template>
    <li>
        <div class="view">
            <input type="checkbox" class="toggle">
            <label>{{todo.text}}</label>
            <button class="destroy"></button>    
        </div>
        <input type="text" class="edit">
    </li>
</template>

<script>
    export default {
        name:"itemComponent",
        props:['todo']
    }
</script>

<style lang="scss" scoped>

</style>