<template>
  <div class="filters">
    <button @click="$emit('toggle-filters')" class="btn btn-close top">&times;</button>
    <form @submit.prevent="onSubmit">
      <div class="inner">
        <div>
          <label>
            Name country
            <input type="text" />
          </label>
        </div>

        <div>
          <button @click="$emit('toggle-filters')" class="btn btn-close bottom" type="submit">OK</button>
        </div>
      </div>
    </form>
  </div>
</template>

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
