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
  import {defineAsyncComponent} from 'vue'; 
  import Home from '@/views/Home.vue';
  import SplashScreen from '@/components/SplashScreen.vue';

  export default {
    components: {
      Home: defineAsyncComponent(() => {
        return new Promise((resolve) => {
          setTimeout(() =>  {
            resolve(import('./views/Home.vue')); 
          }, 1000);
        })
      }),
      SplashScreen
    },
  };
</script>

<style></style>
