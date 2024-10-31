<template>
  <section id="testimonials" :class="{ 'show': isVisible }" ref="testimonialsSection">
    <div class="container">
      <div class="section-title">
        <h2>Testimonials</h2>
        <p>See what our clients say.</p>
      </div>
      <div class="testimonials-slider">
        <div
          class="testimoni-wrapper"
          :style="{ transform: `translateX(-${currentIndex * 100}%)` }"
        >
          <div
            v-for="(testimonial, index) in testimonials"
            :key="index"
            class="testimoni"
          >
            <q>{{ testimonial.message }}</q>
            <div class="testimoni-author">
              <img
                loading="lazy"
                class="testimoni-author-avatar"
                :src="testimonial.avatar"
                alt=""
              />
              <span class="testimoni-author-name">{{ testimonial.name }}</span>
              <span class="testimoni-author-role">{{ testimonial.role }}</span>
            </div>
          </div>
        </div>
      </div>

      <button
        class="testimoni-prev"
        @click="prevSlide"
        title="Previous"
      ></button>
      <button class="testimoni-next" @click="nextSlide" title="Next"></button>

      <div class="testimonial-index-poin">
        <span
          v-for="(testimonial, index) in testimonials"
          :key="index"
          class="index-poin"
          :class="{ active: index === currentIndex }"
          @click="setCurrentIndex(index)"
        ></span>
      </div>
      <button class="main">More Testimonials</button>
    </div>
  </section>
</template>

<script>
import avatar from '@/assets/images/avatar/avatar-1.jpg';

export default {
  name: 'Testimonials',
  data() {
    return {
      currentIndex: 0,
      isVisible: false,
      testimonials: [
        {
          message:
            'Lorem ipsum dolor sit amet consectetur adipisicing. Lorem ipsum dolor sit amet consectetur',
          name: 'Lorem Ipsum Ipsum',
          role: 'UI Designer',
          avatar: avatar,
        },
        {
          message:
            'Lorem ipsum dolor sit amet consectetur adipisicing. Lorem ipsum dolor sit amet consectetur, adipisicing elit. Placeat, aliquam! Lorem ipsum dolor sit amet.',
          name: 'Lorem',
          role: 'UI Designer',
          avatar: avatar,
        },
        {
          message:
            'Lorem ipsum dolor sit amet consectetur adipisicing. Lorem ipsum dolor sit amet consectetur, adipisicing elit. Placeat, aliquam!',
          name: 'Lorem Ipsum',
          role: 'UI Designer',
          avatar: avatar,
        },
      ],
    };
  },
  methods: {
    nextSlide() {
      this.currentIndex = (this.currentIndex + 1) % this.testimonials.length;
    },
    prevSlide() {
      this.currentIndex =
        (this.currentIndex - 1 + this.testimonials.length) % this.testimonials.length;
    },
    setCurrentIndex(index) {
      this.currentIndex = index;
    },
    handleScroll(entries) {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          this.isVisible = true;
        }
      });
    },
  },
  mounted() {
    const observer = new IntersectionObserver(this.handleScroll, {
      threshold: 0.5,
    });
    observer.observe(this.$refs.testimonialsSection);

    setInterval(this.nextSlide, 5000);
  },
};
</script>

<style scoped>
#testimonials .section-title {
  margin-bottom: 0px;
}

#testimonials .container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column; 
  position: relative;
}

#testimonials .testimonials-slider {
  width: 100%;
  max-width: 900px; 
  height: auto;
  overflow: hidden;
}

.testimonials-slider .testimoni-wrapper {
  display: flex;
  transition: transform 0.5s ease;
  width: 100%;
}

.testimonials-slider .testimoni {
  min-width: 100%; 
  box-sizing: border-box; 
  text-align: center;
  line-height: 1.8;
  padding: 30px;
  display: flex;
  flex-direction: column;
  gap: 60px;
  margin: 80px 0 20px;
  transition: 0.8s;
}

.testimonials-slider .testimoni .testimoni-message {
  font-style: italic;
  width: 80%;
  margin: 0 auto;
}

.testimonials-slider .testimoni .testimoni-author {
  width: max-content;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(2, auto);
  row-gap: 0;
  column-gap: 15px;
  grid-template-areas:
    'avatar name'
    'avatar role';
  text-align: left;
  line-height: 1;
}

.testimonials-slider .testimoni .testimoni-author-avatar {
  grid-area: avatar;
  width: 50px;
  height: 50px;
  margin: auto;
  border-radius: 50%;
}

.testimonials-slider .testimoni .testimoni-author-name {
  grid-area: name;
  font-weight: 500;
  display: flex;
  align-items: center;
}

.testimonials-slider .testimoni .testimoni-author-role {
  grid-area: role;
  font-weight: 400;
  display: flex;
  align-items: center;
  font-size: 1.4em;
}

.testimonial-index-poin {
  width: max-content;
  margin: 0 auto 110px;
  display: flex;
  flex-direction: row;
  gap: 10px;
}

.testimonial-index-poin span.index-poin {
  display: block;
  width: clamp(10px, 1vw, 16px);
  height: clamp(10px, 1vw, 16px);
  background: var(--text-color);
  opacity: 0.2;
  border-radius: 50%;
  cursor: pointer;
  transition: 0.8s;
}

span.index-poin.active {
  opacity: 0.8;
}

#testimonials {
  opacity: 0;
  transform: translateY(100px);
  transition: opacity 0.8s ease, transform 0.8s ease;
}

#testimonials.show {
  opacity: 1;
  transform: translateY(0);
}

#testimonials .section-title {
  margin-bottom: 0px;
}

/* Contrôles */

button.testimoni-prev,
button.testimoni-next {
  all: unset;
  width: 40px;
  height: 40px;
  background-size: 100%;
  border-radius: 50%;
  cursor: pointer;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
}

button.testimoni-prev {
  left: 0;
  background: url(@/assets/images/ic_round-navigate-pref.svg) no-repeat center;
}

button.testimoni-next {
  right: 0;
  background: url(@/assets/images/ic_round-navigate-next.svg) no-repeat center;
}

/* Styles pour écrans de 560px et moins */

@media (max-width: 560px) {
  #testimonials .testimonials-slider {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .testimonials-slider .testimoni {
    padding: 20px; 
    width: 90%;
  }

  .testimonial-index-poin {
    justify-content: center;
  }
}
</style>
