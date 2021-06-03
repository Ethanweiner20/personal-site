<template>
  <router-view v-slot="{ Component }">
    <transition :name="transitionName">
      <component :is="Component"></component>
    </transition>
  </router-view>
</template>

<script>
import { onMounted } from '@vue/runtime-core'
import { transitionName } from './store'

export default {
  name: 'App',
  setup() {
    return { transitionName }
  }
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}
body,
html {
  position: fixed;
  background-color: rgb(27, 27, 27);
  width: 100%;
  height: 100%;
}
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;

  margin: 0;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* route transitions */
.fade-enter-active,
.fade-leave-active {
  transition-property: opacity;
  transition-duration: 0.5s;
}

.fade-enter-active {
  transition-delay: 0.25s;
}

.fade-enter,
.fade-leave-active {
  opacity: 0;
}

/* zoom transition */
.zoom-enter-active,
.zoom-leave-active {
  animation-duration: 1s;
  animation-fill-mode: both;
  animation-name: zoom;
}
.zoom-leave-active {
  animation-direction: reverse;
}
// Define the zoom animation here: Fade and scale
@keyframes zoom {
  from {
    opacity: 0;
    transform: scale3d(0.3, 0.3, 0.3);
  }
  100% {
    opacity: 1;
  }
}
</style>
