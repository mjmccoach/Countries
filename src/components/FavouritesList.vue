<template>
  <div class="favourites-list">
    <h1>Favourites List</h1>
    <ul>
        <li v-for="favouriteCountry in favouriteCountries" :key="favouriteCountry.alpha3Code"> {{ favouriteCountry.name }}</li>
    </ul>

  </div>
</template>

<script>
export default {
    props : ['favouriteCountries']
}
</script>

<style>

</style>

module.exports FavouritesList