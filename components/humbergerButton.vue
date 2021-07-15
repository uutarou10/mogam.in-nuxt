<template>
  <div @click='onClick' class='hamburgerButton'>
    <div/>
    <div/>
    <div/>
  </div>
</template>

<script lang='ts'>
  export default {
    methods: {
      onClick() {
        console.log(`onClick Hamburger!!🍔`)
      }
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

  & > div {
    width: 100%;
    height: 3px;
    background-color: #20C0FB;
  }
}
</style>
