<template>
    <div>
        <header class="site-header jumbotorn">
          <div class="container">
            <div class="row">
              <div class="col-xs-12">
                <h1>请发表对Vue的评论</h1>
              </div>
            </div>
          </div>
        </header>
        <div class="container">
            <Add :addComment="addComment"/>
            <!--组件间通信：标签属性，一般属性名与数据名同名-->
            <List :comments="comments" :deleteComment="deleteComment"/>
        </div>
    </div>

</template>

<script>
    import Add from './components/Add.vue'
    import List from './components/List.vue'
    export default {
        data(){
            return{
                comments: [ // 数据在哪个组件，更新数据的行为（方法）就应该定义在哪个组件
                    {
                        name: 'AAA',
                        content: 'aaaa'
                    },
                    {
                        name: 'BBB',
                        content: 'bbbb'
                    },
                    {
                        name: 'CCC',
                        content: 'ccc'
                    },
                ]
            }
        },
        methods: {
            //添加评论
            addComment(comment){
                this.comments.unshift(comment)
            },

            //删除指定下标的评论
            deleteComment(index) {
                this.comments.splice(index, 1)
            }
        },
        components: {
            Add,
            List
        }
    }
</script>

<style>

</style>
