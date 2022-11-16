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
        }
    }
</script>

<template>

    <div class="container">
        <div class="row">

            <h1>AppMain</h1>
            <div class="col-2" v-for="entry in state.entries">
                {{entry.title}}
            </div>
            
        </div>
    </div>
        
</template>