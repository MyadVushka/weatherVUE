<script setup></script>

<template>
  <section class="wrapper__hightlight">
    <h1>Today's Highlights</h1>
    <div class="wrapper__bottom">
      <div class="wrapper__displays">
        <div class="wrapper__displays-block top">
          <h2 class="wrapper__displays-top_main-text">Wind</h2>
          <img
            class="wrapper__display-top_img"
            src="../assets/general-imgs/wind-icon.svg"
            alt="wind"
          />
          <div class="wrapper__displays-top_main-bottom-block">
            <span>3.6 m/s</span>
            <span>350 deg</span>
          </div>
        </div>
        <div class="wrapper__displays-block bottom">
          <p>Wind gusts</p>
          <p>8.4 m/s</p>
        </div>
      </div>
      <div class="wrapper__displays">
        <div class="wrapper__displays-block top">
          <h2 class="wrapper__displays-top_main-text">Pressure</h2>
          <img
            class="wrapper__display-top_img"
            src="../assets/general-imgs/pressure.svg"
            alt="pressure"
          />
          <div class="wrapper__displays-top_main-bottom-block">
            <span>765 mm</span>
          </div>
        </div>
        <div class="wrapper__displays-block bottom">
          <p>Feels like</p>
          <p>21 C</p>
        </div>
      </div>
      <div class="wrapper__displays">
        <div class="wrapper__displays-block top">
          <h2 class="wrapper__displays-top_main-text">Sunrise and sunset</h2>
          <img src="" alt="" />
          <div class="wrapper__displays-top_main-bottom-block"></div>
        </div>
        <div class="wrapper__displays-block bottom"></div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.wrapper__hightlight {
  background: radial-gradient(
    circle at center top,
    rgba(73, 85, 145, 0.897) 0%,
    rgba(97, 86, 113, 1) 100%
  );
  padding: 20px 40px;
  border-radius: 20px;
  display: flex;
  flex-direction: column;
  gap: 60px;
}

.wrapper__bottom {
  display: flex;
  gap: 40px;
}

.wrapper__displays {
  display: flex;
  flex-direction: column;
  gap: 40px;
}

.wrapper__displays-block {
  background: radial-gradient(circle at center, rgb(68, 68, 120) 100%, rgb(97, 90, 160) 100%);
  padding: 20px;
  border-radius: 14px;
}
.wrapper__display-top_img {
  width: 120px;
  height: 80px;
}

.wrapper__displays-top_main-bottom-block {
  display: flex;
  padding-top: 25px;
  justify-content: center;
  gap: 20px;
}
</style>
