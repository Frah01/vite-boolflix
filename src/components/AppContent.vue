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
        }
    },
   
   
}
</script>
<template lang="">
    <div class="container my-4">
        <div class="row row-cols-5 flex-nowrap">
            <AppCard v-for="(item, index) in store.movieArray" :key="index" :info="item" />
        </div>
    </div>
</template>
<style lang="scss" scoped>

.container{
    overflow-x: auto;
}

</style>