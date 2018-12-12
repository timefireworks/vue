<template>
    <!--
    -->
    <li @mouseenter="handleEnter(true)" @mouseleave="handleEnter(false)" :style="{background: bgColor}">
        <label>
            <input type="checkbox" v-model="todo.complete"/>
            <span>{{todo.title}}</span>
        </label>
        <button class="btn btn-danger" v-show="isShow" @click="deleteItem">删除</button>
    </li>
</template>

<script>

    export default {
        props: {
            todo: Object,
            index: Number,
            deleteTodo: Function
        },
        data() {
            return {
                bgColor: 'whitle',//默认背景颜色
                isShow: false  //按钮默认是否显示
            }
        },
        methods: {
            handleEnter(isEnter) {
                if(isEnter) {
                    this.bgColor = '#aaaaaa'
                    this.isShow = true
                } else {
                    this.bgColor = 'white'
                    this.isShow = false
                }
            },
            deleteItem() {
                console.info('deleteItem')
                const {todo, index} = this
                if(window.confirm('确认删除' + todo.title + '吗？')){
                    this.deleteTodo(index)
                    handleEnter(true)
                }
            }
        }
    }
</script>

<style scoped>

</style>
