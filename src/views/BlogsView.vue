<template>
  <div id="blogs-list">
    <!-- <p>{{ blogs }}</p> -->
    <h1>Blogs List</h1>
    <div class="grid-blog">
      <blogsList v-for="blog in blogs" :key="blog.id" :blog="blog" />
    </div>
  </div>
</template>

<script lang="ts">
// import axios from "axios";
import { defineAsyncComponent } from "vue";

const blogsList = defineAsyncComponent(
  () =>
    import(/* webpackChunkName: "BlogsList" */ "@/components/BlogListing.vue")
);

export default {
  name: "BlogListing",
  components: {
    blogsList,
  },
  props: ["blogs"],
  //   data() {
  //     return {
  //       blogs: {},
  //     };
  //   },
  //   async created() {
  //     try {
  //       const resp = await axios.get("blogs/").then((resp) => {
  //         this.blogs = resp.data;
  //       });
  //     } catch (error) {
  //       console.log("error: " + error);
  //     }
  //   },
};
</script>

<style lang="scss">
.grid-blog {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
}
</style>
