<template>
  <section id="partners" class="py-16">
    <div class="container">
      <!-- Section Title -->
      <div class="section-title">
        <h2 class="text-3xl font-bold">Partners</h2>
        <p class="text-gray-500">
          Most calendars are designed for teams. Slate is designed for
          freelancers.
        </p>
      </div>

      <!-- Partners List -->
      <div class="partners-list">
        <img
          loading="lazy"
          src="@/assets/images/ggl.jpg"
          alt="Google"
          class="mx-auto"
        />
        <img
          loading="lazy"
          src="@/assets/images/amz.jpg"
          alt="Amazon"
          class="mx-auto"
        />
        <img
          loading="lazy"
          src="@/assets/images/ms.jpg"
          alt="Microsoft"
          class="mx-auto"
        />
        <img
          loading="lazy"
          src="@/assets/images/ubr.jpg"
          alt="Uber"
          class="mx-auto"
        />
        <img
          loading="lazy"
          src="@/assets/images/db.jpg"
          alt="Dropbox"
          class="mx-auto"
        />
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'PartnersSection',
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
</style>
