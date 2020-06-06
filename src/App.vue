<template>
  <div id="app">
    
    <Header
      v-bind:countries="filteredCountries"
      v-bind:filters="filters"
      @changeFilters="changeFilters"
    />

    <div class="countries-list">
      <Country 
        v-for="country in filteredCountries"
        v-bind:key="country.name"
        v-bind:country="country"
      />
    </div>
    
  </div>
</template>

<script>
import Country from './components/Country'
import Header from './components/Header'

export default {
  name: 'App',

  components: {
    Country, Header
  },

  data() {
    return {
      countries: [],
      filteredCountries: [],
      filters: {
        name: ''
      }
    }
  },

  methods: {
    changeFilters(field, value) {
      // console.log(`field = ${field}; value = ${value}`)
      this.filters[field] = value

      this.applyFilters()
    },

    applyFilters() {
      this.filteredCountries = this.countries
        .filter(country => country.name.toLowerCase().includes(this.filters.name.toLowerCase()))
    }

  },

  mounted() {
    fetch('https://restcountries.eu/rest/v2/all')
      .then(response => response.json())
      .then(json => {
        this.countries = json
        this.filteredCountries = json
      })
  },
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.btn {
  cursor: pointer;
}

.countries-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  .country {
    width: 49%;
    box-sizing: border-box;
  }
}

@media screen and (max-width: 900px) {
  .countries-list {
    justify-content: center;

    .country {
      width: 100%;
    }
  }
}
</style>
