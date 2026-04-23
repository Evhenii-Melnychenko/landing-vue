<script setup>
import { useI18n } from 'vue-i18n';
import SpecialOfferCard from './SpecialOfferCard.vue';

const { t } = useI18n({ useScope: 'global' });

const offers = [
  {
    id: 'first',
    iconClass: 'pi pi-lightbulb',
    titleKey: 'specialOffers.items.first.title',
    descriptionKey: 'specialOffers.items.first.description',
  },
  {
    id: 'second',
    iconClass: 'pi pi-lightbulb',
    titleKey: 'specialOffers.items.second.title',
    descriptionKey: 'specialOffers.items.second.description',
  },
  {
    id: 'third',
    iconClass: 'pi pi-lightbulb',
    titleKey: 'specialOffers.items.third.title',
    descriptionKey: 'specialOffers.items.third.description',
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
          <h2>{{ t('specialOffers.title') }}</h2>
          <div class="offers-grid">
              <SpecialOfferCard
                v-for="offer in offers"
                :key="offer.id"
                :icon-class="offer.iconClass"
                :title="t(offer.titleKey)"
                :description="t(offer.descriptionKey)"
              />
          </div>
          <a href="#contact" class="claim-offer-btn" @click.prevent="scrollToSection('contact')">{{ t('specialOffers.cta') }}</a>
        </div>
      </div>
  </section>
</template>

<style lang="scss" scoped>
.special-offers {
  background: linear-gradient(135deg, var(--color-primary) 0%, var(--color-primary-light) 100%);
  padding: 80px 0;
  color: var(--color-white);
  position: relative;
  overflow: hidden;

  &::before {
    content: "";
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
    color: var(--color-white);
    font-size: 2.8rem;
    margin-bottom: 50px;
    font-weight: 700;
    text-shadow: 2px 2px 4px rgba(var(--color-black-rgb), 0.3);
  }

  &-content {
    position: relative;
    z-index: 2;
    text-align: center;
  }
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
  box-shadow: 0 8px 25px rgba(var(--color-black-rgb), 0.2);
  text-transform: uppercase;
  letter-spacing: 1px;

  &:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 35px rgba(var(--color-black-rgb), 0.3);
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