<template>
    <section class="container">
    <transition-group 
        appear
        @before-enter="beforeBoxEnter"
        @enter="boxEnter"
        @after-enter="afterBoxEnter"
        tag="article" 
        class="box__container"
    >
        <div key=1 :data-set="0" class="box box1"></div>
        <div key=2 :data-set="1" class="box box2"></div>
        <div key=3 :data-set="2" class="box box3"></div>
        <div key=4 :data-set="3" class="box box4"></div>
    </transition-group>

    <transition
        appear
        @before-enter="beforeSingleBoxEnter"
        @enter="singleBoxEnter"
        @after-enter="afterSingleBoxEnter"
    >
        <div class="box"></div>
    </transition>

        <transition
        appear
        @before-enter="beforeBoxxEnter"
        @enter="boxxEnter"
        >
        <div class="boxx__container">
            <transition
            appear
            @enter="box1Enter"
            >
            <div class="boxx"></div>
            </transition>
            <transition
            appear
            @enter="box2Enter"
            >
            <div class="boxx"></div>
            </transition>
            <transition
            appear
            @enter="box3Enter"
            >
            <div class="boxx"></div>
            </transition>
            <transition
            appear
            @enter="box4Enter"
            >
            <div class="boxx"></div>
            </transition>
        </div>
        </transition>
    </section>
  </template>
  
  <script setup>
    import gsap from 'gsap';
  
    const beforeBoxEnter = (el) => {
      gsap.set(el, {
        opacity: 0,
        scale: 0,
      })
    }
  
    const boxEnter = (el, done) => {
      gsap.to(el, {
        opacity: 1,
        scale: 1,
        // translateY: 0,
        // translateX: 0,
        duration: 1.5,
        delay: el.dataset.set * .7,
        onComplete: done,
      })
    }
  
    const beforeSingleBoxEnter = (el) => {
      gsap.set(el, {
        opacity: 0,
        scale: 0,
        borderRadius: '0px'
      })
    }
  
    const singleBoxEnter = (el, done) => {
      gsap.to(el, {
        opacity: 1,
        duration: 3,
        borderRadius: '50%',
        scale: 1,
        onComplete: done
      })
    }
  
    const afterSingleBoxEnter = (el, done) => {
      gsap.to(el, {
        x: 300,
        backgroundColor: 'rebeccaPurple',
        duration: 1,
      })
    }
  
    const beforeBoxxEnter = (el, done) => {
      el.style.opacity = 0;
      el.style.transform = 'translateY(100%)'
    }
  
    const boxxEnter = (el, done) => {
      gsap.to(el, {
        opacity: 1,
        y: 0,
        duration: 2,
        onComplete: done
      })
    }
  
    const box1Enter = (el) => {
      gsap.to(el, {
        backgroundColor: 'red',
        duration: 2,
        delay: 2,
      })
    }
  
    const box2Enter = (el) => {
      gsap.to(el, {
        x: -100,
        y: -110,
        backgroundColor: 'blue',
        duration: 2,
        delay: 3,
      })
    }
  
    const box3Enter = (el) => {
      gsap.to(el, {
        x: -90,
        backgroundColor: 'green',
        duration: 2,
        delay: 4,
      })
    }
  
    const box4Enter = (el) => {
      gsap.to(el, {
        x: -190,
        y: -110,
        backgroundColor: 'yellow',
        duration: 2,
        delay: 5,
      })
    }
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
  