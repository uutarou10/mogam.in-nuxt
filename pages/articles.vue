<template>
  <div>
    <AppHeading :level='1' class='pageTitle'>Articles</AppHeading>
    <div class='articleList'>
      <ArticleCard
        v-for='item of 10'
        :key='item'
        class='articleCard'
        title='hogehoge'
        body='記事本文です'
        :date='new Date()'
        media-type='note'
        url='https://yurufuwa-tech.hatenablog.com'
      />
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import AppHeading from '../components/AppHeading'
import ArticleCard from '../components/ArticleCard'

export default Vue.extend({
  components: { ArticleCard, AppHeading }
})
</script>

<style lang='scss' scoped>
.pageTitle {
  margin-bottom: 64px;
}

.articleCard {
  min-width: 588px;
}

.articleList {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 32px 0;
}
</style>
