<script setup>
import DisplayUI from './DisplayUI.vue';

const props = defineProps({
  cityInfoProps: Object
});
</script>

<template>
  <section class="wrapper__hightlight">
    <h1>Today's Highlights</h1>
    <div class="wrapper__bottom">
      <DisplayUI
        :displayTypeSrc="'/src/assets/general-imgs/wind-icon.svg'"
        :displayTypeTitle="'Wind'"
        :displayInfoOne="
          props?.cityInfoProps === undefined ? '' : String(props.cityInfoProps.wind.speed)
        "
        :displayInfoTwo="'m/s'"
        :displayInfoThree="'Wind gusts'"
        :displayInfoFour="
          props?.cityInfoProps?.wind?.gust === undefined
            ? 'm/s'
            : String(props.cityInfoProps.wind.gust) + ' m/s'
        "
      />
      <DisplayUI
        :displayTypeSrc="'/src/assets/general-imgs/pressure.svg'"
        :displayTypeTitle="'Pressure'"
        :displayInfoOne="
          props?.cityInfoProps === undefined ? 'mm' : props.cityInfoProps.main.pressure + ' mm'
        "
        :displayInfoThree="'Feels like'"
        :displayInfoFour="
          props?.cityInfoProps === undefined
            ? 'C'
            : Math.round(props.cityInfoProps.main.feels_like - 273) + ' C'
        "
      />
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
  justify-content: center;
  align-items: center;
  gap: 60px;
  width: 400px;
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
