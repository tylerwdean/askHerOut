<template>
  <h1>Do it again?</h1>
  <article>
    <p>Please rate how likely you are to go on another date again</p>

    <label
      ><input type="radio" name="mass" v-model="picked" value="5" /> You know, I think I'd like that
      :&rpar;</label
    >
    <label
      ><input type="radio" name="mass" v-model="picked" value="4" /> Maybe if he asks with finger
      guns
    </label>
    <label
      ><input type="radio" name="mass" v-model="picked" value="3" /> Not feeling it, but I have some
      friends who would!
    </label>
    <label>
      <input type="radio" name="mass" v-model="picked" value="2" /> No, I love my friends too much
      to let them date him
    </label>
    <label>
      <input type="radio" name="mass" v-model="picked" value="1" /> He should reconsider priesthood.
      Yikes.
    </label>

    <div v-if="showError">
      <p>You gotta pick one... ok?</p>
    </div>

    <br />
    <div>
      <button @click="beforeContinue">Finish</button> <text> </text>
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
