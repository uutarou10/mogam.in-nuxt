<template>
  <component :is='`h${level}`' class='heading'>
    <slot></slot>
  </component>
</template>

<script lang='ts'>
import Vue from 'vue';

export default Vue.extend<{}, {}, {}, {level: number}>({
  props: {
    level: {
      type: Number,
      required: true,
      default() {
        return 1;
      },
      validator(value) {
        return [1,2,3].includes(value)
      }
    }
  }
});
</script>

<style lang='scss' scoped>
.heading {
  color: #20C0FB;
  line-height: 180%;
}

h1 {
  font-weight: 800;
  font-size: 48px;
}

h2 {
  font-weight: 700;
  font-size: 36px;
}

h3 {
  font-weight: 500;
  font-size: 24px;
}
</style>
