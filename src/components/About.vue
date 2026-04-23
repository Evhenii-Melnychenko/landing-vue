<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import { useI18n } from 'vue-i18n';

const { t } = useI18n({ useScope: 'global' });

const stats = [
  { id: 'experience', max: 22, suffix: '+', labelKey: 'whyChooseUs.stats.experience' },
  { id: 'counties', max: 7,  suffix: '',  labelKey: 'whyChooseUs.stats.counties' },
  { id: 'financing', max: 0,  suffix: '%', labelKey: 'whyChooseUs.stats.financing' },
  { id: 'satisfaction', max: 100, suffix: '%', labelKey: 'whyChooseUs.stats.satisfaction' },
];

const features = [
  {
    id: 'first',
    titleKey: 'whyChooseUs.features.first.title',
    descriptionKey: 'whyChooseUs.features.first.description',
  },
  {
    id: 'second',
    titleKey: 'whyChooseUs.features.second.title',
    descriptionKey: 'whyChooseUs.features.second.description',
  },
  {
    id: 'third',
    titleKey: 'whyChooseUs.features.third.title',
    descriptionKey: 'whyChooseUs.features.third.description',
  },
  {
    id: 'fourth',
    titleKey: 'whyChooseUs.features.fourth.title',
    descriptionKey: 'whyChooseUs.features.fourth.description',
  },
  {
    id: 'fifth',
    titleKey: 'whyChooseUs.features.fifth.title',
    descriptionKey: 'whyChooseUs.features.fifth.description',
  },
];

const counters = ref(stats.map(() => 0));
const statsRef = ref(null);

let observer = null;
let animated = false;

function animateCounters() {
  if (animated) return;
  animated = true;

  stats.forEach((stat, i) => {
    if (stat.max === 0) return;

    const duration = 1500;
    const steps = 60;
    const increment = stat.max / steps;
    let current = 0;
    let step = 0;

    const timer = setInterval(() => {
      step++;
      current = Math.min(Math.round(increment * step), stat.max);
      counters.value[i] = current;

      if (current >= stat.max) clearInterval(timer);
    }, duration / steps);
  });
}

onMounted(() => {
  observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) animateCounters(); },
    { threshold: 0.3 }
  );
  if (statsRef.value) observer.observe(statsRef.value);
});

onUnmounted(() => {
  observer?.disconnect();
});

</script>

<template>
  <section class="about" id="about">
    <div class="container">
      <div class="about-content">
        <div class="about-text">
            <h2>{{ t('whyChooseUs.title') }}</h2>
            <p><span class="highlight">{{ t('whyChooseUs.highlight') }}</span>{{ t('whyChooseUs.description') }}</p>
            
            <ul class="features-list">
                <li v-for="feature in features" :key="feature.id">
                  <i class="pi pi-check"></i>
                  <strong>{{ t(feature.titleKey) }}</strong>
                  <span>{{ t(feature.descriptionKey) }}</span>
                </li>
            </ul>
        </div>
        <div class="stats-grid" ref="statsRef">
            <div class="stat-card" v-for="(stat, i) in stats" :key="stat.id">
              <span class="stat-number">{{ counters[i] }}{{ stat.suffix }}</span>
              <span class="stat-label">{{ t(stat.labelKey) }}</span>
            </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>

.about {
  padding: 100px 0;
  background: linear-gradient(135deg, #f8f9fa 0%, #e8f5e8 100%);
  position: relative;

  &::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="50" cy="50" r="2" fill="rgba(0,87,27,0.05)"/></svg>') repeat;
    opacity: 0.3;
  }
}

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
  position: relative;
  z-index: 2;
}

.about-text {
  background: var(--color-white);
  padding: 50px 40px;
  border-radius: 20px;
  box-shadow: 0 15px 40px rgba(var(--color-primary-rgb), 0.15);
  border-left: 6px solid var(--color-primary);

  h2 {
    font-size: 2.5rem;
    color: var(--color-primary);
    margin-bottom: 30px;
    font-weight: 700;
  }

  p {
    font-size: 1.1rem;
    line-height: 1.8;
    margin-bottom: 30px;
    color: var(--color-secondary);
  }
}

.about-description {
  font-size: 1.2rem;
  font-weight: 600;
  color: var(--color-primary);
  margin-bottom: 25px;
  padding: 20px;
  background: linear-gradient(
    135deg,
    rgba(0,87,27,0.05) 0%,
    rgba(0,123,36,0.08) 100%
  );
  border-radius: 10px;
  border-left: 4px solid var(--color-primary);
}

.highlight {
  background: linear-gradient(120deg, var(--color-primary) 0%, var(--color-primary-light) 100%);
  color: var(--color-white);
  padding: 4px 10px;
  border-radius: 6px;
  font-weight: 600;
}

.features-list {
  list-style: none;
  margin-top: 30px;

  li {
    padding: 10px 0;
    font-size: 1.2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 15px;
  }

  span {
    text-wrap: balance;
    text-align: right;
  }
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 30px;
  margin-top: 40px;
}

.stat-card {
  text-align: center;
  padding: 30px 20px;
  background: var(--color-white);
  border-radius: 10px;

  .stat-number {
    font-size: 2.5rem;
    font-weight: 700;
    color: var(--color-primary);
    display: block;
  }

  .stat-label {
    font-size: 0.9rem;
    color: var(--color-secondary);
    margin-top: 5px;
  }
}

@media (max-width: 968px) {
  .about-content {
    grid-template-columns: 1fr;
    text-align: center;
  }
    
  .about-evergreen-content {
    padding: 40px 30px;
  }

  .features-list {
    li {
      flex-direction: column;
    }
  }
}
</style>