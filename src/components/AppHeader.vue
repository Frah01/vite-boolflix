<script>
export default {
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
    <div>
        <div class="container" >
            <div class="row">
            <div class="input-group mb-3">
                <input type="text" class="form-control" placeholder="Ricerca il film" aria-label="Ricerca il film" v-model="inputText" @keyup.enter="search(inputText)">
                <button class="btn btn-outline-secondary" type="button" @click="search(inputText)">Cerca</button>
            </div>
        </div>
        </div>
    </div>
</template>
<style lang="">
    
</style>