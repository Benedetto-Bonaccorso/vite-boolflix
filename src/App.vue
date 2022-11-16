<script>
import axios from 'axios'
import { state } from './state.js'
import AppMain from "./components/AppMain.vue"
import AppHeader from "./components/AppHeader.vue"
export default {
  name: 'App',
  components: {
    AppMain,
    AppHeader,
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

  <AppHeader />
  <AppMain />

</template>

<style lang="scss" scoped>

</style>