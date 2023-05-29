<template>
    <div class="nav">
        <router-link to="/">Home</router-link>
        <router-link to="./add">Add Restaurant</router-link>
        <a href="#" v-on:click="logout">Log out</a>
    </div>
</template>

<script>
export default{
    name:"HeaderElem",
    methods:{
        logout(){
            localStorage.clear()
            this.$router.push({name:"LoginPage"})
        }
    }
}
</script>

<style>
.nav{
    background-color: #333;
    overflow: hidden;
}
.nav a{
    color: white;
    float: left;
    padding: 15px;
    margin-right: 8px;
    font-size: 19px;
    text-decoration: none;
}
.nav a:hover{
    background-color: #ddd;
    color: #333;
}
</style>