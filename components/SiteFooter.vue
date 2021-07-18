<template>
  <footer>
    <div class='footerContents'>
      <span>Copyright 2021 Kota Nonaka</span>
      <NuxtLink to='/policy'>プライバシーポリシー</NuxtLink>
    </div>
  </footer>
</template>

<style lang='scss' scoped>
footer {
  margin-top: 36px;
  color: #6D787B;
  line-height: 180%;
  font-size: 12px;
}

.footerContents {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
