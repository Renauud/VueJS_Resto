<template>
    <HeaderElem />
    <h1>Hello {{name}}, Welcome on Home Page</h1>
</template>

<script>
import HeaderElem from "./HeaderElem.vue"
export default{
    name:"HomePage",
    data(){ // ?
        return{
            name:''
        }
    },
    components:{
        HeaderElem
    },
    mounted(){ //empêche l'utilisateur d'aller sur la page HomePage s'il n'est pas connecté
        let user = localStorage.getItem("user-info")
        this.name = JSON.parse(user).name // ?
        if(!user){
            this.$router.push({name:"SignUp"})
        }
    }
}

</script>