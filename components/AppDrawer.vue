<template>
  <div class='appDrawer'>
    <button class='appDrawer__closeButton' @click='$emit("close-drawer")'>
      <img src='~/assets/close.svg' alt='close button'>
    </button>
    <nav class='appDrawer__nav'>
      <AppHeading :level='3'><NuxtLink to='/profile'>Profile</NuxtLink></AppHeading>
      <AppHeading :level='3'><NuxtLink to='/articles'>Articles</NuxtLink></AppHeading>
      <AppHeading :level='3'><NuxtLink to='/contact'>Contact</NuxtLink></AppHeading>
    </nav>
  </div>
</template>

<script>
import AppHeading from './AppHeading'
export default {
  components: { AppHeading }
}
</script>

<style lang='scss' scoped>
.appDrawer {
  display: flex;
  flex-direction: column;
  gap: 48px;
  padding: 32px 48px;
  width: 400px;
  height: 100%;
  background-color: #F2F3F4;

  @media screen and (max-width: 400px) {
    width: 100vw;
    padding: 32px;
  }

  &__nav {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  &__closeButton {
    align-self: flex-end;
    width: 32px;
    height: 32px;
    cursor: pointer;
  }
}
</style>

