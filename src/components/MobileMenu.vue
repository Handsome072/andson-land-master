<template>
  <div id="mobile-menu" :class="{ show: isMenuOpen }">
    <nav class="navbar-mobile-menu">
      <a href="#hero" class="home">Home</a>
      <a href="#about" class="about">About</a>
      <a href="#features" class="features">Features</a>
      <a href="#pricing" class="pricing">Pricing</a>
      <a href="#contact" class="contact">Contact</a>
    </nav>
    <div class="right-social social-mobile">
      <a
        href="https://twitter.com"
        target="_blank"
        rel="noopener"
        title="Find Us on Twitter"
      >
        <span class="ic-twitter"></span>
      </a>
      <a
        href="https://facebook.com"
        target="_blank"
        rel="noopener"
        title="Find Us on Facebook"
      >
        <span class="ic-facebook"></span>
      </a>
      <a
        href="https://linkedin.com"
        target="_blank"
        rel="noopener"
        title="Find Us on Linkedin"
      >
        <span class="ic-linkedin"></span>
      </a>
    </div>
    <div class="overlay" @click="$emit('close')"></div>
  </div>
</template>

<script>
export default {
  name: 'MobileMenu',
  props: {
    isMenuOpen: {
      type: Boolean,
      required: true,
    },
  },
};
</script>

<style scoped>
@media (max-width: 560px) {
  #mobile-menu {
    gap: 40px;
    height: 500px;
    display: block;
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background-color: #252b42;
    z-index: -1;
    transform: translateX(-100%);
    transition: transform 0.3s ease;
  }

  #mobile-menu.show {
    transform: translateX(0);
  }

  .navbar-mobile-menu {
    padding: 20px;
    margin-bottom: -50px;
    margin-top: 30px;
    background-color: #252b42;
  }
  .navbar-mobile-menu a {
    font-weight: 400;
    font-size: 1rem;
  }

  .overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: transparent;
  }
  
  @media (max-width: 560px) {
    .overlay {
      width: 100vw;
      height: 100vh;
      background: black;
      opacity: 0;
      position: fixed;
      top: 0;
      left: 0;
      z-index: 0;
      transition: 0.3s;
    }

    .header-wrapper.bg-dark ~ .overlay {
      opacity: 0.6;
      z-index: 998;
    }
    #mobile-menu {
      padding: 60px;
      width: 100%;
      display: none;
      flex-direction: column;
      gap: 40px;
    }

    #mobile-menu.show {
      display: flex;
      transition: 0.6s;
    }

    .header-wrapper.bg-dark {
      background: var(--text-color);
      filter: var(--drpshdw);
    }

    .navbar-mobile-menu {
      display: flex;
      flex-direction: column;
    }

    .navbar-mobile-menu a {
      padding: 20px 40px;
      cursor: pointer;
      font-weight: 400;
      font-size: 1.5em;
      text-align: left;
    }

    .social-mobile {
      padding: 40px;
      display: inline-flex;
      align-items: center;
    }

    .social-mobile a {
      padding: 0;
    }
  }
}
</style>
