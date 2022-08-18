<template>
  <Suspense>
    <template #default>
      <Home />
    </template>
    <template #fallback>
      <SplashScreen />
    </template>
  </Suspense>
</template>

<script>
import SplashScreen from '@/components/SplashScreen.vue'
import { defineAsyncComponent } from 'vue'
export default {
  components: {
    SplashScreen,
    Home: defineAsyncComponent(() => new Promise((resolve) => {
      setTimeout(() => {
        resolve(import('./components/Home.vue'))
      }, 2500)
    }))
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    font-size: 1.6rem;
  }
  html {
    font-size: 62.5%;
    font-family: Arial, Helvetica, sans-serif
  }
  body {
    margin: 0;
    padding: 0;
  }

  :root {
    --brand-green: #04b500;
    --brand-blue: #0689b0;
  }

  .app {
    min-height: 100vh;
    margin: 0;
  }
</style>
