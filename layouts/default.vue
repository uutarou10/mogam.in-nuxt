<template>
  <div class='container'>
    <header>
      <NuxtLink to='/'>
        <img alt='logo' src='~/assets/logo.svg' class='logo' />
      </NuxtLink>
      <humberger-button />
    </header>
    <Nuxt />
  </div>
</template>

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
    width: 100px;
    height: 100px
  }
}
</style>
<script>
import HumbergerButton from '../components/humbergerButton'
export default {
  components: { HumbergerButton }
}
</script>
