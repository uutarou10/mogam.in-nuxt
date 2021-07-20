<template>
  <div class='container'>
    <header>
      <NuxtLink to='/'>
        <img alt='logo' src='~/assets/logo.svg' class='logo' />
      </NuxtLink>
      <HamburgerButton @click='isShowDrawer = true' />
    </header>
    <main>
      <Nuxt />
    </main>
    <SiteFooter />
    <transition name='drawerTransition'>
      <div v-if='isShowDrawer'>
        <div class='drawerBackdrop' @click='isShowDrawer = false'></div>
        <AppDrawer class='drawer' />
      </div>
    </transition>
  </div>
</template>

<script>
import Vue from 'vue';
import HamburgerButton from '../components/HamburgerButton';
import SiteFooter from '../components/SiteFooter'
import AppDrawer from '../components/AppDrawer'

export default Vue.extend({
  components: {
    AppDrawer,
    SiteFooter,
    HamburgerButton
  },
  data() {
    return {
      isShowDrawer: false
    }
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

.drawerBackdrop {
  width: 100vw;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
  transition: all .2s;
  opacity: 1;
  background-color: rgba(0,0,0, .2);
  cursor: pointer;
}

.drawer {
  position: fixed;
  top: 0;
  right: 0;
  transition: all .2s;
}

.drawerTransition {
  &-enter, &-leave-to {
    .drawerBackdrop {
      opacity: 0;
    }
    .drawer {
      transform: translateX(100%);
    }
  }
  &-enter-active, &-leave-active {
    transition: all .2s;
  }
}
</style>
