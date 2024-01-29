<template>
  <main>
    <!-- <appear /> -->
    <!-- <elements-trans /> -->
    <!-- <stagger /> -->
    <!-- <list /> -->
    <text-reveal />
  </main>
</template>

<script setup>
  import gsap from 'gsap';

  import appear from './components/appear.vue';
  import stagger from './components/Stagger.vue';
  import ElementsTrans from './components/ElementsTrans.vue';
  import List from './components/List.vue';
  import TextReveal from './components/TextReveal.vue';

</script>

<style scoped>
  .container {
    width: min(400px, 100% - 3rem);
    /* border: 2px solid red; */
    margin-inline: auto;
  }

  .box__container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
  }

  .box {
    width: 150px;
    height: 150px;
    margin: 20px;
    background-color: #333;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  }

  .boxx__container {
    margin-top: 120px;
    display: flex;
  }

  .boxx {
    width: 100px;
    height: 100px;
    background-color: #333;
    /* box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);   */
  }
</style>
