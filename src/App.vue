<template>
  <div id="app">
    <!-- <header> </header> -->
    <!-- <body></body> -->
    <h1 class=titulo>Rick & Morty</h1>
    <h2>Información de los personajes</h2>
    <button v-on:click="fetch"> click para concerlos</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  dependecies: axios,
  methods:{
  fetch(){
    // console.log('holi')
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
#app button{
  padding: 1rem;
  border: none;
  color:#2c3e50;
  border-radius: 1rem;
  transition: all ease 0.3s;
  background-color: rgba(255, 255, 255, 0.496);
}
#app button:hover{
  cursor: pointer;
  transform: scale(1.1);
  font-weight: bold;
}
</style>
