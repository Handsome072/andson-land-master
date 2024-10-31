<template>
  <div id="app">
    <Header />
    <Hero />
    <About />
    <Features />
    <Newsletter />
    <Partner />
     <Testimonial />
       <Pricing />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Hero from "./components/Hero.vue";
import About from "./components/About.vue";
import Features from "./components/Features.vue";
import Newsletter from "./components/Newsletter.vue";
import Partner from "./components/Partner.vue";
import Testimonial from './components/Testimonial.vue';
import Pricing from './components/Pricing.vue';

export default {
  components: {
    Header,
    Hero,
    About,
    Features,
    Newsletter,
    Partner,
      Testimonial,
        Pricing,
  },
};
</script>
