<template>
  <div class="filters">
    <button 
      @click="$emit('toggle-filters')" 
      class="btn btn-close top"
    >&times;</button>
    
    <form @submit.prevent="onSubmit">
      <div class="inner">
        <div>
          <label>
            Name country
            <input
              v-model="filters.name"
              type="text" 
              @input="changerName"
            />
          </label>
          <label>
            Region
            <!-- v-model="filter" -->
            <select v-model="filters.region" @change="changerRegion">
              <option
                v-for="(region, index) in regions"
                v-bind:key="index"
                v-bind:value="region"
              >
                {{region}}
              </option>
            </select>
          </label>
        </div>

        <div>
          
          <button 
            @click="$emit('toggle-filters')"
            class="btn btn-close bottom" 
            type="submit"
          >OK</button>

        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  props: ['filters', 'regions'],

  methods: {
    changerName(input) {
      this.$emit('changeFilters', 'name', input.target.value)
    },
    changerRegion(input) {
      this.$emit('changeFilters', 'region', input.target.value)
    }
  }
}
</script>

<style lang="scss" scoped>
  .filters {
    position: absolute;
    width: 50%;
    height: 500px;
    background-color: #f1dfdf;

    border: 1px solid #928989;
    box-shadow: 4px 4px 5px #d1c6c6;

    padding: 20px;

    .inner {
      margin: 5% 0;
      height: 90%;
      overflow: auto;
    }

    .btn-close {
      position: absolute;
      background-color: grey;
      color: white;
      font-size: 20px;
      border: none;
      border-radius: 5px;

      &.top {
        top: 10px;
        right: 10px;
      }

      &.bottom {
        bottom: 10px;
        right: 50%;
        transform: translateX(50%);
      }
    }
  }
</style>
