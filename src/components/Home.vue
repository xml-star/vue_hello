<template>
    <div>这点Home组件
    <hr>
        <input type="text" v-model="msg">
        <button @click="send_msg">发表留言</button>
        <ul v-for="(msg,index) in msg_list">
            <li>{{msg}}<a href="javascript:;" @click="del(index,msg_list)">删除</a></li>
        </ul>
        <span v-show="isShow">共有留言{{msg_list.length}}条</span>
        <input type="button" value="删除所有" @click="del_all" v-show="isShow">

    </div>

</template>

<script>
export default {
    name: "Home",
    data(){
        return{
            isShow:true,
            msg:"",
            msg_list:localStorage.msgs? JSON.parse(localStorage.msgs):[],
        }

    },
    methods:{
        send_msg(){
            let msg = this.msg;
            if (msg){
                this.isShow=true
                this.msg_list.push(this.msg);
                localStorage.msgs = JSON.stringify(this.msg_list);
                this.msg="";
            }
            // localStorage.clear()
        },
        del(index,msg_list){
            msg_list.splice(index,1)
            localStorage.msgs = JSON.stringify(msg_list)
            if (msg_list.length==0){
                this.isShow=false
            }
        },
        del_all(){
            this.msg_list=[]
            localStorage.removeItem('msgs')
            this.isShow=false


        }
    }


}
</script>

<style scoped>

</style>
