<template>
  <section id="contact">
    <div class="container">
      <div class="section-title">
        <h2>Contact Us</h2>
        <p>
          Most calendars are designed for teams. Slate is designed for
          freelancers
        </p>
      </div>
      <div class="contact-form-left">
        <form @submit.prevent="submitForm">
          <h3>Contact Us</h3>
          <label for="input-name">Your Name</label>
          <input
            v-model="form.name"
            required
            id="input-name"
            name="name"
            type="text"
            placeholder="Your Name"
          />
          <label for="input-mail">Your Email</label>
          <input
            v-model="form.email"
            required
            id="input-mail"
            type="email"
            name="email"
            placeholder="Your Email"
          />
          <label for="input-message">Your Message</label>
          <textarea
            v-model="form.message"
            required
            id="input-message"
            name="message"
            placeholder="Your Message"
          ></textarea>
          <button type="submit" class="main" title="Send Message">Send</button>
        </form>
      </div>
      <div class="contact-info-right">
        <ul class="contact-info-list">
          <li><span class="contact_location"></span>{{ address }}</li>
          <li><span class="contact_phone"></span>{{ phone }}</li>
          <li><span class="contact_mail"></span>{{ email }}</li>
        </ul>
        <div class="google_maps">
          <iframe
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3954.133871563915!2d109.6492080758221!3d-7.66875367590129!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e7aca0881659fcb%3A0x1fb6a781a4f47e70!2sAlun-alun%20Kota%20Kebumen!5e0!3m2!1sid!2sid!4v1682099392332!5m2!1sid!2sid"
            style="width: 100%; height: 400px; border: none"
            allowfullscreen=""
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade"
          ></iframe>
        </div>

        <ul class="contact-social-link-list">
          <li v-for="link in socialLinks" :key="link.name" :class="link.class">
            <a :href="link.href" :title="link.title">
              <img :src="link.icon" alt="" loading="lazy" />
            </a>
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

<script>
import FacebookIcon from '@/assets/images/ant-design_facebook-filled-color-primary.svg';
import TwitterIcon from '@/assets/images/ant-design_twitter-outlined-color-primary.svg';
import LinkedInIcon from '@/assets/images/ant-design_linkedin-filled-color-primary.svg';
export default {
  name: 'ContactForm',
  data() {
    return {
      form: {
        name: '',
        email: '',
        message: '',
      },
      address:
        '6386 Spring St undefined Anchorage, Georgia 12473 United States',
      phone: '(843) 555-0130',
      email: 'willie.jennings@example.com',
      socialLinks: [
        {
          name: 'facebook',
          href: '#',
          title: 'Visit our Facebook page',
          icon: FacebookIcon,
          class: 'contact-facebook-link',
        },
        {
          name: 'twitter',
          href: '#',
          title: 'Get the latest update on Twitter',
          icon: TwitterIcon,
          class: 'contact-twitter-link',
        },
        {
          name: 'linkedin',
          href: '#',
          title: 'Get in touch with LinkedIn',
          icon: LinkedInIcon,
          class: 'contact-linkedin-link',
        },
      ],
    };
  },
  methods: {
    submitForm() {
      // Logique de soumission du formulaire
      console.log('Form data:', this.form);
    },
    initializeMap() {
      const map = new google.maps.Map(document.getElementById('map'), {
        center: { lat: 61.2181, lng: -149.9003 },
        zoom: 10,
      });
    },
  },
  mounted() {
    this.loadGoogleMapsAPI();
  },
};
</script>

<style scoped>
#contact .container {
  display: grid;
  grid-template-columns: 40% auto;
  grid-template-rows: repeat(2, auto);
  grid-template-areas:
    'title title'
    'contact-form contact-info';
  gap: 60px;
}

#contact .section-title {
  grid-area: title;
}

#contact .contact-form-left {
  grid-area: contact-form;

  padding: 52px 50px;
  border-radius: 20px;
  background: #ffffff;
  border: 1px solid #dddddd;
  box-shadow: 0px 13px 19px rgba(0, 0, 0, 0.07);
}

#contact .contact-form-left form {
  display: flex;
  flex-direction: column;
  gap: var(--form-gap);
}

.contact-form-left form label {
  display: none;
}

.contact-form-left form input,
.contact-form-left form textarea {
  padding: 19px 20px;
  background: #f5f5f5;
  border: 1px solid #e8e8e8;
  border-radius: 39px;
  font-family: var(--font-family);
}

.contact-form-left form #input-message {
  border-radius: 2px;
  min-height: 200px;
  resize: none;
}

#contact .contact-form-left form h3 {
  width: 100%;
  text-align: center;
  font-style: normal;
  line-height: 1.6;
  letter-spacing: 0.1px;
}

#contact .contact-form-left button {
  width: max-content;
  margin: 0;
}

#contact .contact-info-right {
  grid-area: contact-info;
  display: flex;
  flex-direction: column;
  gap: 50px;
  padding: 30px 0 30px 30px;
}

#contact .contact-info-right .contact-info-list {
  display: flex;
  gap: 15px;
  text-align: center;
  list-style: none;
}

#contact .contact-info-right .contact-info-list li {
  width: calc(100% / 3);
  overflow-wrap: break-word;
}

.contact-info-list li span {
  display: block;
  width: 32px;
  height: 32px;
  margin: 0 auto 20px;
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
}

span.contact_location {
  background: url(@/assets/images/ic-loc-color-primary.svg);
}

span.contact_phone {
  background: url(@/assets/images/ic-phone-color-primary.svg);
}

span.contact_mail {
  background: url(@/assets/images/ic-mail-color-primary.svg);
}

.contact-info-right iframe {
  border: none;
  width: 100%;
  height: 400px;
}

@media (max-width: 560px) {
  section {
    padding: 135px clamp(15px, 6vw, 30px);
  }

  section .container {
    width: 100%;
    margin: 0 !important;
    padding: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  #contact .container {
    display: grid;
    grid-template-rows: repeat(3, auto);
    grid-template-columns: 100%;
    grid-template-areas:
      'title'
      'contact-form'
      'contact-info';
    gap: 60px;
    padding: 0;
  }

  #contact .contact-info-right {
    padding: 60px 0;
  }

  #contact .contact-form-left {
    padding: 52px calc(var(--padding-lr) + 10px);
  }

  #contact .contact-info-right .contact-info-list {
    flex-direction: column;
    gap: 35px;
  }

  #contact .contact-info-right .contact-info-list li {
    width: 100%;
    display: inline-flex;
    align-items: center;
    text-align: left;
  }

  #contact .contact-info-right .contact-info-list li span {
    margin: 0 20px 0 0;
    padding: 16px;
  }
}
</style>
