<template>
  <div>
    <span>{{label}}</span>
    &nbsp;
    <img v-if="type === 'img'" v-bind:src="value" alt="">
    <span v-else>{{value}}</span>
  </div>
</template>

<script>
export default {
  props: ['label', 'value', 'type']
}
</script>