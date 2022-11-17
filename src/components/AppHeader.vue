<script>
import axios from 'axios';
import { state } from '../state.js';
    export default{
        name: "AppHeader",
        data(){
            return{
                state
            }
        },
        methods: {
            search(){
                this.state.url = `https://api.themoviedb.org/3/search/${this.state.searchCategory}?api_key=e99307154c6dfb0b4750f6603256716d&query=${this.state.searchText}`
                this.state.searchText = ""

                axios.get(this.state.url)
                .then(response => {
                    this.state.entries = response.data.results
                    this.state.info = response.data.info
                    console.log(response.data.results)
                    console.log(this.state.entries)
                })
            },
            log(){
                console.log(this.state.searchCategory)
            }
        }
    }
</script>

<template>
    <div class="headerWrapper d-flex justify-content-between mx-5 my-4">
        <h1 class="title text-white">BoolFlix</h1>
        <div class="searchbar p-2">
            <input type="text" placeholder="Search" v-model="state.searchText" v-on:keydown.enter="log()">
            <button class="px-2" v-on:click="search()"><i class="fa-solid fa-magnifying-glass"></i></button>
            
            <select v-model="state.searchCategory" @change="log()">
                <option value="movie" v-on:click="category = 'movie'">Movies</option>
                <option value="tv" v-on:click="category = 'tv'">Tv Series</option>
            </select>

        </div>
    </div>
</template>