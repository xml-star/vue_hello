<template>
    <div>
<!--        <button @click="setUser"></button>-->
        <span>这是User组件</span>
        <table border="2">
            <tr>
                <td>id</td>
                <td>name</td>
                <td>age</td>
                <td>bir</td>
                <td>操作</td>
            </tr>
            <tr v-for="(user,index,key) in users" :key="user.id">
                <td>{{user.id}}</td>
                <td>{{user.name}}</td>
                <td>{{user.age}}</td>
                <td>{{user.bir}}</td>
                <td><a href="javascript:;" @click="del(index,users)">删除</a>| <router-link :to="`/detail/${user.id}`">详细信息</router-link></td>
            </tr>
        </table>
        <hr>

        姓名：<input type="text" v-model="name"><br>
        年龄：<input type="text" v-model="age"><br>
        生日：<input type="text" v-model="bir"><br>
        <br>
        <input type="button" value="添加用户" @click="add">
    </div>


</template>

<script>
export default {
    name: "User",
    data:function (){
        return{
            name:"",
            age:"",
            bir:"",
            users:localStorage.users?JSON.parse(localStorage.users):[]
        }
    },
    methods:{
        add(){
            let id='';
            if(localStorage.users){
                for(let i=this.users.length-1;i<this.users.length;i++){
                    id = parseInt(this.users[i].id)+1
                }
            }else{
                id=1
            }

            // alert()
            let name = this.name
            let age = this.age
            let bir = this.bir
            this.users.push({'id':id,"name":name,"age":age,"bir":bir});
            this.name = '',
            this.age = '',
            this.bir = '',
            localStorage.users = JSON.stringify(this.users)

        },
        del(index,users){
            // alert()
            this.users.splice(index,1)
            if(this.users.length){
                localStorage.users = JSON.stringify(this.users)
            }else {
                localStorage.removeItem('users')
            }

        }
    }
}
</script>

<style scoped>

</style>
