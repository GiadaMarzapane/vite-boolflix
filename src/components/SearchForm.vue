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
        <input type="text" placeholder="Effettua la tua ricerca..." v-model="store.searchText" @keyup.enter="$emit('search')">
    </div>

</template>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Coming+Soon&family=Raleway:wght@400;600&display=swap');
    input{
        padding: 5px 10px;
        outline: none;
        border: none;
        border-radius: 10px;
        &::placeholder{
            font-family: 'Raleway', sans-serif;
        }
    }
    button{
        font-family: "Raleway", sans-serif;
        padding: 5px 10px;
        margin-left: 5px;
        border-radius: 0;
    }
</style>