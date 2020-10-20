<template>
  <div id="app">
    <h1>COUNTRIES APP</h1>
    <label for="countries">Select Country</label>
    <select name="countries" id="countries" >
      <option v-for="(country, index) in countries" :key="index" :item="country">{{country.name}}</option>
    </select>
  </div>
</template>

<script>

 import selectedCountry from './components/selectedCountry.vue'

export default {  
  name: "App",
  data() {
    return {
      countries: []
    }
  },

  mounted () {
    this.fetchCountry()
  },

  methods: {
    fetchCountry: function () {
      fetch("https://restcountries.eu/rest/v2/all")
      .then((response) => response.json())
      .then((country) => this.countries = country);
    },

  },

  components: {
    'selected-country': selectedCountry
  }

  
}
</script>

<style>

</style>