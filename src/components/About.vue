<template>
  <section
    id="about"
    class="opacity-0 translate-y-10 transition-all duration-500"
    ref="aboutSection"
  >
    <div class="container mx-auto grid grid-cols-1 md:grid-cols-2 gap-12">
      <div class="left-cta">
        <h2>Fastest way to organize</h2>
        <p>
          Most calendars are designed for teams. Slate is designed for
          freelancers.
        </p>
        <button @click="goToPricing" class="main">Try For Free</button>
      </div>
      <div class="right-img">
        <img
          loading="lazy"
          src="@/assets/images/screen content.jpg"
          alt="Screen content"
          class="w-full max-w-xl mx-auto"
        />
      </div>
    </div>
  </section>
</template>

<script>
export default {
  mounted() {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add("show");
            observer.unobserve(entry.target);
          }
        });
      },
      { threshold: 0.8 }
    );

    observer.observe(this.$refs.aboutSection);
  },
};
</script>

<style scoped>
#about {
  background: white;
}

#about .container {
  max-width: 1236.3px;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 50px;
}

.left-cta h2 {
  line-height: 1.2;
  letter-spacing: 0.2px;
}

.left-cta p {
  font-style: normal;
  line-height: 1.8;
  letter-spacing: 0.2px;
  margin: 30px 0 60px;
  color: #020202a3;
}

.right-img img {
  width: 100%;
  max-width: 660px;
}

/* for animation */
#about {

  transform: translateY(100px);
  transition: opacity 3s ease, transform 3s ease;
}

#about.show {
  opacity: 1;
  transform: translateY(0);
}

@media (max-width: 560px) {
  #about .container {
    width: 100%;
    display: grid;
    grid-template-columns: 100%;
    grid-template-rows: repeat(2, auto);
    gap: 60px;
  }

  #about .container * {
    text-align: center;
  }
}
</style>
