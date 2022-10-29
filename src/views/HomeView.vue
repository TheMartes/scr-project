<template>
  <div id="home">
    <section class="container home-container">
      <homeCont
        v-for="item in home"
        :key="item.id"
        :title="item.title"
        :item="item"
      />
    </section>
  </div>
</template>

<script lang="ts">
import axios from "axios";
import { defineAsyncComponent, defineComponent } from "vue";

const homeCont = defineAsyncComponent(
  () =>
    import(/* webpackChunkName: "HomeContent" */ "@/components/HomeContent.vue")
);

export default defineComponent({
  name: "HomePage",
  components: {
    homeCont,
  },
  data() {
    return {
      home: {},
      blogs: null,
    };
  },
  async created() {
    try {
      await axios.get("home/").then((response) => {
        this.home = response.data;
      });
    } catch (error) {
      console.log("error: " + error);
    }
  },
});
</script>

<style scoped lang="scss">
#home {
  padding: 4.375rem 0 3.125rem;
}
.home-container {
  width: 50%;
  @media (max-width: 480px) {
    width: 80%;
  }
}
</style>
