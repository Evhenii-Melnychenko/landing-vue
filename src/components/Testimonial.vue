<script setup>
  import { useI18n } from 'vue-i18n'

  const { t } = useI18n({ useScope: 'global' })
</script>

<template>
   <section class="testimonial">
        <div class="container">
            <div class="testimonial-content">
                <p class="testimonial-text">{{ t('testimonial.quote') }}</p>
                <p class="testimonial-author">— {{ t('testimonial.author') }}</p>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>

.testimonial {
    background: linear-gradient(135deg, var( --color-primary) 0%, var( --color-primary-light) 100%);
    padding: 80px 0;
    color: var(--color-white);
    text-align: center;

    &::before {
        content: '"';
        font-size: 4rem;
        position: absolute;
        left: -20px;
        top: -20px;
        opacity: 0.3;
    }

    &-content {
        max-width: 800px;
        margin: 0 auto;
    }

    &-text {
        font-size: 1.4rem;
        font-style: italic;
        line-height: 1.8;
        margin-bottom: 30px;
        position: relative;
    }
    
    &-author {
        font-size: 1.1rem;
    }
}

</style>