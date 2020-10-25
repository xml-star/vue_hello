<template>
    <div id="app">

        <h3 @event="getUser">这是主页</h3>
        <router-link to="/home">访问Home组件</router-link>
        <router-link to="/user" @click="getUser">访问User组件</router-link>
        <hr>


        <router-view></router-view>

    </div>
</template>

<script>
export default {
    name: 'App',
    data() {
        return {

        }
    },
    methods:{
        getUser(){
            let user = JSON.parse(local.user0)
        }
    }


}
</script>

<style>
#app {

}
</style>
