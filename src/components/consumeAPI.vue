<template>
    <div class="API" id="consumeAPI">
        <h1>Consume la API de Rick and Morty</h1>
        <p>{{x}}</p>
        
    </div>
</template>
<script>
    export default{
        name:'consumeAPI',
        datos(){
            return{
                consumeAPI: fetch ("https://rickandmortyapi.com/api/character").then((response)=>response.json()),
                x: console.log(fetch ("https://rickandmortyapi.com/api/character").then((response)=>response.json()))                
                }
        }
        }
    
    
</script>