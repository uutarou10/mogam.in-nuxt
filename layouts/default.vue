<template>
  <div class='container'>
    <header>
      <NuxtLink to='/'>
        <img alt='logo' src='~/assets/logo.svg' class='logo' />
      </NuxtLink>
      <HamburgerButton />
    </header>
    <main>
      <Nuxt />
    </main>
    <SiteFooter />
  </div>
</template>

<script>
import Vue from 'vue';
import HamburgerButton from '../components/HamburgerButton';
import SiteFooter from '../components/SiteFooter'

export default Vue.extend({
  components: {
    SiteFooter,
    HamburgerButton
  }
})
</script>

<style lang='scss' scoped>
.container {
  width: 1200px;
  margin: 0 auto;
}

header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 32px 0;

  .logo {
    width: 80px;
    height: 80px
  }
}

main {
  padding-top: 32px;
}
</style>
