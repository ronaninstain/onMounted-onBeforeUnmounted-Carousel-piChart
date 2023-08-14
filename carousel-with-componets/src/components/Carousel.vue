<template>
  <div class="carousel">
    <transition name="fade" mode="out-in">
      <img
        :key="currentIndex"
        :src="images[currentIndex]"
        alt="Carousel Image"
        class="carousel-image"
      />
    </transition>
    <div class="carousel-buttons">
      <button @click="prevImage" class="btn-prev">Previous</button>
      <button @click="nextImage" class="btn-next">Next</button>
    </div>
  </div>
</template>

<script setup>
import { onMounted, onBeforeUnmount, ref } from "vue";

const currentIndex = ref(0);
const images = [
  "https://images.unsplash.com/photo-1682685797769-481b48222adf",
  "https://images.unsplash.com/photo-1682695794816-7b9da18ed470",
  "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60",
  "https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d",
];

const nextImage = () => {
  currentIndex.value = (currentIndex.value + 1) % images.length;
};

const prevImage = () => {
  currentIndex.value = (currentIndex.value - 1 + images.length) % images.length;
};

let carouselInterval;

onMounted(() => {
  carouselInterval = setInterval(nextImage, 5000);
});

onBeforeUnmount(() => {
  clearInterval(carouselInterval);
});
</script>

<style scoped>
.carousel {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 400px;
}

.carousel-image {
  max-width: 100%;
  max-height: 100%;
}

.carousel-buttons {
  position: absolute;
  bottom: 20px;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
}

.btn-prev,
.btn-next {
  padding: 8px 12px;
  margin: 0 10px;
  background-color: #333;
  color: white;
  border: none;
  cursor: pointer;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
