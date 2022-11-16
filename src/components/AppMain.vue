<script>
    import {state} from "../state.js"
    export default {
        name: "AppMain",
        data() {
            return{
                state
            }
        },
        mounted(){
            console.log(this.state.prova)
        },
        computed: {
            
        }
    }
</script>

<template>
    <div class="container">
        <div class="row">
            <div class="col-3 movie-card my-2" v-for="(entry,i) in state.entries">
                <img class="movie-img" :src="state.path+entry.poster_path" :alt="entry.title">
                <div class="movie-info bg-dark text-white text-center">
                    <p><span class="movie-property">Titolo:</span> {{entry.title}}</p>
                    <p><span class="movie-property">Titolo originale:</span> {{entry.original_title}}</p>
                    <div>
                        <p class="movie-property">Lingua: <span class="language">{{entry.original_language}}</span></p>
                        <img :src="state.imgPath+'/'+entry.original_language+'.png'" alt="" class="lang-flag">
                    </div>
                    <p class="movie-rating">PLACEHOLDER</p>
                </div>
            </div>

        </div>
    </div>
        
</template>