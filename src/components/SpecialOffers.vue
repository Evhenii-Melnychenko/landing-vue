<script setup>
import SpecialOfferCard from './SpecialOfferCard.vue';

const offers = [
  {
    iconClass: 'pi pi-lightbulb',
    title: 'Special Offers Title first',
    description: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit. Consectetur adipisci corrupti quo, eos fuga omnis?',
  },
  {
    iconClass: 'pi pi-lightbulb',
    title: 'Special Offers Title second',
    description: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit. Consectetur adipisci corrupti quo, eos fuga omnis?',
  },
  {
    iconClass: 'pi pi-lightbulb',
    title: 'Special Offers Title third',
    description: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit. Consectetur adipisci corrupti quo, eos fuga omnis?',
  },
];

function scrollToSection(id) {
  const header = document.getElementById('header');
  const target = document.getElementById(id);

  if (target) {
    const headerHeight = header ? header.offsetHeight : 0;
    window.scrollTo({ top: target.offsetTop - headerHeight - 20, behavior: 'smooth' });
    window.history.replaceState({}, '', window.location.pathname + window.location.search);
  }
}
</script>

<template>
  <section class="special-offers">
        <div class="container">
            <div class="special-offers-content">
                <h2>Special Offers</h2>
                <div class="offers-grid">
                    <SpecialOfferCard
                      v-for="offer in offers"
                      :key="offer.title"
                      :icon-class="offer.iconClass"
                      :title="offer.title"
                      :description="offer.description"
                    />
                </div>
                <a href="#contact" class="claim-offer-btn" @click.prevent="scrollToSection('contact')">Call to us</a>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
.special-offers {
  background: linear-gradient(135deg, #f0f9f0 0%, #e8f8e8 50%, var(--color-white) 100%);
  padding: 80px 0;
  color: var(--color-white);
  position: relative;
  overflow: hidden;

  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><polygon points="50,10 60,40 90,40 68,60 78,90 50,75 22,90 32,60 10,40 40,40" fill="rgba(255,255,255,0.05)"/></svg>') repeat;
    background-size: 80px 80px;
    opacity: 0.3;
    animation: float 20s linear infinite;
  }

  h2 {
    color: var(--color-primary);
    font-size: 2.8rem;
    margin-bottom: 50px;
    font-weight: 700;
    text-shadow: 2px 2px 4px rgba(var(--color-black), 0.3);
  }
}

.special-offers-content {
  position: relative;
  z-index: 2;
  text-align: center;
}

.offers-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
  margin-bottom: 50px;
}

.claim-offer-btn {
  background: var(--color-primary);
  color: var(--color-white);
  padding: 18px 40px;
  font-size: 1.2rem;
  font-weight: 700;
  text-decoration: none;
  border-radius: 50px;
  display: inline-block;
  transition: all 0.3s ease;
  box-shadow: 0 8px 25px rgba(var(--color-black), 0.2);
  text-transform: uppercase;
  letter-spacing: 1px;

  &:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 35px rgba(var(--color-black), 0.3);
    background: var(--color-primary-light);
  }
}

@keyframes float {
    0% {
      transform: translateX(0) translateY(0);
    }

    100% { 
      transform: translateX(-80px) translateY(-80px); 
    }
}
</style>