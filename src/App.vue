<script>
import { store } from './store.js'
import axios from "axios";

export default {
  name: "App",
  components: {
  },
  data() {
    return {
      store

    }
  },
  methods: {
    callApi(url) {
      axios.get(url)
        .then(response => {
          console.log(response);
          this.store.personaggi = response.data
        })
    }
  },
  mounted() {
    this.callApi(this.store.API_URL)
  }
}

</script>

<template>
  <div class="container">
    <div class="row row-cols-4">
      <div class="col" v-for="personaggio in store.personaggi">
        <img class="immagini" :src="personaggio.img" alt="">
        <h2 class="name">{{ personaggio.name }}</h2>
        <h3>{{ personaggio.category }}</h3>
        <h3>{{ personaggio.status }}</h3>
      </div>
    </div>
  </div>
</template>

<style scoped>
.immagini {
  width: 300px;
  height: 400px;
}
</style>
