<template>
  <section id="newsletter" ref="newsletterSection" :class="{'scrolled': hasScrolled}">
    <div class="container">
      <div class="newsletter-left w-full md:w-1/2">
        <img
          loading="lazy"
          src="@/assets/images/ilustration/undraw_newsletter_vovu.svg"
          alt="newsletter illustration"
          class="mx-auto"
          :class="{'animate': imageAnimationCompleted}"
        />
      </div>
      <div class="newsletter-right w-full md:w-1/2 mt-8 md:mt-0 md:ml-12" :class="{'show': imageAnimationCompleted}">
        <span :class="{'animate': hasScrolled}">At your Fingertips</span>
        <h3 class="bold"  :class="{'animate': hasScrolled}">Lightning fast prototyping</h3>
        <p :class="{'animate': hasScrolled}">Subscribe to our Newsletter</p>
        <p class="text-gray-500" :class="{'animate': hasScrolled}">Available exclusively on Figmaland</p>
        <form @submit.prevent="subscribe" :class="{'animate': hasScrolled}">
          <label for="input-mail-at-newsletter" class="sr-only">Email</label>
          <input
            required
            type="email"
            name="email"
            id="input-mail-at-newsletter"
            placeholder="Your Email"
            v-model="email"
            @invalid="setInvalid"
          />
          <button type="submit" class="main">Subscribe</button>
        </form>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      hasScrolled: false,
      imageAnimationCompleted: false,
    };
  },
  mounted() {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            this.hasScrolled = true;
            this.animateImageFirst();
            observer.disconnect(); 
          }
        });
      },
      { threshold: 0.1 }
    );
    observer.observe(this.$refs.newsletterSection);
  },
  methods: {
    animateImageFirst() {
      // Délai pour simuler l'animation de l'image avant de passer au reste
      setTimeout(() => {
        this.imageAnimationCompleted = true;
      }, 1000); 
    },
    subscribe() {
      console.log(`Email subscribed: ${this.email}`);
      this.email = '';
    },
    setInvalid(event) {
      event.target.style.outline = '1px solid red';
      event.target.setCustomValidity('Email cannot be blank');
    },
  },
};
</script>

<style scoped>
 body{
      font-family: var(--font-family);
 }
.newsletter-left img,
.newsletter-right {
  opacity: 0;
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.newsletter-left img.animate {
  animation: rotateScaleUp 0.5s forwards;
}

.newsletter-right {
  transform: translateX(50px);
  opacity: 0; 
}

.newsletter-right span,
.newsletter-right h3,
.newsletter-right p,
.newsletter-right form{
  opacity: 0; 
}

.newsletter-right.show {
  opacity: 1; 
  transform: translateX(0);
  transition: opacity 1s ease, transform 1s ease;
}

.newsletter-right span.animate {
  animation: fadeInRight 0.5s 1.2s forwards;
}

.newsletter-right h3.animate {
  animation: fadeInRight 0.5s 1.4s forwards;
}

.newsletter-right p.font-bold.animate {
  animation: fadeInRight 0.5s 1.6s forwards;
}

.newsletter-right p:not(.font-bold).animate {
  animation: fadeInRight 0.5s 1.8s forwards;
}

.newsletter-right form.animate {
  animation: fadeInRight 0.5s 2s forwards;
}

/* Keyframes */
@keyframes rotateScaleUp {
  0% {
    transform: rotate(-720deg) scale(0.3);
    opacity: 0;
  }
  100% {
    transform: rotate(0deg) scale(1);
    opacity: 1;
  }
}

@keyframes fadeInRight {
  0% {
    opacity: 0;
    transform: translateX(50px);
  }
  100% {
    opacity: 1;
    transform: translateX(0);
  }
}

form button.main {
  color: white;
  padding: 20px 60px;
  padding: clamp(12px, 5vw, 20px) clamp(20px, 12vw, 60px);
  border-radius: 35px;
  margin: 0 auto;
  line-height: 1.2;
  box-shadow: var(--btn-shdw);
}

.newsletter-left {
  display: flex;
  justify-content: center;
  margin-right: 2rem;
}

.newsletter-right {
  text-align: left;
}

button.main {
  background-color: var(--primary);
  color: white;
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

#newsletter .container {
  display: flex;
  flex-direction: row;
  gap: 50px;
}

.newsletter-left {
  width: 50%;
}

.newsletter-left img {
  width: 100%;
  max-width: 677px;
}

.newsletter-right {
  width: 50%;
  line-height: 2;
}

.newsletter-right > span {
  font-weight: 100;
  line-height: 1.8;
  letter-spacing: 0.1px;
}

.newsletter-right h3 {
  max-width: 400px;
  line-height: 1.8;
  letter-spacing: 0.2px;
  color: var(--text-color);
  padding: 20px 0;
}

.newsletter-right p {
  line-height: 1.8;
  font-weight: 500;
}

.newsletter-right form {
  margin: 36px 0;
}

.newsletter-right label {
  display: none;
}

.newsletter-right input {
  margin-right: 12px;
  outline: none;
  padding: 15px 38px;
  background: #f4f4f4;
  border: 1px solid #e8e8e8;
  border-radius: 39px;
}

.newsletter-right input::placeholder {
  color: #18171d93;
}

@media (max-width: 560px) {
  #newsletter .container {
    display: flex;
    flex-direction: column;
    gap: 50px;
  }

  .newsletter-left,
  .newsletter-left img,
  .newsletter-right,
  .newsletter-right form {
    display: block;
    width: 100%;
  }

  .newsletter-right form input {
    width: 100%;
    margin-bottom: 20px;
  }

  .newsletter-right form button.main {
    display: block;
    width: 100%;
    padding: 19px 0;
    text-align: center;
  }

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
</style>
