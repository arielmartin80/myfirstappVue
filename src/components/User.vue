<template>
    <div class="users">
        <h1>User component</h1>
        <ul>
            <li v-for="user in users"  v-bind:key = "user.id">
                {{user.id}} - {{user.name}} - {{user.email}} - 
                <button v-on:click="deleteUser(user)">X</button>
            </li>
        </ul>
        <form v-on:submit.prevent="addUser">
            <input type="text" v-model="newUser.name" placeholder="Nombre">
            <input type="email" v-model="newUser.email" placeholder="Email">
            <button type="submit">Add</button>
        </form>
    </div>
</template>
    
<script>
export default{
    data(){
        return{
            users:[
 
            ],
            newUser: {}
         
        }
    },
    methods:{
        addUser(e){
            e.preventDefault();
            this.users.push(this.newUser);
            this.newUser = {};
        },
        deleteUser(user){
            this.users.splice(this.users.indexOf(user),1);
        }
    },
    created(){
         this.$http.get('https://jsonplaceholder.typicode.com/users')
         .then(res => this.users = res.body);
    }
}
</script>
    
<style scoped>
    .users{
        background: #333;
        color:#fff;
        padding: 20px;
    }
</style>