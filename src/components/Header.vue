<template>
  <div class="header-wrapper" :class="{ 'bg-dark': isMenuOpen }">
    <header
      :class="{
        'bg-white sticky': isSticky,
        'bg-transparent text-white': !isSticky,
        'fixed top-0 left-0 right-0 z-1000 transition-colors duration-300': true,
      }"
      :style="{ height: headerHeight }"
    >
      <div class="container">
        <div class="left-container">
          <nav class="navbar-desktop-menu">
            <a href="#hero" class="home">Home</a>
            <a href="#about" class="about">About</a>
            <a href="#fe@/assetsures" class="features">Features</a>
            <a href="#pricing" class="pricing">Pricing</a>
            <a href="#contact" class="contact">Contact</a>
          </nav>

          <div class="logo-center">
            <img :src="logoSrc" alt="Figma Land Logo" title="Figma Land" />
          </div>
        </div>

        <div
          class="mobile-button"
          @click="toggleMenu"
          :style="{ transform: isMenuOpen ? 'rotate(180deg)' : 'rotate(0)' }"
          title="Open Menu"
        >
          <svg
            v-if="!isMenuOpen"
            viewBox="0 0 40 32"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M6.66797 8H33.3346V10.6667H6.66797V8ZM13.3346 14.6667H33.3346V17.3333H13.3346V14.6667ZM21.668 21.3333H33.3346V24H21.668V21.3333Z"
            />
          </svg>
          <svg v-else xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
            <path
              d="M18.3 5.71a.996.996 0 0 0-1.41 0L12 10.59L7.11 5.7A.996.996 0 1 0 5.7 7.11L10.59 12L5.7 16.89a.996.996 0 1 0 1.41 1.41L12 13.41l4.89 4.89a.996.996 0 1 0 1.41-1.41L13.41 12l4.89-4.89c.38-.38.38-1.02 0-1.4z"
            />
          </svg>
        </div>

        <div class="right-social">
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
      </div>

      <!-- Mobile Menu -->
      <MobileMenu :isMenuOpen="isMenuOpen" @close="toggleMenu" />
    </header>
  </div>
</template>

<script>
import { ref, onMounted, onUnmounted } from 'vue';
import logoDark from '@/assets/images/content-logo-darkLogo.png';
import logoBlack from '@/assets/images/ilustration/logo-black.jpg';
import MobileMenu from './MobileMenu.vue';

export default {
  name: 'HeaderComponent',
  components: {
    MobileMenu,
  },
  setup() {
    const isSticky = ref(false);
    const logoSrc = ref(logoDark);
    const headerHeight = ref('var(--header-height)');
    const isMenuOpen = ref(false);

    const handleScroll = () => {
      if (window.scrollY > 50) {
        isSticky.value = true;
        headerHeight.value = '81px';
        logoSrc.value = logoBlack;
      } else {
        isSticky.value = false;
        headerHeight.value = 'var(--header-height)';
        logoSrc.value = logoDark;
      }
    };

    const toggleMenu = () => {
      isMenuOpen.value = !isMenuOpen.value;
      document.body.classList.toggle('overflow-hidden', isMenuOpen.value);
    };

    onMounted(() => {
      window.addEventListener('scroll', handleScroll);
    });

    onUnmounted(() => {
      window.removeEventListener('scroll', handleScroll);
    });

    return { isSticky, logoSrc, headerHeight, isMenuOpen, toggleMenu };
  },
};
</script>

<style scoped>
.navbar-desktop-menu a {
  font-weight: 400;
  font-size: 1.5em;
}

.navbar-desktop-menu a:hover {
  background-color: var(--primary);
}

.header-wrapper {
  display: flex;
  flex-direction: column;
  z-index: 999;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}

#mobile-menu {
  display: none;
}

header {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: auto;
  top: 0;
  left: 0;
  z-index: 9;
  transition: all 0.3s;
}

header .container {
  width: 100%;
  max-width: 1200px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 40px;
  height: 187px;
}

nav.navbar-desktop-menu {
  display: inline-flex;
  gap: 21px;
}

.left-container {
  display: inline-flex;
  align-items: center;
  gap: 35px;
}

.navbar-desktop-menu a {
  font-weight: 400;
  font-size: 1.5em;
}

.navbar-desktop-menu a:hover {
  background-color: var(--primary);
  color:white;
}

header.sticky {
  background: #fff;
  filter: var(--drpshdw);
}

header.sticky a {
  color: var(--text-color) !important;
}

header.sticky a:hover {
  color: white;
}

.custom-logo {
  width: 200px !important;
  height: auto !important;
}

@media (max-width: 560px) {
  header {
    height: var(--header-height);
  }

  header .container {
    padding: 0 var(--padding-lr);
  }
  nav .navbar-desktop-menu {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    background-color: var(--primary);
    padding: 30px;
    display: flex;
    flex-direction: column;
    display: none;
  }
  nav .right-social {
    display: none;
  }

  .navbar-desktop-menu a,
  .right-social {
    display: none;
  }

  .navbar-desktop-menu a.active {
    display: flex;
  }
  .mobile-button {
    width: clamp(30px, 9vw, 40px);
    padding: 0;
    height: auto;
    border-radius: 6px;
    display: block;
    cursor: pointer;
    transition: 0.6s;
  }

  .mobile-button svg {
    fill: white;
  }
  .sticky .mobile-button svg {
    fill: black;
  }

  .mobile-button:hover {
    background-color: var(--primary);
  }
}

@media (min-width: 600px) {
  .logo-center img {
    max-width: 45vw;
  }
}
</style>
