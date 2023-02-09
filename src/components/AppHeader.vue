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
            titleSearch(){
                axios.get('https://api.themoviedb.org/3/search/movie',{
                    params:{
                        api_key: '18d77260316140c9471d7a8a365ed4c7',
                        query: this.store.searchText,
                        language: 'it-IT'}
                    }
                )
                .then((response) => {
                    console.log('ricerca: ', this.store.searchText, response.data.results)
                    this.store.movies = response.data.results
                })
            }
        }
    }

</script>

<template>
    <h1>BoolFlix</h1>
    <SearchForm @search="titleSearch"/>
</template>

<style lang="scss">

</style>