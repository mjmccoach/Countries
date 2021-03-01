<template>
  <div id="app">
    <country-detail/>
    <favourites-list/>
  </div>
</template>

<script>
import CountryDetail from './components/CountryDetail.vue';
import FavouritesList from './components/FavouritesList.vue';


export default {
  name: 'App',
  components: {
    CountryDetail : CountryDetail,
    FavouritesList: FavouritesList
  },
  data() {
    return {
      countries: []
    }
  },
  methods: {
    getCountries: function() {
      fetch('https://restcountries.eu/rest/v2/all')
      .then(res => res.json())
      .then(countries => this.countries = countries);
    }
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
  margin-top: 60px;
}
</style>
