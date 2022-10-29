<template>
  <div class="head-home">
    <div class="container">
      <h1>{{ msg }}</h1>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  Name: "Title Head",
  props: ["msg"],
};
</script>
