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
    <div class="main-container my-4">
        <div class="  mb-5 ">
                    <!-- {{ store.movieArray.length }} Risultati -->
                    <div class="categoria text-white">
                        <h3 >Film e Serie Tv</h3>
                    </div>
                </div>
                <div class=" cards-of row row-cols-5 flex-nowrap mt-5">
                    <AppCard v-for="(item, index) in store.movieArray" :key="index" :info="item" />
                </div>
            </div>
</template>
<style lang="scss" scoped>
.main-container{
    width: 100%;
    margin: 0 auto;
}

.categoria{
    width: 95%;
    margin: 0 auto;
}
.cards-of{
    overflow-x: auto;
    width: 95%;
    margin: 0 auto;

&::-webkit-scrollbar-track{   
    
	box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
	border-radius: 10px;
	background-color: #F5F5F5;

}

&::-webkit-scrollbar{

	height: 6px;
	background-color: #F5F5F5;
    border-radius: 10px;

}

&::-webkit-scrollbar-thumb{

	border-radius: 10px;
	box-shadow: inset 0 0 6px rgba(0,0,0,.3);
	background-color: #424242;
}
}

</style>