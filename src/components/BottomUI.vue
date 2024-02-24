<script setup>
const props = defineProps({
  generalInfo: String,
  generalText: String,
  optionalInfo: String,
  optionalText: String,
  img: String
});
</script>

<template>
  <section class="wrapper__longitude">
    <div class="wrapper__longitude_img">
      <img :src="props.img" alt="" />
    </div>
    <div class="wrapper__longitude-text">
      <div class="wrapper__longitude-text_longitude">
        <h2>{{ props.generalInfo }}</h2>
        <p>{{ props.generalText }}</p>
      </div>
      <div class="wrapper__longitude-text_latitude">
        <h2>{{ props.optionalInfo }}</h2>
        <p>
          {{ props.optionalText }}
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.wrapper__longitude {
  background: radial-gradient(
    circle at left top,
    rgba(73, 85, 145, 0.897) 0%,
    rgba(97, 86, 113, 1) 100%
  );
  padding: 15px 10px;
  border-radius: 20px;
  display: flex;
  align-items: center;
  gap: 20px;
  max-width: 500px;
}

h2 {
  margin: 0;
  font-size: 20px;
  font-weight: 500;
}

p {
  margin-top: 5px;
  color: rgba(255, 255, 255, 0.411);
  font-size: 16px;
}

img {
  width: 130px;
}
</style>
