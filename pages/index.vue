<template>
  <div class='mainContainer'>
    <main>
      <img src='~/assets/logo.svg' alt='logo' class='logo' />
      <h1>
        <img src='~/assets/text-logo.svg' alt='mogam.in' class='text-logo' />
      </h1>
      <nav>
        <heading :level='3'><NuxtLink to='/profile'>Profile</NuxtLink></heading>
        <heading :level='3'><NuxtLink to='/articles'>Articles</NuxtLink></heading>
        <heading :level='3'><NuxtLink to='/contact'>Contact</NuxtLink></heading>
      </nav>
    </main>
    <site-footer />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import heading from '~/components/Heading.vue';
import SiteFooter from '~/components/SiteFooter.vue'

export default Vue.extend({
  components: {
    SiteFooter,
    heading,
  },
  layout: 'topPage'
})
</script>

<style lang='scss' scoped>
.mainContainer {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

main {
  display: flex;
  flex-direction: column;
  align-items: center;
}

nav {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 44px;
}

.text-logo {
  width: 240px;
  margin-top: 24px;
}

.logo {
  width: 100px;
  height: 100px;
}

</style>
