<template>
  <div id="app">
    <Header />
    <Hero />
    <About />
    <Features />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Hero from "./components/Hero.vue";
import About from "./components/About.vue";
import Features from "./components/Features.vue";

export default {
  components: {
    Header,
    Hero,
    About,
    Features,
  },
};
</script>
