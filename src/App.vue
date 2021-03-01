<template>
  <div id="app">

    <label for="country_select">Select a Country:</label>
    <select id="country_select" v-model="selectedCountry">
      <option v-for="country in countries" :key="country.alpha3Code" :value="country">{{ country.name }}</option>
    </select>

    <button v-on:click="addToFavourites">
      Add to Favourites
    </button>

    <country-detail v-if="selectedCountry" :selectedCountry="selectedCountry"/>

    <favourites-list :favouriteCountries="favouriteCountries"/>
  </div>
</template>

<script>
import CountryDetail from './components/CountryDetail.vue';
import FavouritesList from './components/FavouritesList.vue';


export default {
  name: 'App',
  components: {
    CountryDetail : CountryDetail,
    'favourites-list': FavouritesList
  },
  data() {
    return {
      countries: [],
      selectedCountry: null,
      favouriteCountries: []
    }
  },
  mounted() {
    this.getCountries()
  },
  methods: {
    getCountries: function() {
      fetch('https://restcountries.eu/rest/v2/all')
      .then(res => res.json())
      .then(countries => this.countries = countries);
    },
    addToFavourites: function() {
      this.favouriteCountries.push(this.selectedCountry)
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
