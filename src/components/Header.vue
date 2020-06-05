<template>
  <div class="header">
    <div class="filters-btn-container">
      <button class="btn btn-filters" @click="toggleFilters">Filters</button>
      <Filters @toggle-filters="toggleFilters" v-if="isFilters" />    
    </div>
    
    <div class="countries-count">
      {{ `Found ${countriesCount} countries` }}
    </div>
  </div>
</template>

<script>
import Filters from './Filters'

export default {
  props: ['countriesCount'],
 
  components: {
    Filters
  },

  data() {
    return {
      isFilters: false
    }
  },

  methods: {
    onSubmit() {
      console.log('submit')
    },
    toggleFilters() {
      this.isFilters = !this.isFilters 
    }
    
  }
}
</script>

<style lang="scss" scoped>
  .header {
    display: flex;
    justify-content: space-between;
    margin: 15px;
    position: relative;

  }
</style>