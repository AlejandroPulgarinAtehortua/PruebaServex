<template>
    <div class="API" id="consumeAPI">
        <h2>otra cosa cualquiera</h2>
    </div>
</template>
<script>
    import axios from "axios"
    export default {
        name: 'body',
        created() {
            axios.get("https://rickandmortyapi.com/api/character").then((result) => {
            console.log(result.data);
        })
    }
    };


</script>