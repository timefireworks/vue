<template>
    <div class="container">
        <Search/>
        <UsersMain/>
    </div>
</template>

<script>
    import Search from './components/Search.vue'
    import Main from './components/main.vue'
    export default {
        components: {
            Search,
            UsersMain: Main //给Main标签取别名，因为Main在html中不能用，已经有这个标签
        }
    }
</script>

<style scoped>

</style>
