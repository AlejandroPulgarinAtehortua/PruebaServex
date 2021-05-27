<template>
  <div id="app">

    <h1 class=titulo> </h1>
    <h2>Información de los personajes</h2>
    <!-- <button v-on:click="fetch"> click para concerlos</button> -->

    <div class="conteiner" v-for="character of characters" v-bind:key="character.id">
      <div class="card" :class="character.status === 'unknown' ? 'desconocido' : ''">
        <div class="card-header">
          <img class="img" v-bind:src="character.image" v-bind:alt="character.name" :class="character.status === 'Dead' ? 'gray-img' : ''">
        </div>
        <div class="card-content">
          <h3 class="title nombre">
            {{character.name}}
          </h3>
          <h3 class="title">Estado:
            {{character.status}} <span :class="character.status === 'Alive' ? 'span' : ''"></span>
            <span :class="character.status === 'Dead' ? 'dead' : ''"></span>
          </h3>
          <h3 class="title">Especie:
            {{character.species}}
          </h3>

        </div>
      </div>
    </div>

    <!-- <div v-for="character of characters" v-bind:key="character.id">
      {{character}}
    </div> -->

  </div>
</template>

<script>
import axios from 'axios'
export default {
   name: 'App',
  data: function (){
    return{
      characters: [],
      nameFilter: '',
      selectedStatusFilter: '',
      statusOptions: [
        { text: 'All', value: '' },
        { text: 'Alive', value: 'alive' },
        { text: 'Dead', value: 'dead' },
        // { text: 'Unknown', value: 'unknown' }
		],
		filtersApplied: [],
		timer: null
    };
  },
  created(){
    this.fetch()
  },
  dependecies: axios,
  methods:{
  fetch(){
    // console.log('holi')
    let x = this;
    axios.get('https://rickandmortyapi.com/api/character/1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20')
    .then(function(res) {
        x.characters = res.data;
        // console.log(res.data)
    })
  }
  }
}

 
</script>

<style>

::-webkit-scrollbar {
    display: none;
}
#app {
  background-image: url('https://fondosmil.com/fondo/27365.png');
  background-position: center;
  background-attachment: fixed;
  background-repeat: no-repeat;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;

}
.titulo{
  background-image: url('https://fontmeme.com/permalink/210527/413e64d5b86213148fed3db2d4e89ca1.png');
  background-position: center;
  background-attachment:scroll ;
  background-repeat: no-repeat;
  background-size:contain;
  height: 25vh;
  width: 100vw;
}
#app h1, #app h2, #app h3{
  text-align: center;
  color: rgba(255, 255, 255, 0.605);
  /* margin: 0; */
}

#app h1{
  font-size: 5rem;
  margin: 4rem auto 0 auto;
  transition: all ease-out 0.3s;
  width: 100vw;
  height: 30vh;
}
#app h1:hover{
  cursor: pointer;
  transform: scale(1.1);
}
#app h2{
  font-size: 2rem;
  margin: 0 0 5rem 0;
}





/* ------------------------- */
.conteiner{
  display: flex;
  justify-content: center;
  align-items: center;
}

.card{
  display: flex;
	height:300px;
	border-radius:2.5rem;
	overflow:hidden;
	margin-bottom:4.5rem;
	position:relative;
  justify-content: center;
  align-items: center;
  transition: all ease 0.3s;
}
#app .card:hover{
  cursor: pointer;
  transform: scale(1.2);
  -webkit-box-shadow: -5px 12px 15px 1px rgba(0, 0, 0, 0.653); 
  box-shadow: -5px 12px 15px 1px rgba(0, 0, 0, 0.633);
  border-radius: 4.5rem;
  
}
/* #app .card:hover .card-header img{
  width: 30vw;
  position: absolute;
} */
#app .card:hover h3{
  color: white;
}

/* .card:hover .card-content{
  font-size: 1.2rem;
} */
.card-content{
  max-width: 20rem;
}
.card-content{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background-color: rgba(0, 0, 0, 0.448);
  height: 100%;
  padding: 0 2rem;
  transition: all ease 0.3s;
  min-width: 25rem;
}
.nombre{
  font-size: 3rem;
  margin: 0 0 3rem 0;
}

/* -------------------------- */
.desconocido{
  display:none
}
#app .card:hover .card-header img{
  filter: drop-shadow(16px 16px 10px black) ;
}
.img{
  filter: drop-shadow(16px 16px 10px black);
}
.gray-img{
  filter: grayscale(100%) drop-shadow(16px 16px 10px black);
}
 .span{
    display: inline-block;
    width: 1rem;
    margin-right:0 0.375rem;
    background: rgb(85, 204, 68);
    /* background:red ; */
    border-radius: 50%;
    height: 1rem;
}
.dead{
    display: inline-block;
    width: 1rem;
    margin-right:0 0.375rem;
    /* background: rgb(85, 204, 68); */
    background:red ;
    border-radius: 50%;
    height: 1rem;;
}

</style>
