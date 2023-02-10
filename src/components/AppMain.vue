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
            else if (lang == 'el') {
                return classflag = 'gr'
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
    <main>
        <section>
            <!-------- SECTION FILM -------->
            <div class="title-container">
                <div>
                    <h4>FILM</h4>
                </div>
            </div>
            <!-------- SECTION FILM CARD -------->
            <div class="my-container">
                <div v-for="element in store.movies" class="flip-card">
                    <div class="flip-card-inner">
                        <div class="flip-card-front">
                            <img :src="cover(element.poster_path)" :alt="element.original_title">
                        </div>
                        <div class="description flip-card-back">
                            <div>
                                <p>
                                    <strong>Titolo: </strong>
                                    <span class="caption">
                                        {{ element.title }}
                                    </span>
                                </p>
                            </div>
                            <div>
                                <p>
                                    <strong>Titolo originale: </strong>
                                    <span class="caption">
                                        {{ element.original_title }}
                                    </span>
                                </p>
                            </div>
                            <div>
                                <p>
                                    <strong>Lingua: </strong>
                                    <span class="caption" :class="'fi fi-' + setFlag(element.original_language)"></span>
                                </p>
                            </div>
                            <div>
                                <p>
                                    <strong>Voto: </strong>
                                    <span v-for="index in voteAndStar(element.vote_average)">
                                        <font-awesome-icon class="icon-star" icon="fa-solid fa-star" />
                                    </span>
                                    <span v-for="index in (5 - voteAndStar(element.vote_average))">
                                        <font-awesome-icon class="icon-star" icon="fa-regular fa-star" />
                                    </span>
                                </p>
                            </div>
                        </div>
                    </div>
                    
                </div>
            </div>
            <!-------- SECTION SERIE TV -------->
            <div class="title-container">
                <div>
                    <h4>SERIE TV</h4>
                </div>
            </div>
            <!-------- SECTION SERIE TV CARD -------->
            <div class="my-container">
                <div v-for="elementB in store.series" class="flip-card">
                    <div class="flip-card-inner">
                        <div class="flip-card-front">
                            <img :src="cover(elementB.poster_path)" :alt="elementB.original_title">
                        </div>
                        <div class="description flip-card-back">
                            <div>
                                <p>
                                    <strong>Titolo: </strong>
                                    <span class="caption">
                                        {{ elementB.name }}
                                    </span>
                                </p>
                            </div>
                            <div>
                                <p>
                                    <strong>Titolo originale: </strong>
                                    <span class="caption">
                                        {{ elementB.original_name }}
                                    </span>
                                </p>
                            </div>
                            <div>
                                <p>
                                    <strong>Lingua: </strong>
                                    <span class="caption" :class="'fi fi-' + setFlag(elementB.original_language)"></span>
                                </p>
                            </div>
                            <div>
                                <p>
                                    <strong>Voto: </strong>
                                    <span v-for="index in voteAndStar(elementB.vote_average)">
                                        <font-awesome-icon class="icon-star" icon="fa-solid fa-star" />
                                    </span>
                                    <span v-for="index in (5 - voteAndStar(elementB.vote_average))">
                                        <font-awesome-icon class="icon-star" icon="fa-regular fa-star" />
                                    </span>
                                </p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            </section>
            </main>
</template>

<style lang="scss" scoped>
@use "../style/style.scss" as *;
@use "../style/partials/cardHoverEffect.scss" as *;
@import url('https://fonts.googleapis.com/css2?family=Coming+Soon&family=Raleway:wght@400;600&display=swap');

    main{
        height: 90vh;
        overflow-y: auto;
        padding: 20px 0;
        background-color: lightgray;
    }
    .title-container{
        padding: 15px 0;
        color: white;
        background-color: black;
        margin: 15px 0;
        &>div{
            width: 90vw;
            margin: 0 auto;
        }
    }
    p{
        font-size: 0.8rem;
        line-height: 18px;
        margin-bottom: 10px;
    }
    .icon-star{
        color: goldenrod;
    }
    .my-container{
        width: 90vw;
        margin: 0 auto;
        @include display-flex-rule;
        flex-wrap: wrap;
    }
    div.description{
        top: 0;
        right: 0;
        max-width: 154px;
        background: black;
        color: white;
        padding: 5px 3px 0 5px;
    }
    .caption{
        font-family: 'Coming Soon', cursive;
    }
</style>