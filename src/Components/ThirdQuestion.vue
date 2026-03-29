<template>
  <h1>Mass</h1>
  <article>
    <p>
      Please rate your experience at Mass by selecting the option you feel most appropriate to your
      experience
    </p>

    <label
      ><input type="radio" name="mass" v-model="picked" value="5" /> Literally Heaven on
      Earth</label
    >
    <label
      ><input type="radio" name="mass" v-model="picked" value="4" /> He was a little too excited
      when he heard latin</label
    >
    <label
      ><input type="radio" name="mass" v-model="picked" value="3" /> Why did he cry
      <i>sooo</i> much?</label
    >
    <label>
      <input type="radio" name="mass" v-model="picked" value="2" /> Mass was good, but that singing?
      *shivers*
    </label>
    <label>
      <input type="radio" name="mass" v-model="picked" value="1" /> I think I'm gonna need to be
      re-baptized</label
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
