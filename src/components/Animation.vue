<script setup>
import { ref, onMounted } from 'vue'

import logoPath from '../assets/logo.svg'

const firstCube = ref(true)
const secondCube = ref(false)
const thirdCube = ref(false)

onMounted(() => {
    setTimeout(() => {
        firstCube.value = false
        secondCube.value = true
    }, 1500)

    setTimeout(() => {
        secondCube.value = false
        thirdCube.value = true
    }, 3000)

    setTimeout(() => {
        thirdCube.value = false
        firstCube.value = true
    }, 4500)

    setTimeout(() => {
        firstCube.value = false
        secondCube.value = true
    }, 6000)

    setTimeout(() => {
        secondCube.value = false
        thirdCube.value = true
    }, 7500)

    setTimeout(() => {
        thirdCube.value = false
    }, 10000)
})


</script>

<template>
  <div class="animation">
    <div class="animation__wrapper">
        <div class="animation__info">
            <p>Գովազդային պատուհան</p>
            <p>Դալլաքյան Ալեն Կարապետի</p>
            <p>05.12.2023</p>
        </div>
        <img v-if="firstCube" :src="logoPath" class="cube1"/>
        <img v-if="secondCube"  :src="logoPath" class="cube2"/>
        <img v-if="thirdCube" :src="logoPath" class="cube3"/>
    </div>
  </div>
</template>

<style lang="scss" scoped>

@keyframes Animation {
    0% {
        right: 10px;
    }

    50% {
        right: 95%;
    }

    75% {
        right: 100%;
    }

    100% {
        right: auto;
        left: 10px;
    }
}


.animation {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    border-radius: 20px;

    &__wrapper {
        position: relative;
        background: #242424;
        width: 500px;
        height: 350px;
        border-radius: 5px;
        box-shadow: 0 10px 15px rgba(0,0,0, .1);
        padding: 10px;
        border-radius: 20px;
    }

    &__info {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
    .cube1, .cube2, .cube3 {
        position: absolute;
        width: 70px;
        height: 70px;
        animation: Animation 2.5s 0.5s forwards;
    }

    .cube1 {
        top: 10px;
        right: 10px;
    }

    .cube2 {
        top: 20%;
        right: 10px;
    }

    .cube3 {
        bottom: 10px;
        right: 10px;
    }
}
</style>