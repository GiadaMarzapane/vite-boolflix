<script>
import { store } from '../store';
    
    export default{
    name: 'AppMain',
    data() {
        return {
            store,
            classFlag: ''
        }
    },
    methods:{
        setFlag(lang){
            this.classFlag = lang
            if (lang == 'en') {
                return this.classFlag = 'gb'
            }
            else if(lang == 'ja'){
                return this.classFlag = 'jp'
            }
        }
    }
    }

</script>

<template>
    <h3> <em>La tua ricerca ha ottenuto i seguenti risultati:</em> </h3>
    <h4>FILM</h4>
    <ul v-for="element in store.movies">
        <li> <strong>Titolo: </strong>{{ element.title }}</li>
        <li> <strong>Titolo originale: </strong>{{ element.original_title }}</li>
        <li> <strong>Lingua: </strong>
            {{ setFlag(element.original_language) }}
            <span :class="'fi fi-'+classFlag"></span>
        </li>
        <li> <strong>Voto: </strong>{{ element.vote_average }}</li>
    </ul>
    <hr>
    <h4>SERIE TV</h4>
    <ul v-for="elementB in store.series">
        <li> <strong>Titolo: </strong>{{ elementB.name }}</li>
        <li> <strong>Titolo originale: </strong>{{ elementB.original_name }} </li>
        <li> <strong>Lingua: </strong>{{ elementB.original_language }} </li>
        <li> <strong>Voto: </strong>{{ elementB.vote_average }}</li>
    </ul>
</template>

<style lang="scss">
@use "../style/style.scss"
</style>