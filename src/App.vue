<script setup>
import SearchUI from './components/SearchUI.vue';
import HightlightsUI from './components/HightlightsUI.vue';
import LongitudeUI from './components/LongitudeUI.vue';
import HumidityUI from './components/HumidityUI.vue';

navigator.geolocation.getCurrentPosition((position) => console.log(position));
</script>

<template>
  <div class="wrapper">
    <div class="wrapper__top">
      <SearchUI />
      <HightlightsUI />
    </div>
    <div class="wrapper__bottom">
      <LongitudeUI />
      <HumidityUI />
    </div>
  </div>
</template>

<style scoped>
.wrapper__top,
.wrapper__bottom {
  display: flex;
  gap: 80px;
}

.wrapper__top {
  margin-bottom: 60px;
}

.wrapper__bottom {
  justify-content: space-between;
}
</style>
