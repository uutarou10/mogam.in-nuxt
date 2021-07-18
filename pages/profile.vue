<template>
  <div>
    <heading :level='1' class='pageTitle'>Profile</heading>
    <p>のなか こうた<br/>もがみんと呼ばれたり、ううたろと呼ばれたりしていた時期もありました。</p>
    <heading :level='2'>経歴</heading>
    <ul>
      <li>2019年3月 東京工科大学 コンピュータサイエンス学部卒業</li>
      <li>2019年4月〜2021年7月 Fringe81株式会社</li>
      <li>2021年8月〜 ???</li>
    </ul>
    <heading :level='2'>スキル</heading>
    <p>
      JavaScript / TypeScript / React / Elm / Firebase などを使ったフロントエンド開発をやってきました。<br/>
      たまにGolangを書いたり、書かなかったり。
    </p>
    <p>クラウドはGCPがお好き。</p>
    <heading :level='2'>趣味</heading>
    <p>アイドル(でんぱ組.inc) / カメラ / ガジェット etc...</p>
  </div>
</template>
<script>
import Heading from '../components/Heading'
export default {
  components: { Heading }
}
</script>

<style lang='scss' scoped>
.pageTitle {
  margin-bottom: 64px;
}
</style>
