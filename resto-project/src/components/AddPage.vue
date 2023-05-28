<template>
    <HeaderElem />
    <h1>Hello User, Welcome on Add Restaurant Page</h1>
    <form class="add">
        <input type="text" name="name" placeholder="Enter a restaurant name !" v-model="Restaurant.name">
        <input type="text" name="address" placeholder="Enter their address !" v-model="Restaurant.address">
        <input type="text" name="contact" placeholder="Enter their contact !" v-model="Restaurant.contact">
        <button type="button" v-on:click="addRestaurant">Add new restaurant</button>
    </form>
</template>

<script>
import HeaderElem from "./HeaderElem.vue"
import axios from "axios"
export default{
    name:"AddPage",
    components:{
        HeaderElem
    },
    data(){
        return{
            Restaurant:{
                name:"",
                address:"",
                contact:"",
            }
        }
    },
    methods:{
        async addRestaurant(){
            const result = await axios.post("http://localhost:3000/restaurants",{
                name:this.Restaurant.name,
                address:this.Restaurant.address,
                contact:this.Restaurant.contact,
            })
            if(result.status === 201){
                this.$router.push({name:"HomePage"})
            }
        }
    },
    mounted(){ //empêche l'utilisateur d'aller sur la page HomePage s'il n'est pas connecté
        let user = localStorage.getItem("user-info")
        if(!user){
            this.$router.push({name:"SignUp"})
        }
    }
}

</script>