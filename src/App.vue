<template>
  <div id="app">
    <div class="countries-count">
      {{ `Found ${countries.length} countries` }}
    </div>
    <div class="countries-list">
      <Country 
        v-for="country in countries"
        v-bind:key="country.name"
        v-bind:country="country"
      />
    </div>
    
  </div>
</template>

<script>
import Country from './components/Country'

export default {
  name: 'App',
  data() {
    return {
      countries: [
        {
          name: "Albania",
          capital: "Tirana",
          region: "Europe",
          population: 2886026,
          area: 28748,
          timezones: [
            "UTC+01:00"
          ],
          flag: "https://restcountries.eu/data/alb.svg",
          cioc: "ALB"
        },
        {
          name: "Albania2",
          capital: "Tirana",
          region: "Europe",
          population: 2886026,
          area: 28748,
          timezones: [
            "UTC+01:00"
          ],
          flag: "https://restcountries.eu/data/alb.svg",
          cioc: "ALBA"
        }
      ]
    }
  },

  mounted() {
    fetch('https://restcountries.eu/rest/v2/all')
      .then(response => response.json())
      .then(json => this.countries = json)
  },

  components: {
    Country
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.countries-count {
  text-align: right;
  margin: 20px 0;
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
