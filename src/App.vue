<script>
import { store } from './store.js'
import axios from "axios";
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';

export default {
  name: "App",

  components: {
    AppHeader,
    AppMain,
    AppFooter,
  },

  data() {
    return {
      store,
    }
  },

  methods: {
    callApi(url) {
      axios.get(url)
        .then(response => {
          this.store.name = response.data
          this.store.lunghezza = response.data.length
        })
    },
    ciaoMio() {
      this.selected = event.target.value
      console.log(this.selected);
      if (this.selected == "Breaking+Bad") {
        let brakingBad = `${this.store.API_URL}?category=${this.selected}`
        this.callApi(brakingBad)
        console.log(brakingBad);
      } else if (this.selected == "Better+Call+Saul") {
        let BetterCall = `${this.store.API_URL}?category=${this.selected}`
        this.callApi(BetterCall)
        console.log(BetterCall);
      } else {
        this.callApi(this.store.API_URL)
        console.log("ciao");
      }
    },
  },
  mounted() {
    this.callApi(this.store.API_URL)
  }
}

</script>

<template>

  <AppHeader />
  <AppMain @allSeries="ciaoMio" />
  <AppFooter />

</template>

<style>
body {
  background-color: rgb(47, 47, 49);
}
</style>
