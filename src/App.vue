<template>
  <v-app class="grey lighten-4">
    <Navbar />

    <v-main class="mx-16">
      <router-view msg="Pratik is here"></router-view>
      <!-- <HelloWorld/> -->
      <!-- <Home msg="Pratik is here" /> -->
    </v-main>
  </v-app>
</template>

<script>
import Navbar from '@/components/Navbar';
// import HelloWorld from './components/HelloWorld';
// import Home from './components/Home.vue';

export default {
  name: 'App',

  components: {
    Navbar
  //   HelloWorld,
  //   Home
  },

  data: () => ({
    
  }),
};
</script>
