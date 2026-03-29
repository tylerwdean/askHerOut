<template>
  <h1>Cleanliness of the car</h1>
  <article>
    <p>
      Please rate the cleanliness of the car by selecting the option you feel most appropriate to
      your experience
    </p>

    <label
      ><input v-model="picked" type="radio" name="car" value="5" /> I'd eat off the floor- 5 second
      rule</label
    >
    <label
      ><input v-model="picked" type="radio" name="car" value="4" /> Just what's that smell?</label
    >
    <label
      ><input v-model="picked" type="radio" name="car" value="3" /> I see he likes McDonalds</label
    >
    <label
      ><input v-model="picked" type="radio" name="car" value="2" /> Has he heard of a vacuum?</label
    >
    <label
      ><input v-model="picked" type="radio" name="car" value="1" /> Ew, mom please pick me up
    </label>

    <div v-if="showError">
      <p>You gotta pick one... ok?</p>
    </div>

    <br />

    <button @click="beforeContinue">Continue</button>
  </article>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const emit = defineEmits(['continue']);

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
