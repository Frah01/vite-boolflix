<script>
import { store } from '../store'
import axios from 'axios'
export default {
    data(){
        return{
            store,
            inputText: '',
        }
    },
    methods: {
        search(input) {
            let apiMovie = store.apiMovie + input;
            axios.get(apiMovie).then((response) => {
                store.movieArray = response.data.results
            })
        }
    }
}
</script>
<template lang="">
    <div class="container-header" >
            <div class="row ">
                <div class ="col">
                    <div class="d-flex align-items-center justify-content-between">
                        <div class="titolo">
                            <h3>BOOLFLIX</h3>
                        </div>
                        <div class=" my-3">
                            <input type="text" class="input-search" placeholder="Film, serie" aria-label="Film, serie" v-model="inputText" @keyup.enter="search(inputText)">
                            <button class="btn" type="button" @click="search(inputText)"><i class="fa-solid fa-magnifying-glass"></i></button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
</template>
<style lang="scss">
    @use '../styles/partials/mixins' as*;

    .input-search{
        @include input-search
    }

    .fa-magnifying-glass{
        color: white;
    }

    .titolo{
        color: red;
        h3{
            margin-bottom: 0;
        }
    }

    .container-header{
        width: 97%;
        margin: 0 auto;
    }
</style>