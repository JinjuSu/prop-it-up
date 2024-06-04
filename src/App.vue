<template>
  <NavbarComp></NavbarComp>
  <router-view />
</template>

<script>
import NavbarComp from "./components/NavbarComp.vue";

export default {
  name: "App",
  components: { NavbarComp },
};
</script>

<style>
#app {
  font-family: Roboto, Helvetica, Arial, sans-serif;
}
</style>
