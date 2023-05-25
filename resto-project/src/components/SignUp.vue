<template>
    <img class="logo" src="../assets/resto-logo.png">
    <h1>Sign Up</h1>
    <div class="register">
        <input type="text" v-model="name" placeholder="Enter your name">
        <input type="text" v-model="email" placeholder="Enter your email">
        <input type="password" v-model="password" placeholder="Enter your password">
        <button v-on:click="signUp">Sign up</button>
        <p>
            <router-link to="/login">If you've already got an account, click me !</router-link>
        </p>
    </div>
</template>
<script>
import axios from "axios"
export default{
    name:"SignUp",
    data(){
        return{
            name:"",
            email:"",
            password:""
        }
    },
    methods:{
        async signUp(){
            let result = await axios.post("http://localhost:3000/users",{
                email:this.email,
                password:this.password,
                name:this.name 
            });

            console.warn(result);
            if(result.status===201){
                localStorage.setItem("user-info", JSON.stringify(result.data))
                this.$router.push({name:"HomePage"})
            }else alert("There was an error while signing up !")
        }
    },

    mounted(){//empêche l'utilisateur d'aller aux pages login/sign up s'il est déjà connecté, ça le redirige vers HomePage
        let user = localStorage.getItem("user-info")
        if(user){
            this.$router.push({name:"HomePage"})
        }
    }
}
</script>

<style>

</style>