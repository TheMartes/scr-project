<template>
  <div id="single-blog">
    <h1></h1>
    <article></article>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      id: this.$route.params.id,
      blog: {},
    };
  },
  async created() {
    try {
      await axios.get("posts/" + this.id).then((response) => {
        console.log(response);
      });
    } catch (error) {
      console.log(error);
    }
  },
};
</script>
