<template>
    <footer class="footer">
        <span class="todo-count">
            <strong>1</strong>
            <span>item left</span>
        </span>
        <ul class="filters">
            <li><a href="#/all">All</a></li>
            <li><a href="#/active">Active</a></li>
            <li><a href="#/completed">Completed</a></li>
        </ul>
        <button class="clear-completed">Clear Completed</button>
    </footer>
</template>

<script>
    export default {
        name:"footerComponent"
    }
</script>

<style lang="scss" scoped>

</style>