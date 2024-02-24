<script setup>
defineProps({
  displayTypeSrc: String,
  displayTypeTitle: String,
  displayInfoOne: String,
  displayInfoTwo: String,
  displayInfoThree: String,
  displayInfoFour: String,
  weatherInfo: String
});
</script>

<template>
  <div class="wrapper__displays">
    <div class="wrapper__displays-block top">
      <h2 class="wrapper__displays-top_main-text">{{ displayTypeTitle }}</h2>
      <img class="wrapper__display-top_img" :src="displayTypeSrc" alt="typeBlock" />
      <div class="wrapper__displays-top_main-bottom-block">
        <span v-if="displayInfoOne?.length">{{ displayInfoOne }}</span>
        <span>{{ displayInfoTwo }}</span>
      </div>
    </div>
    <div class="wrapper__displays-block bottom">
      <p>{{ displayInfoThree }}</p>
      <p>{{ displayInfoFour }}</p>
    </div>
  </div>
</template>

<style scoped>
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
