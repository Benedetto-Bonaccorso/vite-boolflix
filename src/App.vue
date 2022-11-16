<script>
import axios from 'axios'
import { state } from './state.js'
import AppMain from "./components/AppMain.vue"
export default {
  name: 'App',
  components: {
    AppMain
  },
  data() {
    return {
      state
    }
  },
  methods: {
    
  },
  mounted() {
    axios.get(state.url)

      .then(response => {
          this.state.entries = response.data.results
          this.state.info = response.data.info
          console.log(response.data.results)
          console.log(this.state.entries)
      })
  }
}
</script>

<template>

  <h1>app</h1>
  <AppMain />

</template>

<style lang="scss" scoped>

</style>