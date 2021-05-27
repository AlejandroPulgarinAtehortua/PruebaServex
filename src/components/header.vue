<template>
    <div id="header">
        <h1>Consume la API de Rick and Morty</h1>
        <p>{{parrafo}}</p>
    </div>
</template>
<script>
    export default{
        name:'header',
        data(){
            return{
                parrafo: 'Esta pagina muestra los primeros 20 personajes de Rick and Morty'
        }
        }
    }

</script>