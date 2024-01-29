<template>
  <header>
    <h1 ref="el" id="text">Text.Appear</h1>
  </header>
  <main>
    <div class="papapa">
        <p ref="para1" class="para para1">
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Autem, harum.
        </p>
    </div>
    <div style="display: flex; gap: 2rem;">
        <p class="para para2">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Ullam autem,
          magnam praesentium obcaecati ex ut commodi magni iste totam maxime
          adipisci veritatis temporibus nisi qui?
        </p>
        <p class="para para3">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Ullam autem,
          magnam praesentium obcaecati ex ut commodi magni iste totam maxime
          adipisci veritatis temporibus nisi qui?
        </p>
    </div>
    <p ref="para4" class="para para4">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Ullam autem,
      magnam praesentium obcaecati ex ut commodi magni iste totam maxime
      adipisci veritatis temporibus nisi qui?
    </p>
    <div style="display: flex; gap: 1rem;">
      <div class="circle"></div>
      <div class="circle"></div>
      <div class="circle"></div>
      <div class="circle"></div>
      <div class="circle"></div>
    </div>
  </main>
</template>

<script setup>
import { ref, onMounted } from "vue";
import gsap from "gsap";
import splitType from "split-type";

const el = ref(null);
const para1 = ref(null);
const para4 = ref(null);

onMounted(() => {
  const text = new splitType(el.value);
  const para = new splitType(para1.value);
  const para2 = new splitType(para4.value);
  const tl = gsap.timeline();

  tl.from("h1 .char", {
    y: 100,
    stagger: 0.05,
    duration: 1,
    ease: "back.out(1.7)",
  });

  tl.from('.para1 .word', {
    opacity: 0,
    y: '-100%',
    duration: .5,
    stagger: 0.1
  })

  tl.from('.para2', {
    opacity: 0,
    x: '-100%',
    duration: .5
  })

  tl.from('.para3', {
    opacity: 0,
    x: '100%',
    duration: .5
  }, '-=.5')

  tl.from('.para4 .word', {
    opacity: 0,
    y: '-100%',
    duration: .5,
    stagger: 0.1,
    ease: 'back'
  })

  tl.from('.circle', {
    opacity: 0,
    x: '-100%',
    duration: .5,
    stagger: 0.1
  })
});
</script>

<style scoped>
header {
  /* display: grid;
        place-content: center;
        height: 100vh; */
}

h1 {
  font-size: 5rem;
  line-height: 1.1;
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
  clip-path: polygon(0 0, 100% 0, 100% 100%, 0% 100%);
}

.para {
  font-size: 1.5rem;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.papapa {
    /* clip-path: polygon(0 0, 50% 0, 50% 100%, 0% 100%); */
    clip-path: polygon(0 0, 100% 0, 100% 100%, 0% 100%);
}

.circle {
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background-color: blue;
}
</style>
