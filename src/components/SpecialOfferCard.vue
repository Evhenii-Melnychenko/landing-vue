<script setup>
const props = defineProps({
  iconClass: {
    type: String,
    default: 'pi pi-lightbulb',
  },
  title: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <div class="offer-card">
    <div class="offer-icon">
      <i :class="props.iconClass"></i>
    </div>
    <h3>{{ props.title }}</h3>
    <p>{{ props.description }}</p>
  </div>
</template>

<style lang="scss" scoped>
.offer-card {
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  padding: 40px 30px;
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.2);
  transition: all 0.3s ease;
  position: relative;

  &:hover {
    transform: translateY(-10px);
    background: rgba(255, 255, 255, 0.25);
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
  }

  h3 {
    font-size: 1.4rem;
    margin-bottom: 15px;
    font-weight: 600;
  }

  p {
    font-style: italic;
    opacity: 0.95;
    line-height: 1.6;
  }
}

.offer-icon {
  font-size: 3rem;
  margin-bottom: 20px;
  display: block;
}
</style>
