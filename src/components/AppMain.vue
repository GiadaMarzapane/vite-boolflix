<script>
import { store } from '../store';
    
    export default{
    name: 'AppMain',
    data() {
        return {
            store
        }
    }
    }

</script>

<template>
    <h3>La tua ricerca ha ottenuto i seguenti risultati:</h3>
    <ul v-for="element in store.movies">
        <li> <strong>Titolo:</strong>{{ element.title }}</li>
        <li><strong>Titolo originale:</strong>{{ element.original_title }}</li>
        <li> <strong>Lingua: </strong>{{ element.original_language }}</li>
        <li> <strong>Voto: </strong>{{ element.vote_average }}</li>
    </ul>
</template>

<style lang="scss">
</style>