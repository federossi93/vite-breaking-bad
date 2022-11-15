<script>
import { store } from '../store.js'

export default {
  name: "AppMain",
  data() {
    return {
      store
    }
  },

}

</script>

<template>

  <main>
    <h1 class="text-light p-3">Braking Bad Api</h1>

    <div class="container py-5">
      <select class="form-select" @change="$emit('AllSeries')">
        <option value="All characters">AllSeries</option>
        <option value="Breaking+Bad">brakingBad</option>
        <option value="Better+Call+Saul">batterCallSaul</option>
      </select>
    </div>
  </main>


  <main>
    <div class="container p-4  bg-light">

      <div class="  mt-5 p-2 bg-dark ">
        <h5 class="text-light">Found {{ store.lunghezza }} caracters</h5>
      </div>

      <div class="row row-cols-5">
        <div class="col text-center p-2 text-light" v-for="personaggio in store.name">
          <div class="p-3 bg-dark card cards">
            <img :src="personaggio.img" alt="">
            <h3>{{ personaggio.name }}</h3>
            <h4>{{ personaggio.category }}</h4>
            <h5>{{ personaggio.status }}</h5>
          </div>
        </div>
      </div>
    </div>
  </main>

</template>

<style lang="scss" scoped>
.cards {
  height: 550px;

  img {
    width: 200px;
    height: 300px;
    object-fit: cover;
  }

  h3 {
    margin-top: 1rem;
  }

}
</style>
