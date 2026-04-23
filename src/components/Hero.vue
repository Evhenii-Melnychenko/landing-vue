<script setup>
import { useI18n } from 'vue-i18n'

const { t } = useI18n({ useScope: 'global' })

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
   <section class="hero" id="hero">
        <div class="container">
          <div class="hero-content">
            <h1>{{ t('hero.title') }}</h1>
            <p class="subtitle">{{ t('hero.subtitle') }}</p>
            <a href="#contact" class="cta-primary" @click.prevent="scrollToSection('contact')">{{ t('hero.cta') }}</a>
          </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
.hero {
  background: linear-gradient(135deg, var( --color-primary) 0%, var( --color-primary-light) 100%);
  color: var(--color-white);
  padding: 80px 0;
  text-align: center;
  position: relative;
  overflow: hidden;

  &::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grid" width="10" height="10" patternUnits="userSpaceOnUse"><path d="M 10 0 L 0 0 0 10" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="0.5"/></pattern></defs><rect width="100" height="100" fill="url(%23grid)"/></svg>');
    opacity: 0.3;
  }

  h1 {
    font-size: 3.5rem;
    font-weight: 700;
    margin-bottom: 1rem;
    text-shadow: 2px 2px 4px rgba(var(--color-black-rgb), 0.3);
    animation: fadeInUp 0.8s ease-out;
  }

  .subtitle {
    font-size: 1.4rem;
    margin-bottom: 2rem;
    opacity: 0.95;
    animation: fadeInUp 0.8s ease-out 0.2s both;
  }
}

.hero-content {
  position: relative;
  z-index: 2;
}

.cta-primary {
  display: inline-block;
  background: var(--color-white);
  color: var( --color-primary);
  padding: 18px 40px;
  font-size: 1.2rem;
  font-weight: 700;
  text-decoration: none;
  border-radius: 50px;
  box-shadow: 0 8px 25px rgba(var(--color-black-rgb), 0.2);
  transition: all 0.3s ease;
  animation: fadeInUp 0.8s ease-out 0.4s both;
  text-transform: uppercase;
  letter-spacing: 1px;

  &:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 35px rgba(var(--color-black-rgb), 0.3);
    background: var(--color-white);
  }
}

.financing-badge {
  display: inline-block;
  background: var(--color-white);
  color: var( --color-primary);
  padding: 15px 35px;
  border-radius: 50px;
  margin-top: 30px;
  font-weight: 700;
  border: 3px solid var( --color-primary);
  animation: fadeInUp 0.8s ease-out 0.6s both;
  text-decoration: none;
  transition: all 0.3s ease;
  box-shadow: 0 6px 20px rgba(var(--color-black-rgb), 0.15);
  text-transform: uppercase;
  letter-spacing: 1px;
  font-size: 1.1rem;

  &:hover {
    background: var( --color-primary);
    color: var(--color-white);
    transform: translateY(-3px);
    box-shadow: 0 10px 30px rgba(var(--color-black-rgb), 0.25);
  }
}

@media (max-width: 968px) {
  .hero h1 {
    font-size: 2.5rem;
  }
  
  .hero .subtitle {
    font-size: 1.2rem;
  }
}
        
@media (max-width: 575px) {
  .hero h1 {
    font-size: 2rem;
  }
  
  .hero .subtitle {
    font-size: 1rem;
  }
}
</style>