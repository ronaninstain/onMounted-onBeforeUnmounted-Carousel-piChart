<template>
  <div
    class="app bg-gray-100 min-h-screen flex flex-col items-center justify-center"
  >
    <h1 class="text-3xl font-semibold mb-4">Vue.js Playground</h1>
    <Carousel />
  </div>
</template>

<script setup>
import Carousel from "./components/Carousel.vue";
</script>

<style>
.app {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
}
</style>
