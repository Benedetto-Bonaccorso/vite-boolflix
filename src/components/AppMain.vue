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
            <div class="col-6 col-md-3 movie-card my-2" v-for="(entry,i) in state.entries">

                <img class="movie-img" v-if="entry.poster_path != null" :src="state.path+entry.poster_path" :alt="entry.title">
                <img class="movie-img" v-else src="https://picsum.photos/id/237/300/450" :alt="entry.title">

                <div class="movie-info bg-dark text-white text-center">
                    <p v-if="state.searchCategory == 'movie'"><span class="movie-property">Titolo:</span> {{entry.title}}</p>
                    <p v-if="state.searchCategory == 'tv'"><span class="movie-property">Titolo:</span> {{entry.name}}</p>
                    
                    <p v-if="state.searchCategory == 'movie'"><span class="movie-property">Titolo originale:</span> {{entry.original_title}}</p>
                    <p v-if="state.searchCategory == 'tv'"><span class="movie-property">Titolo originale:</span> {{entry.original_name}}</p>
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
                    <p><span class="movie-property">OverView:</span> {{entry.overview}}</p>
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
        padding: 0.5rem 1rem;
    }

    .movie-img,
    .movie-info{
        border: 1px solid white;
        height: 50vh;
        overflow-x: hidden;
        overflow-y: auto;

        .language{
            text-transform: uppercase;
        }
        .lang-flag{
            width: 2.5rem;
            display: block;
            margin: 1rem auto;
        }
    }

    @media (min-width: 768px) { 

    }
</style>