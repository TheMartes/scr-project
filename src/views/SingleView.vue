<template>
  <div id="single-blog">
    <h1>{{ blog.title }}</h1>
    <picture class="block relative pb-75p mb-4">
      <source
        :srcset="
          './assets/img/' +
          blog.imgName +
          '.webp 1x, ./assets/img/' +
          blog.imgName +
          '@2x.webp 2x'
        "
        type="image/webp"
      />
      <img
        :src="'./assets/img/' + blog.imgName + '.jpg'"
        :srcset="'./assets/img/' + blog.imgName + '@2x.jpg'"
        :alt="blog.title"
        :title="blog.title"
        :width="blog.imgW"
        class="absolute t-0 l-0 w-full h-full object-cover"
        loading="lazy"
      />
    </picture>
    <article v-html="blog.article"></article>
    <p v-html="blog.authorName"></p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      blog: {},
    };
  },
  props: ["blogs"],
  mounted() {
    this.id = this.$route.params.id;
    this.blog = this.blogs.find((blog) => blog.id == this.id);
  },
};
</script>
