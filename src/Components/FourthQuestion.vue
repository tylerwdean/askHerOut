<template>
  <h1>Eating out</h1>
  <article>
    <p>
      Please rate your experience eating out by selecting the option you feel most appropriate to
      your experience
    </p>

    <label
      ><input type="radio" name="mass" v-model="picked" value="5" /> Great food with great
      company!</label
    >
    <label
      ><input type="radio" name="mass" v-model="picked" value="4" /> Except for that time where he
      got a little food on his mouth and it looked silly</label
    >
    <label
      ><input type="radio" name="mass" v-model="picked" value="3" /> Or the time he asked me if I
      was going to finish that</label
    >
    <label>
      <input type="radio" name="mass" v-model="picked" value="2" /> Or the time when he ordered it
      spicy but <i>really</i> can't take it
    </label>
    <label>
      <input type="radio" name="mass" v-model="picked" value="1" /> Actually, I should've packed a
      lunch</label
    >

    <div v-if="showError">
      <p>You gotta pick one... ok?</p>
    </div>

    <br />
    <div>
      <button @click="beforeContinue">Continue</button> <text> </text>
      <button @click="emit('goBack')">Go Back</button>
    </div>
  </article>
</template>

<script setup lang="ts">
import { ref } from 'vue';
const emit = defineEmits(['continue', 'goBack']);

const picked = ref(0);
const showError = ref(false);

const beforeContinue = () => {
  if (!picked.value) {
    showError.value = true;
    return;
  }

  emit('continue', { picked: picked.value });
};
</script>
