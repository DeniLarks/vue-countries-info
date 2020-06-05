<template>
  <div class="country">

      <div 
        v-for="(field, index) in neededField"
        v-bind:key="index"
      >
      
        <CountryField 
          v-bind:label="field.name"
          v-bind:value="country[field.name]"
          v-bind:type="field.type"  
        />
      </div>
  </div>
</template>

<script>
import CountryField from './CountryField'

export default {
  props: ['country'],
  data() {
    return {
      neededField: [
        { name: 'name'},
        { name: 'capital'}, 
        { name: 'region'}, 
        { name: 'population'},
        { name: 'area'}, 
        { type: 'img', name: 'flag'}
      ]
    }
  },
  components: {
    CountryField
  }
}
</script>

<style lang="scss" scoped>
  .country {
    border: 1px solid black;
    margin-bottom: 12px;
    padding: 15px;
  }
</style>