<template>
  <div class="header">
    <div class="filters-btn-container">
      <button class="btn btn-filters" @click="toggleFilters">Filters</button>
      <Filters
        v-bind:regions="regions"
        v-if="isFilters"
        v-bind:filters="filters"
        @toggle-filters="toggleFilters" 
        @changeFilters="changeFilters"
      />    
    </div>
    
    <div class="countries-count">
      {{ `Found ${countries.length} countries` }}
    </div>
  </div>
</template>

<script>
import Filters from './Filters'

export default {
  props: ['countries', 'filters', 'regions'],
 
  components: {
    Filters
  },

  data() {
    return {
      isFilters: false
    }
  },

  methods: {
    toggleFilters() {
      this.isFilters = !this.isFilters 
    },

    changeFilters(field, value) {
      this.$emit('changeFilters', field, value)
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