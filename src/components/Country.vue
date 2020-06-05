<template>
  <div class="country">
    <div class="name_flag">
      <img v-bind:src="country.flag" v-bind:alt="'flag of ' + country.name">
      <h3 class="name">
        {{country.name}}
      </h3>
    </div>
<!--  -->
      <div class="info">
        <CountryField 
          v-for="(field, index) in neededField"
          v-bind:key="index"
          v-bind:label="field.name"
          v-bind:value="country[field.name]"
        />
      </div>
  </div>
</template>

<script>
import CountryField from './CountryField'

export default {
  props: ['country'],
  
  components: {
    CountryField
  },

  data() {
    return {
      neededField: [
        { name: 'capital' },
        { name: 'region' }, 
        { name: 'population' },
        { name: 'area' }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
  .country {
    border: 1px solid black;
    margin-bottom: 12px;
    padding: 15px;
    background-color: cornsilk;

    .name_flag {
      display: flex;

      img {
        width: 40%;
        border: 1px solid black;
      }
      
      .name {
        text-align: left;
        font-size: 30px;
        padding: 0 10px;
      }
    }

    .info {
      display: flex;
      flex-wrap: wrap;
      text-align: left;
    }
  }
</style>