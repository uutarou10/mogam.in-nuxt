<template>
  <button class='hamburgerButton' @click="$emit('click')">
    <span/>
    <span/>
    <span/>
  </button>
</template>

<script lang='ts'>
  export default {
    emits: {
      click: () => true
    }
  }
</script>

<style lang='scss' scoped>
.hamburgerButton {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 32px;
  height: 24px;
  cursor: pointer;

  & > span {
    width: 100%;
    height: 3px;
    background-color: #20C0FB;
  }
}
</style>
