<template>
<div class="test">
    
        <div v-if="showName">
            <p>{{ msg }}</p>
        </div>

   
    <div v-else>
        <ul>
            <!-- <li v-for="task in tasks">{{task.title}}</li> -->
        </ul>

        <hr>

        <div>
            <input type="text" v-model="user.firsName">
            <button type="button" v-on:click="saludar(user.firsName)">
                CLICK ME!
            </button>
            <hr>
            <input type="text" v-on:keyup.enter="typedEnter">
        </div>
    </div>

</div>
</template>

<script>
 export default {
     data(){
         return{
             title: 'Hola Mundo Vuejs',
             user:{
                 firsName: 'Ryan', 
                 lastName: 'McMillan'
             },
             myHtml: '<h3>hola vue</h3>',
             showName: true,
             tasks:[
                 {title: 'eat'},
                 {title: 'dinner'},
                 {title: 'play'},
                 {title: 'task'}
             ]
         }
     },
     methods: {
        saludar(name){
        alert('hello ' + name)
        },
        typedEnter (e) {
            console.log('Dio un enter');
        }
     },
     computed: {
         fullName() {
             return this.user.firsName + ' ' + this.user.lastName;
         }
     },
     props:{
         msg:{
             type: String,
             default: 'Mje por defecto'
         }
     }
 }
</script>

<style media="screen">
.test{
    background-color: #eee;
    padding: 1em;
}

</style>