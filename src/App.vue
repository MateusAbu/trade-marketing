<script setup>
import { RouterView } from 'vue-router'
import Header from './components/HeaderComponent.vue'
import { useStore } from 'vuex'

const store = useStore()

store.dispatch('initStocks');
</script>

<template>
    <Header />
      <transition name="slide" mode="out-in">
        <RouterView />
      </transition>
</template>

<style>
  @keyframes slide-in {
    from { transform: translateY(-30px); opacity: 0; } 
    to { transform: translateY(0px); opacity: 1; }
  }

  @keyframes slide-out {
    from { transform: translateY(0px); opacity: 1; } 
    to { transform: translateY(-30px); opacity: 0; }
  }

  .slide-enter-active {
    animation: slide-in 0.3s ease;
  }
  .slide-leave-active {
    animation: slide-out 0.3s ease;
  }

</style>
