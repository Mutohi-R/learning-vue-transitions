<template>
    <div>
        <button @click="toggleShow">toggle</button>
        <!-- <transition
            name="bounce"
        >
            <div v-if="show"><h1>This a conditional element</h1></div>
        </transition> -->

        <transition appear :duration="2800" name="nested">
            <div class="cont" v-if="show">
                <h1>STAGGER ONE</h1>
                <h2>STAGGER TWO</h2>
                <h3>STAGGER THREE</h3>
            </div>
        </transition>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const show = ref(false);

const toggleShow = () => {
    show.value = !show.value
}

</script>

<style scoped>
.fade-enter-from,
.fade-leave-to {
    transform: translateX(100px);
    opacity: 0;
}

.fade-enter-active {
    transition: all 0.3s ease-out;
}

.fade-leave-active {
    transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.bounce-enter-active {
    animation: bounce-in 0.5s;
    transform-origin: top center;
}

.bounce-leave-active {
    animation: bounce-in 0.5s reverse;
}

@keyframes bounce-in {
    0% {
        transform: scale(0);
    }

    50% {
        transform: scale(1.25);
    }

    100% {
        transform: scale(1);
    }
}

.cont {
    color: aliceblue;
    padding: 30px;
    background-color: #333;
}

.cont > * + * {
    margin-top: 20px;
}

.nested-enter-from,
.nested-leave-to {
    opacity: 0;
    transform: translateY(100%);
}

.nested-enter-active {
    transition: all 1s ease;
}

.nested-leave-active {
    transition: all 1s ease-out;
    transition-delay: 1.8s;
}


.nested-enter-from h1,
.nested-leave-to h1 {
    opacity: 0;
    transform: translateX(100px);
}

.nested-enter-active h1 {
    transition: all 1s ease;
    transition-delay: 1s;
}

.nested-leave-active h1 {
    transition: all 1s ease-out;
}
.nested-enter-from h2,
.nested-leave-to h2 {
    opacity: 0;
    transform: translateX(100px);
}

.nested-enter-active h2 {
    transition: all 1s ease;
    transition-delay: 1.5s;
}

.nested-leave-active h2 {
    transition: all 1s ease-out;
    transition-delay: 0.5s;
}
.nested-enter-from h3,
.nested-leave-to h3 {
    opacity: 0;
    transform: translateX(100px);
}

.nested-enter-active h3 {
    transition: all 1s ease;
    transition-delay: 2s;
}

.nested-leave-active h3 {
    transition: all 1s ease-out;
    transition-delay: 1s;
}
</style>