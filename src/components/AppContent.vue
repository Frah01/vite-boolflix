<script>
import { store } from '../store';
import AppCard from './AppCard.vue'
import axios from 'axios';
export default {
    components: {
        AppCard,
    },
    name: 'AppMain',
    data() {
        return {
            store,
            inputText: '',
        }
    },
   
   
}
</script>
<template lang="">
    <div class="container my-4">
       
        <div class="mb-5 text-white">
             {{ store.movieArray.length }} Risultati
        </div>
        <div class="row row-cols-5 gap-5 justify-content-between">
            <AppCard v-for="(item, index) in store.movieArray" :key="index" :info="item" />
        </div>
    </div>
</template>
<style lang="scss" scoped>
</style>