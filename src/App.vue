<template>
  <div id="app">
    
    <Header
      v-bind:countries="filteredCountries"
      v-bind:filters="filters"
      v-bind:regions="regions"
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
      regions: ['All'],
      filters: {
        name: '',
        region: ''
      }
    }
  },

  methods: {
    changeFilters(field, value) {
      console.log(`field = ${field}; value = ${value}`)
      this.filters[field] = value

      this.applyFilters()
    },

    applyFilters() {
      this.filteredCountries = [...this.countries]

      this.filteredCountries = this.filteredCountries
        .filter(country => country.name.toLowerCase().includes(this.filters.name.toLowerCase()))
      
      if(this.filters.region === 'All') {
        this.filteredCountries = this.filteredCountries
      } else {
        this.filteredCountries = this.filteredCountries
          .filter(country => country.region === this.filters.region)
      }
      
    }

  },

  mounted() {
    fetch('https://restcountries.eu/rest/v2/all')
      .then(response => response.json())
      .then(json => {
        this.countries = json
        this.filteredCountries = json

        const tempRegions = this.countries.map(country => {
          if(!country.region) return 'undefined'
          return country.region.trim()
        })

        tempRegions.forEach(region => {
          if(!this.regions.includes(region)) this.regions.push(region) 
        })

        this.filters.region = this.regions[0]
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
