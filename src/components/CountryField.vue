<template>
  <div class="info-field">
    <span class="label">{{label.toUpperCase()}}:</span>
    &nbsp;
    <span class="value">{{value}}</span>
  </div>
</template>

<script>
export default {
  props: ['label', 'value']
}
</script>

<style lang="scss" scoped>
  .info-field {
    width: 50%;
    padding: 10px;
    box-sizing: border-box;

    .label {
      font-weight: bold;
    }
  }
</style>