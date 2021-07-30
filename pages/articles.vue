<template>
  <div>
    <AppHeading :level='1' class='pageTitle'>Articles</AppHeading>
    <p>
      直近で書いた記事をピックアップしています。<br/>
      技術系の記事・アウトプットはブログとZennがメイン(Qiitaは過去記事が多め)です。<br/>
      noteにはそれ以外で残しておきたい出来事などを気ままに書いています。
    </p>
    <MediaSelector
      :active-media-type='activeMediaType'
      class='mediaSelector'
      @click='onChangeActiveMedia($event)'
    />
    <div class='articleList'>
      <ArticleCard
        v-for='article of filteredArticles'
        :key='article.link'
        class='articleCard'
        :title='article.title'
        :body='article.contentSnippet'
        :date='new Date(article.isoDate)'
        :media-type='mediaTypeByUrl(article.link)'
        :url='article.link'
      />
    </div>
  </div>
</template>

<script lang='ts'>
import * as crypto from 'crypto';
import { Component, Vue } from "vue-property-decorator";
import Parser from 'rss-parser';
import AppHeading from '../components/AppHeading.vue'
import ArticleCard from '../components/ArticleCard.vue'
import MediaSelector from '../components/MediaSelector.vue'

const md5 = (str: string) => {
  return crypto.createHash('md5').update(str).digest('hex');
}

type MediaType = 'all' | 'note' | 'qiita' | 'zenn' | 'blog';

interface Article {
  link: string,
  title: string,
  contentSnippet: string,
  isoDate: string
}

@Component({
  components: {AppHeading, ArticleCard, MediaSelector},
  head: {
    title: 'Articles'
  },
  async asyncData() {
    const parser = new Parser();
    const feedUrls = [
      'https://note.com/mogamin3/rss',
      'https://yurufuwa-tech.hatenablog.com/rss',
      'https://zenn.dev/mogamin/feed',
      'https://qiita.com/mogamin3/feed'
    ];

    const articles = (await Promise.all(feedUrls.map(feedUrl => parser.parseURL(feedUrl))))
      .reduce<Article[]>((prev, current) => ([...prev, ...(current.items as Article[])]), []);
    return {
      articles,
      feedHash: md5(JSON.stringify(articles))
    }
  }
})
export default class Articles extends Vue {
  articles: Article[] = [];
  feedHash: string = "";
  activeMediaType: MediaType = 'all';

  onChangeActiveMedia(mediaType: MediaType) {
    this.activeMediaType = mediaType;
  }

  mediaTypeByUrl(url: string): MediaType {
    if (this.isQiita(url)) {
      return 'qiita';
    } else if (this.isNote(url)) {
      return 'note';
    } else if (this.isBlog(url)) {
      return 'blog';
    } else if (this.isZenn(url)) {
      return 'zenn';
    } else {
      return 'all'; // unknown的なやつの方がいいかも
    }
  }

  isQiita(url: string): boolean {
    const {host} = new URL(url);
    return /^qiita.com$/.test(host);
  }

  isNote(url: string): boolean {
    const {host} = new URL(url);
    return /^note.com$/.test(host);
  }

  isBlog(url: string): boolean {
    const {host} = new URL(url);
    return /^yurufuwa-tech.hatenablog.com$/.test(host);
  }

  isZenn(url: string): boolean {
    const {host} = new URL(url);
    return /^zenn.dev$/.test(host);
  }

  get filteredArticles(): Parser.Item[] {
    return (() => {
      switch (this.activeMediaType) {
        case 'blog':
          return this.articles.filter(article => this.isBlog(article.link))
        case 'zenn':
          return this.articles.filter(article => this.isZenn(article.link))
        case 'qiita':
          return this.articles.filter(article => this.isQiita(article.link))
        case 'note':
          return this.articles.filter(article => this.isNote(article.link))
        case 'all':
        default:
          return this.articles;
      }
    })().sort((a, b) => new Date(a.isoDate).getTime() < new Date(b.isoDate).getTime() ? 1 : -1);
  }
}
</script>

<style lang='scss' scoped>
.pageTitle {
  margin-bottom: 64px;
}

.mediaSelector {
  margin-top: 32px;
}

.articleList {
  width: 100%;
  margin-top: 32px;
  display: grid;
  grid-template-columns: calc(50% - 16px) calc(50% - 16px); // ↓だと記事タイトルとかが長いときにgridをはみ出していってしまうのでいたしかなたなく。
  gap: 32px;

  @media screen and (max-width: 768px) {
    grid-template-columns: 100%;
  }
}
</style>
