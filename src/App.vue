<script setup>
import { ref } from 'vue';
import SearchUI from './components/SearchUI.vue';
import HightlightsUI from './components/HightlightsUI.vue';
import LongitudeUI from './components/LongitudeUI.vue';
import HumidityUI from './components/HumidityUI.vue';

navigator.geolocation.getCurrentPosition((position) => console.log(position));
const globalCityInfo = ref();

</script>

<template>
  <div class="wrapper">
    <div class="wrapper__top">
      <SearchUI @city-info="(data) => (globalCityInfo = data)" />
      <HightlightsUI :city-info-props="globalCityInfo" />
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
