<!-- pages/index.vue -->
<template>
  <div class="Home">
    <ImageCarousel />
  </div>
</template>

<script setup>
import ImageCarousel from '@/components/ImageCarousel.vue';
</script>

<style scoped>
 * {
  top: 0;
   left: 0;
   right: 0;
   bottom: 0;
 }
.Home {
  display: block;
  justify-content: center;
  align-items: center;
}
</style>
