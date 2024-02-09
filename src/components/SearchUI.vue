<script setup></script>

<template>
  <section class="wrapper__search">
    <div class="wrapper__input-block">
      <input class="wrapper__search_input" type="text" />
      <img
        class="wrapper__search_img"
        src="../assets/general-imgs/magnifying-glass-svgrepo-com.svg"
        alt="lupa"
      />
    </div>
    <div class="wrapper__weather-main">
      <img class="wrapper__search-info_img" src="../assets/weatherIMGS/cloudy.svg" alt="weather" />
      <h1 class="wrapper__weather-info_gradus">14 C</h1>
      <p class="wrapper__weather-info_forecast-type">Thunderstorm</p>
    </div>
    <div class="border"></div>
    <div class="wrapper__weather-secondary">
      <div class="wrapper__weather-secondary_geo">
        <img
          class="wrapper__weather-secondary_img"
          src="../assets/general-imgs/geolocation.svg"
          alt="geolocation"
        />
        <p>Paris, FR</p>
      </div>
      <div class="wrapper__weather-secondary_date">
        <img
          class="wrapper__weather-secondary_img"
          src="../assets/general-imgs/calendar.svg"
          alt=""
        />
        <p>Thu, February 9, 2024</p>
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
.wrapper__weather-secondary_date {
  display: flex;
  align-items: center;
  gap: 15px;
}
</style>
