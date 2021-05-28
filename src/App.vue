<template>
<!-- Este repositorio contiene el proyecto que desarrolla el segundo punto de la prueba técnica de Servex S.A.C para los aprendices de desarrollo de software. Esta prueba evalua las habilidades técnicas frente a diferentes problemas que se pueden aplicar al mundo real del software. Esta prueba está diseñada de acuerdo a un perfil previamente analizado por parte de la organización.

El proyecto consume una API de los personajes de Rick & morty. Este API contiene personajes listados con ID del 1 al 671 API Rick & Morty, Se filtrar y presentan los primeros 20 IDs de la base de datos proporcionados por la API.

Algunas condiciones para los estados de los personajes son:

Cada personaje tiene una tarjeta unica con una imagen, su nombre, status(Alived o Dead) y la especia a la que pertenece el personaje.
  - Si el status del personaje es "Dead", la imagen debe estar en escala de grises.
  - Si el status del peronaje es "Unknown" no se debe mostrar el personaje.
  - Si el status es "Alived" se muesta además un marcador verde en el costado derecho del estado del personje.
  - Si el status del personaje es "Dead" (además de mostrar al personaje en escala de grises) se muestra un marcador rojo en el costado derecho del estado del personaje
  - El personaje pierde la escala de grises cuando se realiza un hover para darle mas información visual de este mismo al usuario.
  - En el header hay un enlace para ir a la pagina oficial de la serie distribuida por adultswim rick & Motty -->
  <div id="app">

    <h1 class=titulo> <a target="_bkank" href="https://www.adultswim.com/streams/rick-and-morty"></a> </h1>
    <h2>Capsulas con información de los personajes</h2>

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
      <section v-if="errored" class="alerta">
        <p>---|Lo sentimos, no es posible obtener la información <br>en este momento, por favor intente nuevamente mas tarde|---</p>
          <img class="img" src="https://cdn.hobbyconsolas.com/sites/navi.axelspringer.es/public/media/image/2019/07/doofus-rick.png" >
      </section>

      <footer>
        <a target="_bkank" href="https://es.wikipedia.org/wiki/Rick_y_Morty">Wiki</a>
        <a target="_bkank" href="https://rickandmortyapi.com/about">API</a>
        <a target="_bkank" href="https://www.adultswim.com/streams/rick-and-morty">Episodios</a>
      </footer>
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
      errored: false,
      selectedStatusFilter: '',
      statusOptions: [
        { text: 'All', value: '' },
        { text: 'Alive', value: 'alive' },
        { text: 'Dead', value: 'dead' }
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
    })
    .catch(error => {alert('Revisa el enlace de requerimiento a la API\n\nMensaje para el usuario:\nLAMENTAMOS LOS INCONVENIENTES :(\nEn este momento tenemos algunos problemas para obtener los datos\n\n\n' + error)
    this.errored = true}) 
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
  background-position: bottom;
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
h1 a{
  width: 100vw;
  height: 25vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.alerta{
  font-size: 2rem;
  flex-direction: column;
  display: flex;
  justify-content: center;
  align-content: center;
  /* text-align: center; */
  color:rgb(155, 155, 155);
  font-weight: bold;
  margin: 9rem 0 0 0;
}
.alerta img{
  width: 50vw;
  margin: 3rem auto;
  border-radius: 4rem;
}

.card{
  display: flex;
	height:300px;
	border-radius:10.5rem;
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
footer{
  height: 20vh;
  width: 100vw;
  display: flex;
  justify-content: space-around;
  align-items: center;
background: rgb(7,10,19);
background: radial-gradient(circle, rgba(7,10,19,1) 10%, rgba(38,44,58,1) 67%);
}
footer a{
  text-decoration: none;
  font-size: 2rem;
  color:rgba(255, 255, 255, 0.605);
  transition: all ease 0.3s;
}
footer a:hover{
  transform: scale(1.2);
  color: #84CA3B;
  text-decoration: overline;
}
/* ------------ Responsive */
@media(max-width: 700px) {
#app {
    background-position: bottom;
    background-attachment: fixed;
    background-size: 49rem 34rem;;
    text-align: center;
    }

#app h1, #app h2, #app h3{
  text-align: center;
  color: rgba(255, 255, 255);
  /* margin: 0; */
}
#app .card:hover{
  cursor: default;
  transform: scale(1);  
}
#app h1:hover{
  cursor: pointer;
  transform: scale(1);
}
.card{
  flex-direction: column;
  border-radius: 10.5rem;
  height: auto;
}
.card-content{
  height: 36vh;
}
}
</style>
