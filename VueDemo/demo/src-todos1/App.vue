<template>
    <div class="todo-container">
        <div class="todo-wrap">
            <TodoHeader :addTodo="addTodo"/>
            <TodoList :todos="todos" :deleteTodo="deleteTodo"/>
            <TodoFooter :todos="todos" :deleteCompleteTodos="deleteCompleteTodos" :selectAllTodos="selectAllTodos"/>
        </div>
    </div>
</template>

<script>
    import TodoHeader from './components/TodoHeader'
    import TodoList from './components/TodoList'
    import TodoFooter from './components/TodoFooter'

    export default {
        data() {
            return {
                //从localStorage读取todos
                todos: JSON.parse(window.localStorage.getItem('todos_key') || '[]')
                /*todos: [
                    {title: 'aaa', complete: false},
                    {title: 'bbb', complete: true},
                    {title: 'ccc', complete: false}
                ]*/
            }
        },

        watch: {//监视
            todos: {
                deep: true, //深度监视
                handler: function (value) {
                    //将todos最新的的json数据，保存到localStorage
                    window.localStorage.setItem('todos_key', JSON.stringify(value))
                }
            }
        },

        methods: {
            addTodo(todo) {
                this.todos.unshift(todo)
            },

            deleteTodo(index) {
                this.todos.splice(index, 1)
            },

            //删除所有选中的
            deleteCompleteTodos() {
                this.todos = this.todos.filter(todo => !todo.complete)
            },

            //全选/全不选, 参数是全选的复选框是否选中
            selectAllTodos(check) {
                this.todos.forEach(todo => todo.complete = check)
            }
        },

        components: {
            TodoHeader,
            TodoList,
            TodoFooter
        }
    }
</script>

<style scoped>

</style>
