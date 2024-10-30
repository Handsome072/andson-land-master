<template>
  <div id="app">
    <Header />
    <Hero />
    <About />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Hero from './components/Hero.vue';
import About from './components/About.vue';

export default {
  components: {
    Header,
    Hero,
    About,
  },
};
</script>
