<script>
import { store } from '../store';
    
    export default{
    name: 'AppMain',
    data() {
        return {
            store,
            stars: 0
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
        },
        cover(posterpath){
            return `https://image.tmdb.org/t/p/w154${posterpath}`
        },
        voteAndStar(OldValue){
            let NewValue = (((OldValue - 1) * (5 - 1)) / (10 - 1)) + 1
            if (OldValue == 0) {
                console.log(typeof this.stars, this.stars)
                return this.stars = 0
            }
            console.log(this.stars)
            return this.stars = parseInt(NewValue.toFixed(0));
        }
    }
    }

</script>

<template>
    <h3> <em>La tua ricerca ha ottenuto i seguenti risultati:</em> </h3>
    <h4>FILM</h4>
    <ul v-for="element in store.movies">
        <li>
            <strong>Titolo: </strong>
            {{ element.title }}
        </li>
        <img :src="cover(element.poster_path)" :alt="element.original_title">
        <li>
            <strong>Titolo originale: </strong>
            {{ element.original_title }}
        </li>
        <li>
            <strong>Lingua: </strong>
            <span :class="'fi fi-' + setFlag(element.original_language)"></span>
        </li>
        <li>
            <strong>Voto: </strong>
            {{ element.vote_average }} // {{ voteAndStar(element.vote_average) }}
            <span v-for="index in voteAndStar(element.vote_average)">
                &#127765;
            </span>
            <span v-for="index in (5 - voteAndStar(element.vote_average))">
                &#127770;
            </span>
        </li>
    </ul>
    <hr>
    <h4>SERIE TV</h4>
    <ul v-for="elementB in store.series">
        <li> <strong>Titolo: </strong>{{ elementB.name }}</li>
        <img :src="cover(elementB.poster_path)" :alt="elementB.original_title">
        <li> <strong>Titolo originale: </strong>{{ elementB.original_name }} </li>
        <li> <strong>Lingua: </strong>
            <span :class="'fi fi-' + setFlag(elementB.original_language)"></span>
        </li>
        <li> <strong>Voto: </strong>{{ elementB.vote_average }} // {{ voteAndStar(elementB.vote_average) }}</li>
    </ul>
</template>

<style lang="scss">
@use "../style/style.scss"
</style>