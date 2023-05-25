<template>
    <HeaderElem />
    <h1>Hello User, Welcome on Update Restaurant Page</h1>
</template>

<script>
import HeaderElem from "./HeaderElem.vue"
export default{
    name:"UpdatePage",
    components:{
        HeaderElem
    },
    mounted(){ //empêche l'utilisateur d'aller sur la page HomePage s'il n'est pas connecté
        let user = localStorage.getItem("user-info")
        if(!user){
            this.$router.push({name:"SignUp"})
        }
    }
}

</script>