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


<!--
绑定事件监听 ----订阅消息
触发事件    ----发布消息
-->
<script>
    import Pubsub from 'pubsub-js'
    export default {
        props: {
            todo: Object,
            index: Number
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
                    //this.deleteTodo(index)
                    //发布消息
                    Pubsub.publish('deleteTodo', index)
                }
            }
        }
    }
</script>

<style scoped>

</style>
