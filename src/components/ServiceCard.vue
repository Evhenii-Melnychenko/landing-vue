<script setup>

const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: true,
  },
  iconClass: {
    type: String,
    default: 'pi pi-star',
  },
  imageSrc: {
    type: String,
    default: '',
  },
  imageAlt: {
    type: String,
    default: '',
  },
});
</script>

<template>
  <div class="service-card">
    <div v-if="props.imageSrc" class="service-media">
      <img :src="props.imageSrc" :alt="props.imageAlt || props.title" loading="lazy" />
    </div>
    <div v-else class="service-icon">
      <i :class="props.iconClass"></i>
    </div>

    <h3>{{ props.title }}</h3>
    <p>{{ props.description }}</p>
  </div>
</template>

<style lang="scss" scoped>
.service-card {
  background: var(--color-white);
  padding: 40px 30px;
  border-radius: 20px;
  text-align: center;
  box-shadow: 0 15px 40px rgba(0, 87, 27, 0.12);
  transition: all 0.4s ease;
  border-top: 6px solid var(--color-primary);
  position: relative;
  overflow: hidden;

  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(0, 87, 27, 0.05), transparent);
    transition: left 0.5s ease;
  }

  &:hover {
    transform: translateY(-15px) scale(1.02);
    box-shadow: 0 25px 60px rgba(0, 87, 27, 0.2);
    border-top-color: var(--color-primary-light);

    &::before {
      left: 100%;
    }
  }

  h3 {
    font-size: 1.5rem;
    margin-bottom: 15px;
    color: var(--color-primary);
  }

  p {
    color: var(--color-secondary);
    line-height: 1.6;
  }
}

.service-icon {
  font-size: 3rem;
  margin-bottom: 20px;
  color: var(--color-primary);
}

.service-media {
  margin-bottom: 20px;

  img {
    width: 100%;
    max-height: 180px;
    object-fit: cover;
    border-radius: 14px;
    display: block;
  }
}
</style>
