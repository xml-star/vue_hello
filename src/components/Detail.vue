<template>
    <div>
        <span>这是详情页面{{$route.params.id}}</span>
        <table border="2">
            <tr>
                <td>id</td>
                <td>name</td>
                <td>age</td>
                <td>bir</td>
            </tr>
            <tr>
                <td>{{id}}</td>
                <td>{{name}}</td>
                <td>{{age}}</td>
                <td>{{bir}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    name: "Detail",
    data(){
        return{
            name:'',
            age:'',
            bir:'',
            id:this.$route.params.id,
        }
    },
    created() {
        let id=this.$route.params.id;
        let users=JSON.parse(localStorage.users)
        for(let i=0;i<users.length;i++){
            if(users[i].id==id){
                this.name=users[i].name
                this.age=users[i].age
                this.bir=users[i].bir
            }
        }



    }

}
</script>

<style scoped>

</style>
