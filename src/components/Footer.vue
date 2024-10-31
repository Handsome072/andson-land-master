<template>
  <footer>
    <div class="container">
      <div class="footer-left">
        <div class="footer-pages animated">
          <h4>Pages</h4>
          <ul>
            <li><a href="#" title="Aller à l'accueil">Accueil</a></li>
            <li><a href="#" title="Aller au produit">Produit</a></li>
            <li><a href="#" title="Aller à la tarification">Tarification</a></li>
            <li><a href="#" title="Aller à propos">À propos</a></li>
            <li><a href="#" title="Aller à contact">Contact</a></li>
          </ul>
        </div>
        <div class="footer-links-1 animated">
          <h4>Liens</h4>
          <ul>
            <li><a href="#" title="Aller à l'accueil">Accueil</a></li>
            <li><a href="#" title="Aller au produit">Produit</a></li>
            <li><a href="#" title="Aller à la tarification">Tarification</a></li>
            <li><a href="#" title="Aller à propos">À propos</a></li>
            <li><a href="#" title="Aller à contact">Contact</a></li>
          </ul>
        </div>
        <div class="footer-links-2 animated">
          <h4>Liens Utiles</h4>
          <ul>
            <li><a href="#" title="Aller à l'accueil">Accueil</a></li>
            <li><a href="#" title="Aller au produit">Produit</a></li>
            <li><a href="#" title="Aller à la tarification">Tarification</a></li>
            <li><a href="#" title="Aller à propos">À propos</a></li>
            <li><a href="#" title="Aller à contact">Contact</a></li>
          </ul>
        </div>
      </div>
      <div class="footer-right">
        <div class="footer-location animated">
          <span class="ic-loc"></span>7480 Mockingbird Hill undefined
        </div>
        <div class="footer-phone animated">
          <span class="ic-phone"></span>(239) 555-0108
        </div>
        <ul class="footer-social-link-list animated">  
          <li class="footer-facebook-link">
            <a href="#" title="Visitez notre page Facebook">
              <img
                loading="lazy"
                src="@/assets/images/ant-design_facebook-filled.svg"
                alt="lien Facebook"
              />
            </a>
          </li>
          <li class="footer-twitter-link">
            <a href="#" title="Recevez les dernières mises à jour sur Twitter">
              <img
                loading="lazy"
                src="@/assets/images/ant-design_twitter-outlined.svg"
                alt="lien Twitter"
              />
            </a>
          </li>
          <li class="footer-linkedin-link">
            <a href="#" title="Contactez-nous sur LinkedIn">
              <img
                loading="lazy"
                src="@/assets/images/ant-design_linkedin-filled.svg"
                alt="lien LinkedIn"
              />
            </a>
          </li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'FooterComponent',
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      const elements = document.querySelectorAll('.animated');
      elements.forEach((el, index) => {
        const rect = el.getBoundingClientRect();
        if (rect.top < window.innerHeight) {
          setTimeout(() => {
            el.classList.add('slide-in');
          }, index * 200); 
        }
      });
    }
  }
};
</script>

<style scoped>
/* Animation CSS */
@keyframes slideIn {
  from {
    transform: translateX(50%);
    opacity: 0;
  }
  to {
    transform: translateX(0);
    opacity: 1;
  }
}

.animated {
  opacity: 0;
}

.slide-in {
  animation: slideIn 1s forwards;
}

/* Le reste du style pour la mise en page */
footer {
  background: #252b42;
  color: white;
  padding: 150px 0;
}

footer .container {
  width: 100%;
  max-width: 1200px;
  margin: auto;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-start;
}

.footer-left {
  display: flex;
  flex-direction: row;
  width: 40%;
  justify-content: space-between;
}

.footer-left div h4 {
  font-style: normal;
  font-size: 1.4em;
  font-weight: 600;
  line-height: 1.8;
  letter-spacing: 0.1px;
  margin-bottom: 25px;
}

.footer-left div ul {
  list-style: none;
  margin: 0;
}

.footer-left div ul li {
  font-style: normal;
  font-weight: 400;
  font-size: 1.4em;
  line-height: 2.5;
  letter-spacing: 0.2px;
}

.footer-left div ul li a {
  padding: 0;
}

.footer-left div ul li a:hover {
  color: #2091f9;
}

.footer-right {
  width: 35%;
  display: flex;
  flex-direction: column;
  gap: 25px;
  font-size: 1.4em;
}

.footer-right .footer-location,
.footer-right .footer-phone {
  display: flex;
  gap: 10px;
  font-style: normal;
  line-height: 1.8;
  letter-spacing: 0.2px;
  align-items: center;
}

.footer-right .footer-location .ic-loc {
  display: block;
  width: 35px;
  height: 40px;
  background: url(@/assets/images/ic-loc.svg) no-repeat;
  background-size: contain;
}

.footer-right .footer-phone .ic-phone {
  display: block;
  width: 35px;
  height: 40px;
  background: url(@/assets/images/ic-phone.svg) no-repeat;
  background-size: contain;
}

.footer-right .footer-social-link-list,
.contact-social-link-list {
  display: flex;
  gap: 25px;
  list-style-type: none;
}

.footer-right .footer-social-link-list li img,
.contact-social-link-list li img {
  width: 35px;
  height: auto;
}

.footer-right .footer-social-link-list li a,
.contact-social-link-list li a {
  padding: 0;
}

@media (max-width: 560px) {
  footer .container {
    flex-direction: column;
    gap: 80px;
    align-items: center;
    padding: 0 40px;
  }

  footer .container .footer-left {
    width: 100%;
    flex-direction: column;
    gap: 80px;
    align-items: center;
    text-align: center;
  }

  footer .container .footer-right {
    width: 100%;
    gap: 80px;
  }

  .footer-right .footer-location,
  .footer-right .footer-phone {
    flex-direction: column;
  }

  footer .container .footer-right * {
    margin: 0 auto;
  }
}
</style>
