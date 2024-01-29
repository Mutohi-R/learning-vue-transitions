<template>
  <div style="margin-top: 20px;">
    Click to cycle through the states:
    <Transition name="slide-up" mode="out-in">
      <button v-if="docState === 'saved'" @click="docState = 'editing'">
        Edit
      </button>
      <button v-else-if="docState === 'edited'" @click="docState = 'saved'">
        Save
      </button>
      <button v-else-if="docState === 'editing'" @click="docState = 'edited'">
        Cancel
      </button>
    </Transition>
  </div>
</template>

<script setup>
import { ref } from "vue";

const docState = ref("saved");

</script>

<style scoped>
button {
  padding: 10px 20px;
  margin-left: 10px;
}

.slide-up-enter-from {
    opacity: 0;
    transform: translateY(100%);
}

.slide-up-leave-to {
    opacity: 0;
    transform: translateY(-100%);
}

.slide-up-enter-active {
    transition: all 0.4s ease;
}

.slide-up-leave-active {
    /* position: absolute not needed when using mode="out-in" */
    /* position: absolute; */
    transition: all 0.4s ease;
}
</style>
