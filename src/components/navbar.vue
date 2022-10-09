<template>
  <nav class="flex justify-between w-screen">
      <div class="flex items-center">
        <img src="@/assets/logo.png" alt="logo" class="w-36" />
      </div>
      <div class="flex items-center">
        <h1 class="text-2xl font-bold text-gray-800">WRI Love Meter</h1>
      </div>
      <div class="flex items-center">
        <router-link to="/" class="p-4">Love Meter</router-link>
        <router-link to="/about" class="p-4">Tentang Project</router-link>
      </div>
  </nav>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";

export default class Navbar extends Vue {}
</script>

<style>
</style>