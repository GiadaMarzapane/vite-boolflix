<script>
import { store } from '../store';
    
    export default{
    name: 'AppMain',
    data() {
        return {
            store,
            // classFlag: ''
        }
    },
    methods:{
        setFlag(lang){
            let classflag = '';
            if (lang == 'en') {
                return classflag = 'gb'
            }
            else if(lang == 'ja'){
                return classflag = 'jp'
            }
            else if (lang == 'ko') {
                return classflag = 'kn'
            }
            else if (lang == 'zh') {
                return classflag = 'cn'
            }
            return classflag = lang
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
            {{  }}
            <span :class="'fi fi-' + setFlag(element.original_language)"></span>
        </li>
        <li> <strong>Voto: </strong>{{ element.vote_average }}</li>
    </ul>
    <hr>
    <h4>SERIE TV</h4>
    <ul v-for="elementB in store.series">
        <li> <strong>Titolo: </strong>{{ elementB.name }}</li>
        <li> <strong>Titolo originale: </strong>{{ elementB.original_name }} </li>
        <li> <strong>Lingua: </strong>
            <span :class="'fi fi-' + setFlag(elementB.original_language)"></span>
        </li>
        <li> <strong>Voto: </strong>{{ elementB.vote_average }}</li>
    </ul>
</template>

<style lang="scss">
@use "../style/style.scss"
</style>