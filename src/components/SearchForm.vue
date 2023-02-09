<script>
import { store } from '../store';
    
    export default{
        name: 'SarchForm',
        data(){
            return{
                store
            }
        }
    }

</script>

<template>

    <div>
        <input type="text" placeholder="Effettua la tua ricerca..." v-model="store.searchText">
        <button type="button" @click="$emit('search')">Cerca</button>
    </div>

</template>

<style lang="scss">
</style>