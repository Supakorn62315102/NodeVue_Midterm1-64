<template>
<div>
    <h1>เพิ่มรายชื่อ</h1>
    <form v-on:submit.prevent = "createUser">
        <p>ชื่อภาพยนตร์: <input type="text" v-model="user.name"></p>
        <p>-: <input type="text" v-model="user.lastname"></p>
        <p>รอบ Movie: <input type="text" v-model="user.email"></p>
        <p>เลขที่นั่ง: <input type="text" v-model="user.password"></p>
        
        <p><button type="submit">create user</button></p>
    </form>
    <hr>
    <div>
        <p>ชื่อภาพยนตร์: {{user.name}}</p>
        <p>-: {{user.lastname}}</p>
        <p>รอบ Movie: {{user.email}}</p>
        <p>เลขที่นั่ง: {{user.password}}</p>
    </div>
</div>
</template>
<script>
import UsersService from '@/services/UsersService'

export default {
    data(){
        return{
            user:{
                name: '',
                lastname: '',
                email: '',
                password: '',
                status: 'active'
            }
        }
    },
    methods:{
        async createUser(){
            try{
                await UsersService.post(this.user)
                this.$router.push({
                    name: 'users'
                })
            }catch(error){
                console.log(error)
            }
        }
    }    
}
</script>
<style scoped>


</style>