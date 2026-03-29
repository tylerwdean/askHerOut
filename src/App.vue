<template>
  <Component :is="pages[page]" @continue="onContinue" @goBack="onGoBack" />
</template>

<script setup lang="ts">
import FifthQuestion from './Components/FifthQuestion.vue';
import FirstQuestion from './Components/FirstQuestion.vue';
import FourthQuestion from './Components/FourthQuestion.vue';
import LastPage from './Components/LastPage.vue';
import SecondQuestion from './Components/SecondQuestion.vue';
import SubmitPage from './Components/SubmitPage.vue';
import ThirdQuestion from './Components/ThirdQuestion.vue';
import WelcomePage from './Components/WelcomePage.vue';
import { ref } from 'vue';

const pages = [
  WelcomePage,
  FirstQuestion,
  SecondQuestion,
  ThirdQuestion,
  FourthQuestion,
  FifthQuestion,
  LastPage,
  SubmitPage,
];

const page = ref(0);

const onContinue = () => {
  page.value = page.value + 1;
};

const onGoBack = () => {
  page.value = page.value - 1;
};
</script>

<style scoped></style>
