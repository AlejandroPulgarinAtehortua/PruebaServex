<template>
  <div id="app">
    <!-- <header> </header> -->
    <!-- <body></body> -->
    <h1 class=titulo> consultar datos</h1>
    <button v-on:click="fetch"> consultar</button>
  </div>
</template>

<script>
import axios from 'axios'
// import header from './components/header.vue';
// import body from './components/body.vue'
export default {
  name: 'App',
  dependecies: axios,
  methods:{
  fetch(){
    console.log('holi')
    console.log(result)
    var result = axios
      .get("https://rickandmortyapi.com/api/character")
     
      .then((res) => {
      console.log(res.data)
    })
    .catch(err => {
      console.log(err);
    });
  }
}
}
 
</script>

<style>
#app {
  /* background-image: url('./assets/image.jpg'); */
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
