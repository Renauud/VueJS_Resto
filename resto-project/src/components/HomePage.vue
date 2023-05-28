<template>
    <HeaderElem />
    <h1>Hello {{name}}, Welcome on Home Page</h1>
    <table border="1">

        <tr>
            <td>Id</td>
            <td>Name</td>
            <td>Contact</td>
            <td>Address</td>
        </tr>
        
        <tr v-for="item in restaurants" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.contact }}</td>
            <td>{{ item.address }}</td>
        </tr>
    </table>
</template>

<script>
import HeaderElem from "./HeaderElem.vue";
import axios from "axios";
export default{
    name:"HomePage",
    data(){ // ?
        return{
            name:'',
            restaurants:[],
        }
    },
    components:{
        HeaderElem
    },
    async mounted(){ //empêche l'utilisateur d'aller sur la page HomePage s'il n'est pas connecté
        let user = localStorage.getItem("user-info")
        this.name = JSON.parse(user)?.name // ?
        if(!user){
            this.$router.push({name:"SignUp"})
        }
        let result = await axios.get("http://localhost:3000/restaurants");
        this.restaurants = result.data;
    }
}

</script>

<style>
table{
    margin: auto;
}
td{
    width:180px;
    height: 30px;
}

</style>