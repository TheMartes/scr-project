<template>
  <nav>
    <div class="nav-inner container">
      <picture>
        <img
          src="./assets/logo.png"
          alt="Vue logo"
          title="SCR project"
          loading="lazy"
        />
      </picture>
      <div>
        <router-link to="/">Home</router-link> |
        <router-link to="/blogs">Blogs</router-link>
      </div>
    </div>
  </nav>
  <TitleHead :msg="msg" />
  <router-view :blogs="blogs" @fetchBlogs="fetchBlogs" />
</template>

<script lang="ts">
import axios from "axios";
import TitleHead from "@/inc/TitleHead.vue";
import { defineComponent } from "vue";

export default defineComponent({
  components: {
    TitleHead,
  },
  data() {
    return {
      blogs: {},
      msg: "As a Designer, I Refuse to Call Peoples 'Users'",
    };
  },
  methods: {
    async fetchBlogs(): Promise<void> {
      await axios
        .get("blogs/")
        .then((resfetch) => {
          this.blogs = resfetch.data;
        })
        .catch((err) => console.log("err: ", err));
    },
  },
  mounted() {
    this.fetchBlogs();
  },
});
</script>

<style lang="scss">
body {
  margin: 0;
  background-color: $project-white;
}

img {
  max-width: 100%;
  height: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.container {
  max-width: 80rem;
  width: 95%;
  margin: 0 auto;
}

nav {
  height: 70px;
  padding: 1.875rem;

  a {
    font-weight: bold;
    color: #2c3e50;
    text-decoration: none;

    &.router-link-exact-active {
      text-decoration: underline;
    }
  }

  picture {
    height: 100%;
  }
  .nav-inner {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 100%;
  }
}

.head-home {
  background: $project-light;
  padding: 2.813rem 0;
  h1 {
    text-align: left;
    font-size: 1.313rem;
    margin: 0;
    margin-left: 15%;
  }
}
</style>
