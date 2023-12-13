<script setup>
import adImg from '../assets/ad.jpg'
</script>

<template>
  <div class="about">
    <h1 class="about__title">Հեղինակ՝ Ալեն Դալլաքյան Կարապետի, Երևանի Ինֆորմատիկայի պետական քոլեջ</h1>
    <img class="about__img" :src="adImg" alt="advertisement">
  </div>
</template>

<style lang="scss" scoped>
.about {
  max-width: 100%;
  &__img {
    width: 100%;
    height: 500px;
    object-fit: cover;
  }
}
</style>