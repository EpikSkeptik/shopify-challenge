<template>
  <NavMenu :header="header" :apiName="apiName"/>
  <div v-show="isLoading">
    <Loading/>
    <p>{{cards}}</p>
  </div>
  <div v-for="card in cards" :key="card.id">
    <Card :packet="card" />
  </div>
  
</template>

<script>
import Card from './components/Card.vue'
import Loading from './components/Loading.vue'
import NavMenu from './components/NavMenu.vue'

export default {
  name: 'App',
  components: {
    Card,
    Loading,
    NavMenu
  },
  data() {
    return {
      header: 'Spacestagram',
      apiName: 'NASA Mars Rover API',
      apiURL: `https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&page=1&api_key=${process.env.VUE_APP_NASAAPIKEY}`,
      cards: [],
      isLoading: true,
    }
  },
  mounted() {
      fetch(this.apiURL)
        .then(res => res.json())
        .then(data => this.cards = data.photos)
        .catch(err => console(err.message))

      this.isLoading = false;
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
