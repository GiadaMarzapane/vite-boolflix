<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

export default {
    name: 'App',
    components: {
        AppHeader,
        AppMain,
    },
    data() {
        return {

        }
    }
}
</script>

<template>

    <AppHeader />
    <AppMain />

</template>

<style lang="scss">
@use "./style/style.scss" as *;
@import url('https://fonts.googleapis.com/css2?family=Coming+Soon&family=Raleway:wght@400;600&display=swap');
body{
    font-family: 'Raleway', sans-serif;
}
</style>
