<template>
  <section id="features">
    <div class="container mx-auto">
      <div class="section-title text-center mb-12 fadeInUp" ref="sectionTitle">
        <h2>Features</h2>
        <p>
          Most calendars are designed for teams. Slate is designed for freelancers.
        </p>
      </div>

      <div class="features-list grid grid-cols-1 md:grid-cols-3 gap-8 justify-items-center text-center">
        <div
          v-for="(feature, index) in features"
          :key="index"
          :class="['feature', animationClasses[index]]"
          ref="features"
        >
          <img :src="feature.img" alt="" class="feature-img mx-auto mb-4" />
          <h3>{{ feature.title }}</h3>
          <p class="text-gray-500">{{ feature.description }}</p>
        </div>
      </div>

      <!-- Video section with animation -->
      <figure class="features-video fadeInUp" ref="featuresVideoSection">
        <button class="play absolute inset-0 flex items-center justify-center z-10" @click="playVideo">
          <img loading="lazy" src="@/assets/images/el_play.svg" alt="Play" />
        </button>
        <video ref="featuresVideo" poster="@/assets/images/screenthumbnail-video.jpg" class="w-full rounded-lg">
          <source src="@/assets/images/features.mp4" type="video/mp4" />
          Your browser does not support video.
        </video>
      </figure>
    </div>
  </section>
</template>

<script>
import mdiDrawing from '@/assets/images/mdi_drawing.svg';
import mdiDraw from '@/assets/images/mdi_draw.svg';
import mdiBrush from '@/assets/images/mdi_brush.svg';

export default {
  data() {
    return {
      features: [
        {
          img: mdiDrawing,
          title: 'OpenType features Variable fonts',
          description: 'Slate helps you see how many more days you need to work to reach your financial goal.',
        },
        {
          img: mdiDraw,
          title: 'Design with real data',
          description: 'Slate helps you see how many more days you need to work to reach your financial goal.',
        },
        {
          img: mdiBrush,
          title: 'Fastest way to take action',
          description: 'Slate helps you see how many more days you need to work to reach your financial goal.',
        },
      ],
      animationClasses: ['fadeInLeft', 'fadeInUp', 'fadeInRight'], // Different animations for each feature
      sectionTitleVisible: false, // Track visibility of section-title
      featuresVisible: false, // Track if features-list animation has been triggered
      videoVisible: false, // Track if video animation has been triggered
    };
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    playVideo() {
      const video = this.$refs.featuresVideo;
      video.play();
      video.setAttribute('controls', 'controls');
      this.$el.querySelector('.play').style.display = 'none';
    },
    handleScroll() {
      const sectionTitle = this.$refs.sectionTitle;
      const sectionTitleRect = sectionTitle.getBoundingClientRect();
      const windowHeight = window.innerHeight || document.documentElement.clientHeight;

      // Trigger section title animation
      if (sectionTitleRect.top <= windowHeight - 200 && !this.sectionTitleVisible) {
        sectionTitle.classList.add('visible');
        this.sectionTitleVisible = true;
      }

      // Trigger features-list animation if the first feature is in view
      const features = this.$refs.features;
      const firstFeature = features[0];
      const firstFeatureRect = firstFeature.getBoundingClientRect();

      if (firstFeatureRect.top <= windowHeight - 500 && !this.featuresVisible) {
        features.forEach((feature) => {
          feature.classList.add('visible');
        });
        this.featuresVisible = true;
      }

      // Trigger video section animation
      const videoSection = this.$refs.featuresVideoSection;
      const videoSectionRect = videoSection.getBoundingClientRect();

      if (videoSectionRect.top <= windowHeight - 300 && !this.videoVisible) {
        videoSection.classList.add('visible');
        this.videoVisible = true;
      }
    },
  },
};
</script>

<style scoped>
.section-title {
  width: 100%;
  max-width: 545px;
  margin: auto;
  color: var(--text-color);
  text-align: center;
  margin-bottom: 80px;
}

.section-title h2 {
  line-height: 1.8;
  text-align: center;
  letter-spacing: 0.2px;
  margin-bottom: 17px;
}

.section-title p {
  line-height: 1.8;
}

.features-list {
  width: 100%;
  margin: 0 auto;
  text-align: center;
  display: grid;
  column-gap: 52px;
}

.features-video {
  position: relative;
  width: 100%;
  min-width: 500px;
  margin-top: 40px;
  opacity: 0;
  transform: translateY(100px);
  transition: opacity 0.8s ease-out, transform 0.8s ease-out;
}

.features-video.visible {
  opacity: 1;
  transform: translateY(0);
}

.features-video video {
  width: 100%;
  min-width: 500px;
  height: auto;
  border-radius: 44.8123px;
  cursor: pointer;
}

button.play {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 2;
  width: calc(10vw + 10px);
  height: calc(10vw + 10px);
  min-width: 80px;
  min-height: 80px;
  max-width: 120px;
  max-height: 120px;
  border-radius: 50%;
  background-color: var(--primary);
  filter: var(--drpshdw);
}

button.play img {
  width: 30%;
  padding-left: 5px;
  height: auto;
}

.play {
  transition: opacity 0.3s ease-in-out;
}

.play:hover {
  opacity: 0.8;
}

.feature {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

/* Animation styles */
.fadeInUp, .fadeInLeft, .fadeInRight {
  opacity: 0;
  transition: opacity 0.8s ease-out, transform 0.8s ease-out;
}

.fadeInUp {
  transform: translateY(300px);
}

.fadeInLeft {
  transform: translateX(-300px);
}

.fadeInRight {
  transform: translateX(300px);
}

.fadeInUp.visible,
.fadeInLeft.visible,
.fadeInRight.visible {
  opacity: 1;
  transform: translate(0, 0);
}

.section-title.fadeInUp {
  opacity: 0;
  transform: translateY(100px);
  transition: opacity 1s ease-out, transform 1s ease-out;
}

.section-title.fadeInUp.visible {
  opacity: 1;
  transform: translateY(0);
}

#features h3 {
  margin: 20px 0 0;
  padding: 10px;
  font-style: normal;
  line-height: 1.4;
  max-width: 300px;
}

#features p {
  line-height: 1.8;
  padding: 10px;
}

/* Image rotation on hover */
.feature-img {
  transition: transform 0.5s ease;
}

.feature:hover{
  cursor:pointer;
}

.feature:hover .feature-img {
  transform: rotate(360deg);
 
}
</style>
