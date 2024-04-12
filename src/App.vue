<template>
  
  <headerComponent />

  <div class="mainContent">
    <sidebarVue />
    <posts />
  </div>

</template>

<script setup>

  import headerComponent from "./components/header.vue"
  import sidebarVue from "./components/sidebar.vue"
  import posts from "./components/posts.vue"

</script>


<style>
.mainContent{
  display: flex;
}
</style>