<template>
  <nav class='mediaSelector'>
    <MediaSelectButton
      :is-active='activeMediaType === "all"'
      @click='$emit("click", "all")'
    >すべて</MediaSelectButton>
    <MediaSelectButton
      :is-active='activeMediaType === "blog"'
      @click='$emit("click", "blog")'
    >Blog</MediaSelectButton>
    <MediaSelectButton
      :is-active='activeMediaType === "zenn"'
      @click='$emit("click", "zenn")'
    >Zenn</MediaSelectButton>
    <MediaSelectButton
      :is-active='activeMediaType === "note"'
      @click='$emit("click", "note")'
    >note</MediaSelectButton>
    <MediaSelectButton
      :is-active='activeMediaType === "qiita"'
      @click='$emit("click", "qiita")'
    >Qiita</MediaSelectButton>
  </nav>
</template>

<script lang='ts'>
import MediaSelectButton from './MediaSelectButton'
export default {
  components: { MediaSelectButton },
  props: {
    activeMediaType: {
      type: String,
      required: true,
      validate(value) {
        return ['all','blog','zenn','note','qiita'].includes(value);
      }
    }
  }
};
</script>

<style lang='scss' scoped>
.mediaSelector {
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 12px;
}
</style>
