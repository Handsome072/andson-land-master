<template>
  <section id="pricing">
    <div class="container">
      <div class="section-title">
        <h2>Plans and Pricings</h2>
        <p>
          Most calendars are designed for teams. Slate is designed for
          freelancers.
        </p>
      </div>
      <div class="pricelist">
        <div
          v-for="(plan, index) in plans"
          :key="index"
          :class="['plan', { 'featured-plan': plan.featured }]"
        >
          <div class="plan-title">
            <h3>{{ plan.title }}</h3>
            <p v-if="plan.description">{{ plan.description }}</p>
          </div>
          <div class="price">
            <span class="number">{{ plan.price }}</span>
            <span class="dollar-sign">$</span>
            <span class="pay-info">{{ plan.paymentInfo }}</span>
          </div>
          <ol class="pricing-features-list" type="i">
            <li v-for="(feature, fIndex) in plan.features" :key="fIndex">
              {{ feature }}
            </li>
          </ol>
          <button class="order main">Order Now</button>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  setup() {
    const plans = [
      {
        title: 'FREE',
        description: 'Start with free plan.',
        price: 0,
        paymentInfo: 'Per Month',
        features: ['Pricing Feature', 'Pricing Feature', 'Pricing Feature'],
      },
      {
        title: 'Business',
        description:
          'Scale up your business with business plan.<br /><br /><strong>Get all the feature!</strong>',
        price: 77,
        paymentInfo: 'a year',
        features: [
          'Pricing Feature',
          'Pricing Feature',
          'Pricing Feature',
          'Pricing Feature',
          'Pricing Feature',
          'Pricing Feature',
          'Pricing Feature',
        ],
        featured: true,
      },
      {
        title: 'STANDARD',
        description: 'Best Choice for Starting up your Business.',
        price: 11,
        paymentInfo: 'Per Month',
        features: [
          'Pricing Feature',
          'Pricing Feature',
          'Pricing Feature',
          'Pricing Feature',
        ],
      },
    ];

    return {
      plans,
    };
  },
};
</script>

<style scoped>
#pricing {
  background: #252b42;
  color: white;
}

#pricing .section-title {
  color: white;
  margin: 0 0 80px;
}

#pricing .pricelist {
  width: -moz-fit-content;
  width: fit-content;
  max-width: 1200px;
  display: flex;
  gap: 50px;
  text-align: center;
  align-items: center;
}

.pricelist .plan {
  background: white;
  color: var(--text-color);
  border-radius: 10px;
  padding: 60px 40px;
  display: flex;
  flex-direction: column;
  gap: var(--plan-gap);
  height: max-content;
  width: 350px;
}

.pricelist .featured-plan {
  background-color: var(--primary);
  color: white;
  width: 400px;
}

.pricelist .featured-plan button {
  background-color: white;
  color: var(--primary);
}

.pricelist .plan-title h3 {
  text-transform: uppercase;
  font-weight: 700;
  font-size: 2em;
  line-height: 1.6;
  margin-bottom: 20px;
  letter-spacing: 0.1px;
}

.plan-title p {
  line-height: 1.4;
  text-align: center;
  letter-spacing: 0.1px;
}

.plan .price {
  display: grid;
  grid-template-columns: 1fr 2fr;
  grid-template-rows: repeat(2, 1fr);
  column-gap: 10px;
  row-gap: 0px;
  grid-template-areas:
    'number dollar'
    'number pay-info';
  text-align: left;
  margin: 0 auto;
  line-height: 0.6;
  align-items: center;
}

.price .number {
  grid-area: number;
  display: block;
  font-weight: 600;
  font-size: 7.4em;
  text-align: right;
}

.price .dollar-sign {
  grid-area: dollar;
  display: block;
  font-weight: 700;
  font-size: 2em;
}

.price .pay-info {
  grid-area: pay-info;
  display: block;
  font-weight: 400;
}

.pricing-features-list {
  text-align: left;
  margin: 0 auto;
}

@media (max-width: 560px) {
  #pricing .pricelist {
    max-width: 100%;
    display: flex;
    flex-direction: column;
    text-align: center;
    align-items: center;
  }

  #pricing .pricelist .plan {
    width: 100%;
    max-width: calc(100vw - var(--padding-lr));
  }
}
</style>
