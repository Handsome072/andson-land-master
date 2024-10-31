<template>
  <section
    id="hero"
    class="flex items-center justify-center min-h-screen bg-gray-100"
  >
    <div class="container">
      <h1 :class="{ 'animate-slide-down': showHeroText }">
        The best products start with Figma
      </h1>
      <p :class="{ 'animate-slide-up': showParagraph }">
        Most calendars are designed for teams. Slate is designed for
        freelancers.
      </p>
      <button :class="{ 'animate-slide-up': showButton }" @click="goToPricing">
        Try For Free
      </button>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      showHeroText: false,
      showParagraph: false,
      showButton: false,
    };
  },
  methods: {
    goToPricing() {
      window.location.hash = '#pricing';
    },
  },
  mounted() {
    this.showHeroText = true;
    setTimeout(() => {
      this.showParagraph = true;
    }, 500);

    setTimeout(() => {
      this.showButton = true;
    }, 1000); 
  },
};
</script>

<style scoped>
#hero {
  position: relative;
  width: 100%;
  height: 125vh;
  color: white;
  background: url('@/assets/images/hero-img-desktop.webp') no-repeat;
  background-size: cover;
  background-position: center;
  display: flex;
}

#hero .container {
  margin: 110px auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  line-height: 1.8;
  text-align: center;
  max-width: 1200px;
}

#hero h1,
#hero p,
button {
  opacity: 0; /* Opacité initiale */
}

#hero h1 {
  font-style: normal;
  line-height: 1.12;
  letter-spacing: 0.2px;
}

#hero p {
  width: 756px;
  height: 80px;
  font-style: normal;
  line-height: 1.8;
  letter-spacing: 0.2px;
  margin: 18px auto 90px;
}

button {
  color: white;
  padding: 20px 60px;
  padding: clamp(12px, 5vw, 20px) clamp(20px, 12vw, 60px);
  border-radius: 35px;
  margin: 0 auto;
  line-height: 1.2;
  font-weight: 400;
  font-size: 1.618em;
  box-shadow: var(--btn-shdw);
}

@keyframes slide-down {
  0% {
    transform: translateY(-20px);
    opacity: 0;
  }
  100% {
    transform: translateY(0);
    opacity: 1;
  }
}

@keyframes slide-up {
  0% {
    transform: translateY(20px);
    opacity: 0;
  }
  100% {
    transform: translateY(0);
    opacity: 1;
  }
}

.animate-slide-down {
  animation: slide-down 1s ease forwards;
}

.animate-slide-up {
  animation: slide-up 2s ease forwards;
}

@media (max-width: 560px) {
  #hero {
    height: 110vh;
  }
  #hero h2 {
    width: 100%;
    line-height: 1.1;
  }

  #hero p {
    width: 100%;
  }
}

@media screen and (max-width: 320px) {
  #hero h1 {
    font-size: 5.854em;
  }
}
</style>
