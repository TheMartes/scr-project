<template>
  <div>
    <picture>
      <img
        :src="'./assets/img/' + blog.imgName + 'jpg'"
        :alt="blog.title"
        :title="blog.title"
        :width="blog.imgW"
        loading="lazy"
      />
    </picture>
    <router-link :to="{ name: 'SingleView', params: { id: blog.id } }">
      <h2>{{ blog.title }}</h2>
    </router-link>
    <article v-html="blog.article"></article>
  </div>
</template>

<script lang="ts">
export default {
  props: {
    blog: Object,
  },
};
</script>
