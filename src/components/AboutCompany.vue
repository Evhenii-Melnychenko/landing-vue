<script setup>
  import { useI18n } from 'vue-i18n'

  const { t } = useI18n({ useScope: 'global' })
</script>

<template>
  <section class="about-our-company" id="about-our-company">
        <div class="container">
            <div class="about-our-company-content">
                <h2>{{ t('about.title') }}</h2>
                <p class="about-description-main">
                  {{ t('about.description_main') }}
                </p>
                <p class="about-description-secondary">
                  {{ t('about.description_secondary') }}
                </p>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>

.about-our-company {
  padding: 100px 0;
  background: linear-gradient(135deg, var(--color-white) 0%, #f8fff8 100%);
  position: relative;

  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="20" cy="20" r="1.5" fill="rgba(0,87,27,0.08)"/><circle cx="80" cy="80" r="1.5" fill="rgba(0,87,27,0.08)"/></svg>') repeat;
    opacity: 0.6;
  }

  h2 {
    font-size: 3rem;
    color: var( --color-primary);
    text-align: center;
    margin-bottom: 40px;
    font-weight: 700;
    position: relative;

    &::after {
      content: '';
      position: absolute;
      bottom: -15px;
      left: 50%;
      transform: translateX(-50%);
      width: 100px;
      height: 4px;
      background: linear-gradient(90deg, var( --color-primary), var( --color-primary-light));
      border-radius: 2px;
    }
  }
}

.about-our-company-content {
  position: relative;
  z-index: 2;
  max-width: 900px;
  margin: 0 auto;
  background: var(--color-surface);
  padding: 60px 50px;
  border-radius: 25px;
  box-shadow: 0 20px 60px rgba(0,87,27,0.15);
  border: 3px solid rgba(0,87,27,0.1);
}

.about-description-main {
  font-size: 1.3rem;
  line-height: 1.8;
  color: var(--color-secondary);
  margin-bottom: 30px;
  text-align: justify;
}

.about-description-secondary {
  font-size: 1.2rem;
  line-height: 1.8;
  color: var(--color-secondary);
  text-align: justify;
  padding: 25px;
  background: linear-gradient(
    135deg,
    rgba(0,87,27, 0.05) 0%,
    
  );
  border-radius: 15px;
  border-left: 5px solid var(--color-primary);
}
</style>