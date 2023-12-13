<script setup>
import { ref } from 'vue'

import HomeView from './HomeView.vue'
import AboutView from './AboutView.vue'
import HelpView from './HelpView.vue'

import Swal from 'sweetalert2'

const emit = defineEmits(['logout'])

const currentPage = ref('home')
const menuVertical = ref(false)

const openLogoutModal = () => {
  Swal.fire({
    title: 'Իսկապե՞ս ուզում եք դուրս գալ:',
    text: 'Դուք դուրս կգրվեք ձեր հաշվից:',
    icon: 'warning',
    showCancelButton: true,
    confirmButtonColor: '#3085d6',
    cancelButtonColor: '#d33',
    confirmButtonText: 'Հաստատել',
    cancelButtonText: 'Չեղարկել'
  }).then((result) => {
    if (result.isConfirmed) {
      handleLogout();
    }
  });
}

const openHelpModal = () => {
  Swal.fire({
    title: 'Ինֆորմացիոն պատուհան',
    text: 'Օգնության թեմա',
    icon: 'question',
  });
}

const openTipModal = () => {
  Swal.fire({
    title: 'Օրվա խորհուրդ',
    text: `
    Դիտեք յուրաքանչյուր օրը որպես հաջողության նոր հնարավորություն
    `,
    icon: 'info',
  });
}

const handleLogout = () => {
  emit('logout')
};
</script>

<template>
  <div class="main">
    <h1 class="main__title">Գովազդային հավելված</h1>
    <div class="main__header" :class="{[`main__header-vertical`]: menuVertical}">
      <button @click="menuVertical = !menuVertical">Դասավորել</button>
      <button @click="openHelpModal">Օգնության պատուհան</button>
      <button @click="openTipModal">Օրվա Խորհուրդ</button>
      <button @click="currentPage = 'home'">Գլխավոր</button>
      <button @click="currentPage = 'about'">Մեր Մասին</button>
      <button @click="currentPage = 'help'">Օգնություն</button>
      <button @click="openLogoutModal">Դուրս գալ</button>
    </div>
    <home-view v-if="currentPage === 'home'" />
    <about-view v-if="currentPage === 'about'" />
    <help-view v-if="currentPage === 'help'" />
  </div>
</template>

<style lang="scss" scoped>
.main {
    background: #242424;
    padding: 30px;
    width: calc(100% - 50px);
    border-radius: 20px;

    &__title {
      margin-top: 0;
      text-align-last: left;
    }

    &__header {
      display: flex;
      align-items: flex-start;
      gap: 10px;
      margin-bottom: 20px;

      &-vertical {
        flex-direction: column;
      }
    }
}
</style>