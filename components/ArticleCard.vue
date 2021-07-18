<template>
  <a :href='url' target='_blank' class='articleCard'>
    <h2 class='articleCard__title'>{{title}}</h2>
    <div class='articleCard__body'>{{body}}</div>
    <small class='articleCard__footer'>{{formattedDate}} from {{mediaType}}</small>
  </a>
</template>

<script>
import Vue from 'vue';
import dayjs from 'dayjs';

export default Vue.extend({
  props: {
    title: {
      type: String,
      required: true
    },
    body: {
      type: String,
      required: true
    },
    date: {
      type: Date,
      required: true
    },
    url: {
      type: String,
      required: true
    },
    mediaType: {
      type: String,
      required: true,
      validate(value) {
        return ['blog', 'zenn', 'qiita', 'note'].includes(value)
      }
    }
  },
  computed: {
    formattedDate() {
      return dayjs(this.date).format("YYYY/MM/DD")
    }
  }
});
</script>

<style lang='scss' scoped>
.articleCard {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 24px;
  background: #F2F3F4;
  box-shadow: 4px 4px 0 #20C0FB;
  border-radius: 4px;
  cursor: pointer;
  transition: transform .2s, opacity .2s;
  text-decoration: none;

  &:hover {
    transform: scale(1.01, 1.01);
  }

  &__title {
    width: 100%;
    font-weight: 500;
    font-size: 24px;
    line-height: 36px;
    text-align: left;
  }

  &__body {
    font-size: 18px;
    line-height: 180%;
    color: #6D787B;
    width: 100%;
    height: 160px;
    text-align: left;
  }

  &__footer {
    width: 100%;
    text-align: left;
    font-size: 12px;
    line-height: 180%;
    color: #6D787B;
  }
}
</style>
