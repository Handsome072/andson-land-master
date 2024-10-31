<template>
  <section id="partners" class="py-16">
    <div class="container">
      <!-- Section Title -->
      <div class="section-title animate-on-scroll" ref="sectionTitle">
        <h2 class="text-3xl font-bold">Partners</h2>
        <p class="text-gray-500">
          Most calendars are designed for teams. Slate is designed for freelancers.
        </p>
      </div>

      <!-- Partners List -->
      <div class="partners-list">
        <img
          v-for="(partner, index) in partners"
          :key="index"
          :src="partner.src"
          :alt="partner.alt"
          class="partner-img animate-partner"
          :style="{ animationDelay: `${index * 0.3}s` }"
          ref="partnerImages"
        />
      </div>
    </div>
  </section>
</template>

<script>
import gglImage from '@/assets/images/ggl.jpg';
import amzImage from '@/assets/images/amz.jpg';
import msImage from '@/assets/images/ms.jpg';
import ubrImage from '@/assets/images/ubr.jpg';
import dbImage from '@/assets/images/db.jpg';

export default {
  name: 'PartnersSection',
  data() {
    return {
      partners: [
        { src: gglImage, alt: 'Google' },
        { src: amzImage, alt: 'Amazon' },
        { src: msImage, alt: 'Microsoft' },
        { src: ubrImage, alt: 'Uber' },
        { src: dbImage, alt: 'Dropbox' },
      ],
    };
  },


  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      const sectionTitle = this.$refs.sectionTitle;
      const partnerImages = this.$refs.partnerImages;

      if (sectionTitle.getBoundingClientRect().top < window.innerHeight - 200) {
        sectionTitle.classList.add('visible');
      }

      partnerImages.forEach((img, index) => {
        if (img.getBoundingClientRect().top < window.innerHeight - 200) {
          img.classList.add('visible');
        }
      });
    },
  },
};
</script>

<style scoped>
section .container {
  max-width: 1440px;
  margin: auto auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 10px 40px;
}

.partners-list {
  margin: 80px 40px;
  display: grid;
  gap: 80px;
  grid-template-columns: repeat(6, 1fr);
  grid-template-rows: repeat(2, 1fr);
  grid-template-areas:
    'one one two two three three'
    '. four four five five .';
}

.partners-list img {
  display: inline;
  width: auto;
  height: 50px;
  margin: auto;
}

.partners-list img:nth-child(1) {
  grid-area: one;
}
.partners-list img:nth-child(2) {
  grid-area: two;
}
.partners-list img:nth-child(3) {
  grid-area: three;
}
.partners-list img:nth-child(4) {
  grid-area: four;
}
.partners-list img:nth-child(5) {
  grid-area: five;
}

@media (max-width: 560px) {
  .partners-list {
    margin: 80px 40px;
    display: grid;
    gap: 80px;
    grid-template-columns: auto;
    grid-template-rows: repeat(6, auto);
    grid-template-areas:
      'one'
      'two'
      'three'
      'four'
      'five'
      '.';
  }
}

.section-title {
  opacity: 0;
  transform: translateY(100px);
  transition: opacity 0.5s ease-out, transform 0.5s ease-out;
}

.section-title.visible {
  opacity: 1;
  transform: translateY(0);
}

/* Animation for partner images */
.partner-img {
  opacity: 0;
  transform: translateX(100px);
  transition: opacity 1s ease-out, transform 1s ease-out;
}

.partner-img.visible {
  opacity: 1;
  transform: translateX(0);
}
</style>
