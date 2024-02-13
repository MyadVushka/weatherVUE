<script setup>
import ListUI from './ListUI.vue';
import { reactive, ref, watch } from 'vue';
import debounce from 'lodash.debounce';

defineProps({
  cityList: Array,
})

const apiKey = '&appid=df57d4e39636b7a56315b864ca166989';

let searchByCityName = 'https://api.openweathermap.org/data/2.5/weather?q=';
const URLCitiesList = 'http://api.openweathermap.org/geo/1.0/direct?q=';
const searchLimit = '&limit=5';
const cityListRef = ref([]);

const searchInput = ref('');

const weatherTypes = new Map([
  ['Clouds', '/src/assets/weatherIMGS/cloudy.svg'],
  ['Thundersotrm', '/src/assets/weatherIMGS/thunder.svg'],
  ['Drizzle', '/src/assets/weatherIMGS/raining.svg'],
  ['Mist', '/src/assets/weatherIMGS/mist.svg'],
  ['Rain', '/src/assets/weatherIMGS/raining.svg'],
  ['Snow', '/src/assets/weatherIMGS/snow.svg']
]);

const cityDate = reactive({
  temperature: String,
  city: String,
  region: String,
  weather: String,
  time: String,
  flag: 0
});

const weatherIMG = ref('');

const toValidTime = (timezone) => {
  const date = new Date();
  date.setHours(date.getHours() - 3 + timezone / 3600);
  return date.getMinutes() < 10
    ? date.getHours() + ':0' + date.getMinutes()
    : date.getHours() + ':' + date.getMinutes();
};

const searchListCities = async () => {
  const cities = await fetch(URLCitiesList + searchInput.value + searchLimit + apiKey);
  const response = await cities.json();

  return response;
};

const toValidWeather = (weatherType, timezone) => {
  if (weatherTypes.has(weatherType)) {
    weatherIMG.value = weatherTypes.get(weatherType);
  } else if (weatherType === 'Clear') {
    const date = Number(toValidTime(timezone).split(':')[0]);
    weatherIMG.value =
      date.getHours() >= 6 && date.getHours() <= 19
        ? '/src/assets/weatherIMGS/day.svg'
        : '/src/assets/weatherIMGS/night.svg';
  }
  return weatherIMG;
};
const searchBy = async () => {
  try {
    const response = await fetch(searchByCityName + searchInput.value + apiKey);
    const data = await response.json();
    cityDate.city = data.name;
    cityDate.region = data.sys.country;
    cityDate.temperature = Math.round(data.main.temp - 273);
    cityDate.weather = '/src/assets/weatherIMGS/day.svg';
    cityDate.weather = toValidWeather(data['weather'][0]['main'], data.timezone);
    cityDate.time = toValidTime(data.timezone);
    console.log(data);
    cityDate.flag = 1;
  } catch (err) {
    cityDate.flag = 0;
    alert('Invalid city');
  }
};

let debounceHandler = debounce(async function () {
  console.log(searchInput.value);
  const citiesList = await searchListCities();
  cityListRef.value = citiesList;
  console.log(citiesList);
}, 1000);

watch(searchInput, debounceHandler);
</script>

<template>
  <section class="wrapper__search">
    <div class="wrapper__input-block">
      <input
        v-model="searchInput"
        class="wrapper__search_input"
        @input="debounceHandler"
        type="text"
      />
      <img
        @click="searchBy"
        class="wrapper__search_img"
        src="../assets/general-imgs/magnifying-glass-svgrepo-com.svg"
        alt="lupa"
      />
    </div>
    <ListUI v-if="cityDate.flag === 1" :cityList="cityListRef" />
    <div class="wrapper__weather-main" v-if="cityDate.flag === 1">
      <img class="wrapper__search-info_img" :src="cityDate.weather" alt="weather" />
      <h1 class="wrapper__weather-info_gradus">{{ cityDate.temperature }} C</h1>
      <p class="wrapper__weather-info_forecast-type"></p>
    </div>
    <div class="border"></div>
    <div class="wrapper__weather-secondary">
      <div class="wrapper__weather-secondary_geo">
        <img
          class="wrapper__weather-secondary_img"
          src="../assets/general-imgs/geolocation.svg"
          alt="geolocation"
        />
        <p v-if="cityDate.flag === 1">{{ cityDate.city }}, {{ cityDate.region }}</p>
      </div>
      <div class="wrapper__weather-secondary_date">
        <img
          class="wrapper__weather-secondary_img"
          src="../assets/general-imgs/calendar.svg"
          alt="calendar"
        />
        <p>Thu, February 9, 2024</p>
      </div>
      <div class="wrapper__weather-secondary-time">
        <img class="wrapper__weather-secondary_img" src="../assets/general-imgs/clock.svg" alt="" />
        <p v-if="cityDate.flag === 1">{{ cityDate.time }}</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.wrapper__search {
  background: radial-gradient(
    circle at left top,
    rgba(73, 85, 145, 0.897) 0%,
    rgba(97, 86, 113, 1) 100%
  );
  padding: 40px;
  border-radius: 20px;
  display: flex;
  flex-direction: column;
  gap: 20px;
  position: relative;
}

.wrapper__search_input {
  background-color: black;
  border: none;
  outline: none;
  color: white;
  padding: 15px 60px 15px 15px;
  font-size: 25px;
  border-radius: 20px;
}

.wrapper__input-block {
  position: relative;
  margin-bottom: 30px;
}

.wrapper__search_img {
  cursor: pointer;
  right: 5%;
  top: 50%;
  transform: translateY(-50%);
  width: 30px;
  position: absolute;
}
.wrapper__search-info_img {
  width: 80px;
  margin-bottom: 30px;
}

.wrapper__weather-info_gradus {
  font-size: 40px;
}

.wrapper__weather-info_forecast-type {
  font-size: 28px;
}
.border {
  border: solid 0.1px rgb(234, 210, 210);
}
.wrapper__weather-secondary_img {
  width: 30px;
}
.wrapper__weather-secondary_geo,
.wrapper__weather-secondary_date,
.wrapper__weather-secondary-time {
  display: flex;
  align-items: center;
  gap: 15px;
  height: 60px;
}
</style>
