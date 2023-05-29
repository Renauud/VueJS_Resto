<template>
    <HeaderElem />
    <h1>Hello User, Welcome on the Update Restaurant Page</h1>
    <form class="add">
        <input type="text" name="name" placeholder="Enter a restaurant name !" v-model="Restaurant.name">
        <input type="text" name="address" placeholder="Enter their address !" v-model="Restaurant.address">
        <input type="text" name="contact" placeholder="Enter their contact !" v-model="Restaurant.contact">
        <button type="button" v-on:click="updateRestaurant">Update the restaurant</button>
    </form>
</template>

<script>
import HeaderElem from "./HeaderElem.vue"
import axios from "axios"
export default{
    name:"UpdatePage",
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
        async updateRestaurant()
        {
            const result = await axios.put("http://localhost:3000/restaurants/"+this.$route.params.id,{
                name:this.Restaurant.name,
                address:this.Restaurant.address,
                contact:this.Restaurant.contact,
            })
            if(result.status === 200){
                this.$router.push({name:"HomePage"})
            }
        }
    },
    async mounted(){ //empêche l'utilisateur d'aller sur la page HomePage s'il n'est pas connecté
        let user = localStorage.getItem("user-info")
        if(!user){
            this.$router.push({name:"SignUp"})
        }
        const result = await axios.get("http://localhost:3000/restaurants/" + this.$route.params.id)
        console.warn(result.data);
        this.Restaurant = result.data;
    },
}

</script>