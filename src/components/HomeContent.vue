<template>
  <div class="home-article">
    <picture v-if="item.imgName">
      <img
        :src="require('../assets/img/' + item.imgName + '.webp')"
        :srcset="require('../assets/img/' + item.imgName + '@2x.webp')"
        :alt="item.title"
        :title="item.imgAlt"
        :width="item.imgW"
        class=""
        loading="lazy"
        type="image/webp"
      />
    </picture>
    <article v-if="item.text" v-html="item.text"></article>
    <article v-if="item.note" v-html="item.note" class="article-note"></article>
  </div>
</template>

<script lang="ts">
export default {
  props: {
    item: Object,
  },
};
</script>

<style scoped lang="scss">
.home-article {
  text-align: left;
  &:first-child {
    margin-bottom: 1.875rem;
  }
  img {
    object-fit: cover;
    height: 20vw;
  }
}
.article-note {
  background-color: $project-light;
  padding: 1rem;
  font-weight: 700;
  font-style: italic;
  text-align: justify;
}
</style>
