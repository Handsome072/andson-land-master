<template>
  <section id="about" class="">
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
