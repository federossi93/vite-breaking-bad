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
          //console.log(response);
          this.store.name = response.data
          this.store.lunghezza = response.data.length
          // this.store.personaggio = response.data
          // creo e aggiungo una nuova proprietà
        })
    },
    AllSeries() {
      console.log("click su All");
      this.callApi(this.store.API_URL)
    },
    brakingBad() {
      console.log("click su breking bad");
      this.callApi(`${this.store.API_URL}?category=Breaking+Bad`)
      
    },
    batterCallSaul() {
      console.log("click su batter call saul");
      this.callApi(`${this.store.API_URL}?category=Better+Call+Saul`)
    },

  },

  mounted() {
    this.callApi(this.store.API_URL)
  }

}

</script>

<template>

  <AppHeader />
  <AppMain @batterCallSaul="batterCallSaul" @brakingBad="brakingBad" @AllSeries="AllSeries"/>
  <AppFooter />

</template>

<style>
body {
  background-color: rgb(47, 47, 49);
}
</style>
