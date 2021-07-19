<template>
  <button class='formButton'><slot/></button>
</template>

<style lang='scss' scoped>
.formButton {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 8px 36px;
  width: 151px;
  height: 48px;
  left: 87px;
  top: 13px;
  background: #20C0FB;
  border-radius: 999px;
  color: #F2F3F4;
  transition: opacity .2s, color .2s, background-color .2s;

  &:hover {
    opacity: .5;
  }

  &:disabled {
    background-color: #6D787B;
     &:hover {
       opacity: 1;
     }
  }
}
</style>
