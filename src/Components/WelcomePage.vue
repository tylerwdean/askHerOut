<template>
  <h1>Hello Ingrid!</h1>

  <article>
    <p>If you're seeing this- I hope you had a good time!</p>

    <p>
      We are going to go on a little journey. Please fill out all forms as accuraty as possible!
    </p>

    <p>Please also give all answers verbally as this can't save responses! Thanks!</p>

    <button style="text-centered" @click="emit('continue')">Continue!</button>
  </article>
</template>

<script setup lang="ts">
const emit = defineEmits(['continue']);
</script>
