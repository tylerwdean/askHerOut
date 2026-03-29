<template>
  <h1>Location of the date</h1>
  <article>
    <p>
      Please rate your experience at Carowinds! Where the Carolinas Come Together! by selecting the
      option you feel most appropriate to your experience
    </p>

    <label
      ><input type="radio" name="car" v-model="picked" value="5" /> I think I'm in love... *Dreamy
      stare*</label
    >
    <label
      ><input type="radio" name="car" v-model="picked" value="4" /> Yeah, I had a good time</label
    >
    <label
      ><input type="radio" name="car" v-model="picked" value="3" /> Why did he scream so
      much?</label
    >
    <label>
      <input type="radio" name="car" v-model="picked" value="2" /> Lines were long and I had to talk
      to <i>this</i> guy...
    </label>
    <label>
      <input type="radio" name="car" v-model="picked" value="1" /> I wish my seatbelt came
      undone</label
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
