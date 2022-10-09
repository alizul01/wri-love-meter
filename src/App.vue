<template>
  <Navbar class="p-8" />
  <router-view />
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@100;300;400;500;700;900&display=swap");
#app {
  font-family: "Inter", sans-serif;
  text-align: center;
  color: #2c3e50;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #b942af;
}
</style>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import Navbar from './components/navbar.vue'

@Options({
  components: {
    Navbar,
  },
})

export default class App extends Vue {}
</script>