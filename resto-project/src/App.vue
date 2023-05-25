<template>
<router-view/>
</template>

<script>
export default {
  name: 'App',
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body{
  padding: 0;
  margin: 0;
}
.logo{
    width: 100px;
}
.register input, .login input{
    width: 300px;
    height: 30px;
    display: block;
    margin: 0 auto 30px auto;
    border: 1px solid lightblue;
}
.register button, .login button{
    width: 305px;
    height: 40px;
    background-color:lightblue;
    color: white;
    border: none;
    cursor:pointer;
}
</style>
