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
        let BetterCallSoul = `${this.store.API_URL}?category=${this.selected}`
        //let brakingBad = `${this.store.API_URL}?category=${this.selected}`
        this.callApi(BetterCallSoul)
        console.log(BetterCallSoul);
      } else if (this.selected == "Better+Call+Saul") {
        let BetterCallSoul2 = `${this.store.API_URL}?category=${this.selected}`
        //let BetterCall = `${this.store.API_URL}?category=${this.selected}`
        this.callApi(BetterCallSoul2)
        console.log(BetterCallSoul2);
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
  <AppMain @AllSeries="ciaoMio" />
  <AppFooter />

</template>

<style>
body {
  background-color: rgb(47, 47, 49);
}
</style>
