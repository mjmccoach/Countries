<template>
  <div class="selected-country">
        <h1> {{ selectedCountry.name }} </h1>
        <p> {{ selectedCountry.population }} </p>
  </div>
</template>

<script>
export default {
    props : ["selectedCountry"]

}
</script>

<style>

</style>

module.exports CountryDetail;