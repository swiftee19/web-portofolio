<script setup lang="ts">
import { RouterLink } from 'vue-router'

defineProps({
  buttonText: {
    type: String,
    required: true
  },
  viewDestination: {
    type: String,
    required: true
  },
  currentRoute: {
    type: String,
    required: true
  }
})

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}
</script>

<template>
  <RouterLink :to="viewDestination" @click="scrollToTop"
    class="navbar-button relative decoration-0 text-lg transition-all duration-300 hover:cursor-pointer hover:text-gold"
    :class="{ 'text-gold': viewDestination == currentRoute, 'text-text': viewDestination != currentRoute }">{{
      buttonText }}</RouterLink>
</template>

<style>
.navbar-button::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 1px;
  background: var(--gold-color);
  transform: scaleX(0);
  transform-origin: bottom right;
  transition: transform var(--transition-duration) var(--transition-timing-function);
}

.navbar-button:hover::after {
  transform: scaleX(1);
  transform-origin: bottom left;
}
</style>
