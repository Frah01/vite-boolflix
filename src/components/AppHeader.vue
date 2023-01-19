<script>
import { store } from '../store'
import AppSearch from './AppSearch.vue'
import axios from 'axios'
export default {
    components:{
        AppSearch,
    },
    data(){
        return{
            store,
            inputText: '',
        }
    },
}
</script>
<template lang="">
    <header>
        <AppSearch />
    </header>
</template>
<style lang="scss">
    header{
        width: 100%;
        height: 100px;
    } 
</style>