<template>
    <div>
        <h2 v-if="firstView">输入用户名搜素</h2>
        <h2 v-if="loading">LOADING...</h2>
        <h2 v-if="errorMsg">{{errorMsg}}</h2>
        <div class="row">
            <div class="card" v-for="(user, index) in users" :key="index">
                <a :href="user.url" target="_blank">
                    <img :src="user.avatar_url" style="width: 100px">
                </a>
                <p class="card-text">{{user.name}}</p>
            </div>

        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                firstView: true,
                loading: false,
                users: null,  //[{url: '', avatar_url: '', name: ''}]
                errorMsg: ''
            }
        }
    }
</script>

<style scoped>

</style>
