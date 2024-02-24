<script setup>
import { ref, watch } from 'vue';
import SearchUI from './components/SearchUI.vue';
import HightlightsUI from './components/HightlightsUI.vue';
import BottomUI from './components/BottomUI.vue';

navigator.geolocation.getCurrentPosition((position) => console.log(position));
const globalCityInfo = ref();

watch(globalCityInfo, () => {
  console.log(globalCityInfo.value);
});
</script>

<template>
  <div class="wrapper">
    <div class="wrapper__top">
      <SearchUI @city-info="(data) => (globalCityInfo = data)" />
      <HightlightsUI :city-info-props="globalCityInfo" />
    </div>
    <div class="wrapper__bottom">
      <BottomUI
        :general-info="
          globalCityInfo?.coord === undefined
            ? 'Longitude: '
            : 'Longitude: ' + String(globalCityInfo.coord.lon)
        "
        :optional-info="
          globalCityInfo?.coord == undefined
            ? 'Latitude: '
            : 'Latitude: ' + String(globalCityInfo.coord.lat)
        "
        :img="'/src/assets/general-imgs/longitude.svg'"
        :general-text="'Longitude measures distance east or west of the prime meridian'"
        :optional-text="'Latitude lines start at the equator (0 degrees latitude) and run east and west, parallel to the equator'"
      />
      <BottomUI
        :general-info="
          globalCityInfo?.main === undefined
            ? 'Humidity: '
            : 'Humidity: ' + globalCityInfo.main.humidity + '%'
        "
        :img="'/src/assets/general-imgs/humidity.svg'"
        :general-text="'Humidity is the concentrationof water vapor present in the air. Water vapor, the gaseous state of water, is generally invisible to the human eye.'"
        :optional-text="'The same amount of water vapor result in higher relative humidity in cool air than warm air.'"
      />
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
  justify-content: space-between;
}

.wrapper__bottom {
  justify-content: space-between;
}
</style>
