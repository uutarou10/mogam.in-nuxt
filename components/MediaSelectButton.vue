<template>
  <button
    :class="['mediaSelectButton', {['mediaSelectButton--isActive']: isActive}]"
    @click='$emit("click")'
  >
    <slot/>
  </button>
</template>

<script lang='ts'>
import Vue from 'vue';

export default Vue.extend({
  props: {
    isActive: {
      type: Boolean,
      default() {
        return false
      }
    }
  }
});
</script>

<style lang='scss'>
.mediaSelectButton {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 8px 24px;
  border-radius: 4px;
  font-size: 24px;
  text-align: center;
  border: #20C0FB 1px solid;
  color: #20C0FB;
  background-color: white;
  transition: opacity .2s, background-color .2s, color .2s;

  &--isActive {
    background-color: #20C0FB;
    color: #F2F3F4;
  }

  &:hover {
    opacity: .5;
  }
}
</style>
