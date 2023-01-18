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
   <AppSearch />
</template>
<style lang="">
    
</style>