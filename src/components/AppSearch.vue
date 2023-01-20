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
                            <ul>
                                <li >
                                    <a href="">Home</a>
                                    <div class="selezione" ></div>
                                </li>
                                <li>
                                    <a href="">Serie Tv</a>
                                    <div class="selezione" ></div>
                                </li>
                                <li>
                                    <a href="">Film</a>
                                    <div class="selezione" ></div>
                                </li>
                                <li>
                                    <a href="">Nuove Uscite</a>
                                    <div class="selezione" ></div>
                                </li>
                            </ul>
                        </div>
                        <div class=" my-3">
                            <div class="search-box">
                                <button class="btnn-search"  @click="search(inputText)"><i class="fas fa-search"></i></button>
                                <input type="text" class="input-search" placeholder="Film, serie" aria-label="Film, serie" v-model="inputText" @keyup.enter="search(inputText)">
                            </div>
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

    .fa-bell {
        cursor: pointer;
    }

    .selezione {
        width: 1%;
        height: 5px;
        margin: 0 auto;
        transition: 0.3s ease-in-out;
        
    }

    li:hover .selezione{
        width: 60%;
        height: 3px;
        background-color: red;
        border-radius: 1px;
    }
    li:focus .selezione{
        width: 30px;
    }

    .titolo{
        height: 100%;
        color: red;
        display: flex;
        align-items: center;
        h3{
            margin-bottom: 0;
        }
        ul{
            list-style-type: none;
            display: flex;
            margin-bottom: 0;
            padding: 0;
            
            li{
                margin-left: 20px;
                a{
                text-decoration: none;
                color: rgb(255, 255, 255);
            }
               
            }

           
        }
    }

    .container-header{
        width: 97%;
        margin: 0 auto;
    }


    .search-box{
  width: fit-content;
  height: fit-content;
  position: relative;
}
.input-search{
  height: 40px;
  width: 40px;
  border-style: none;
  font-size: 18px;
  letter-spacing: 2px;
  outline: none;
  border-radius: 25px;
  transition: all .5s ease-in-out;
  padding-right: 40px;
  color:#fff;
}
.input-search::placeholder{
  color:rgba(255,255,255,.5);
  font-size: 18px;
  letter-spacing: 2px;
  font-weight: 100;
}
.btnn-search{
  width: 40px;
  height: 40px;
  border-style: none;
  font-size: 20px;
  font-weight: bold;
  outline: none;
  cursor: pointer;
  border-radius: 50%;
  position: absolute;
  right: 0px;
  color:#ffffff ;
  background-color:transparent;
  pointer-events: painted;  
}
.btnn-search:focus ~ .input-search{
  width: 300px;
  border-radius: 0px;
  background-color: transparent;
  border-bottom:1px solid rgba(255,255,255,.5);
  transition: all 500ms cubic-bezier(0, 0.110, 0.35, 2);
}
.input-search:focus{
  width: 300px;
  border-radius: 0px;
  background-color: transparent;
  border-bottom:1px solid rgba(255,255,255,.5);
  transition: all 500ms cubic-bezier(0, 0.110, 0.35, 2);
}

</style>