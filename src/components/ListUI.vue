<script setup></script>

<template>
  <section class="wrapper__list">
    <ul>
      <li v-for="city in cityList" >city</li>
    </ul>
  </section>
</template>

<style scoped>
.wrapper__list {
  box-sizing: border-box;
  background-color: rgb(226, 219, 219);
  position: absolute;
  top: 18%;
  width: 358px;
  border-radius: 15px;
  height: 40px;
}
</style>
