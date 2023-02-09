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
    @use "./style/style.scss" as *
</style>
