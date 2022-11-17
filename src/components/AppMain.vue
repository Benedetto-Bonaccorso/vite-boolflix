<script>
    import {state} from "../state.js"
    export default {
        name: "AppMain",
        data() {
            return{
                state
            }
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
                    <div class="movie-rating d-flex justify-content-center">
                        <p v-for="index in Math.round(entry.vote_average / 2)">
                            <i class="fa-solid fa-star"></i>
                        </p> 
                        <p v-for="index in 5-Math.round(entry.vote_average / 2)">
                            <i class="fa-regular fa-star"></i>
                        </p>
                    </div>
                    <p><span class="movie-property">Titolo:</span> {{entry.overview}}</p>
                </div>
            </div>

        </div>
    </div>
        
</template>

<style lang="scss" scoped>
        
    .movie-card:not(:hover)>.movie-info{
        display: none;
    }

    .movie-card:hover>.movie-img{
        display: none;
    }


    .movie-info>*{
        margin: 1rem;
    }

    .movie-img{

    }

    .movie-img,
    .movie-info{
        border: 2px solid black;
        height: 30vw;
        width: 18vw;
        margin-bottom: auto;
        overflow: auto;

        .language{
            text-transform: uppercase;
        }
        .lang-flag{
            width: 2.5rem;
            display: block;
            margin: 1rem auto;
        }
    }
</style>