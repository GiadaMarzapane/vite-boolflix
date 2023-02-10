<script>
    import axios from 'axios';
    import SearchForm from "./SearchForm.vue";
    import { store } from '../store';


    export default {
        name: 'AppHeader',
        components: {
            SearchForm
        },
        data() {
            return{
                store
            }
        },
        methods:{
            officialResearch(){
                this.titleSearch('movie'),
                this.titleSearch('tv')
            },

            titleSearch(type){
                const mainUrl = 'https://api.themoviedb.org/3/search/'
                axios.get(mainUrl + type,{
                    params:{
                        api_key: '18d77260316140c9471d7a8a365ed4c7',
                        query: this.store.searchText,
                        language: 'it-IT'}
                    }
                )
                .then((response) => {
                    console.log('ricerca: ', this.store.searchText, response.data.results)
                    if (type == 'movie') {
                        this.store.movies = response.data.results
                    }
                    else{
                        this.store.series = response.data.results
                    }
                })
            }
        }
    }

</script>

<template>
    <section>
        <h1>BoolFlix</h1>
        <nav>
            <ul>
                <li><a href="#">Originali Boolflix</a></li>
                <li><a href="#">Film</a></li>
                <li><a href="#">Serie TV</a></li>
                <li><a href="#">Premiati</a></li>
                <li><a href="#">La mia Lista</a></li>
            </ul>
        </nav>
        <SearchForm @search="officialResearch"/>
    </section>
</template>

<style lang="scss" scoped>
@use "../style/style.scss" as *;

section{
        @include display-flex-rule;
        justify-content: flex-start;
        align-items: center;
        height: 10vh;
        background-color: rgb(15, 15, 15);
        padding:  0 20px;

        h1{
            color: #EC2724;
            margin-right: 20px;
        }
        nav{
            flex-grow: 1;
            & ul {
                display: flex;
                list-style-type: none;
                text-align: start;
                li{
                    padding: 5px 15px;
                    a{
                        text-decoration: none;
                        color: white;
                        font-size: 0.8rem;
                    }
                    &:hover a{
                        text-decoration: underline;
                    }
                }
            }
        }
    }
</style>