<script setup lang="ts">
import { defineAsyncComponent } from 'vue';
import SplashScreen from '@/components/SplashScreen.vue';

const Home = defineAsyncComponent(() =>
  new Promise((resolve) => {
    setTimeout(() => {
      resolve(import('./components/Home.vue'));
    }, 2500)
  })
)
</script>

<template>
  <Suspense>
    <template #default>
      <Home/>  
    </template>
    <template #fallback>
      <SplashScreen/>
    </template>
  </Suspense>
</template>

<style scoped>
  html,
  body,
  .app {
    min-height: 100vh;
    margin: 0;
    font-family: Arial, Helvetica, sans-serif;
  }

  * {
    --brand-green: #04b500;
    --brand-blue: #0689b0;
  }
</style>
