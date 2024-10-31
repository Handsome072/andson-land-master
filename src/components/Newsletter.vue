<template>
  <section id="newsletter">
    <div class="container">
      <div class="newsletter-left w-full md:w-1/2">
        <img
          loading="lazy"
          src="@/assets/images/ilustration/undraw_newsletter_vovu.svg"
          alt="newsletter illustration"
          class="mx-auto"
        />
      </div>
      <div class="newsletter-right w-full md:w-1/2 mt-8 md:mt-0 md:ml-12">
        <span>At your Fingertips</span>
        <h3>Lightning fast prototyping</h3>
        <p class="font-bold">Subscribe to our Newsletter</p>
        <p>Available exclusively on Figmaland</p>
        <form @submit.prevent="subscribe">
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
    };
  },
  methods: {
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
  font-weight: 600;
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

.newsletter-right > * {
  visibility: visible !important;
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
