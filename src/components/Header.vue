<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const isScrolled = ref(false);
const isMobileMenuOpen = ref(false);
const activeSection = ref('hero');

const navLinks = [
  { href: 'hero', label: 'Home' },
  { href: 'about-evergreen', label: 'About' },
  { href: 'services', label: 'Services' },
  { href: 'about', label: 'Why Choose Us' },
  { href: 'contact', label: 'Contact' },
];

function toggleMobileMenu() {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
}

function closeMobileMenu() {
  isMobileMenuOpen.value = false;
}

function handleScroll() {
  isScrolled.value = window.scrollY > 50;

  const sections = document.querySelectorAll('section[id]');
  let current = '';

  sections.forEach(section => {
    if (window.scrollY >= section.offsetTop - 100) {
      current = section.getAttribute('id') || '';
    }
  });

  if (current) activeSection.value = current;
}

function scrollToSection(id) {
  const target = document.getElementById(id);

  if (target) {
    const headerHeight = document.getElementById('header').offsetHeight;
    const targetPosition = target.offsetTop - headerHeight - 20;
    
    window.scrollTo({ top: targetPosition, behavior: 'smooth' });
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});

</script>

<template>
  <header class="header" :class="{ scrolled: isScrolled }" id="header">
      <div class="header-content">
          <a href="#hero" class="logo">
              <span>Logo</span>
          </a>

          <nav>
              <ul class="nav">
                  <li v-for="link in navLinks" :key="link.href">
                      <a :href="'#' + link.href" :class="{ active: activeSection === link.href }" @click.prevent="scrollToSection(link.href)">
                        {{ link.label }}
                      </a>
                  </li>
              </ul>
          </nav>

            <div class="mobile-menu-toggle" :class="{ active: isMobileMenuOpen }" @click="toggleMobileMenu">
              <span></span>
              <span></span>
              <span></span>
          </div>

          <div class="mobile-menu" :class="{ active: isMobileMenuOpen }">
              <ul class="nav">
                  <li v-for="link in navLinks" :key="link.href">
                      <a :href="'#' + link.href" :class="{ active: activeSection === link.href }" @click.prevent="scrollToSection(link.href); closeMobileMenu()">
                        {{ link.label }}
                      </a>
                  </li>
              </ul>
          </div>
      </div>
  </header>
</template>

<style lang="scss" scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background: rgba(var(--color-white), 0.95);
  backdrop-filter: blur(20px);
  z-index: 1000;
  padding: 15px 0;
  border-bottom: 1px solid rgba(var(--color-primary), 0.1);
  transition: all 0.3s ease;

  &.scrolled {
    background: rgba(var(--color-white), 0.98);
    box-shadow: 0 5px 25px rgba(var(--color-primary), 0.1);
  }
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;

  @media (max-width: 968px) {
    padding: 0 15px;
  }
}

.logo {
  display: flex;
  align-items: center;
  font-size: 1.8rem;
  font-weight: 700;
  color: var( --color-primary);
  text-decoration: none;
  transition: all 0.3s ease;

  &:hover {
    color: var( --color-primary-light);
    transform: scale(1.05);
  }

  &-icon {
    font-size: 2.2rem;
    margin-right: 10px;
  }
}

.nav {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  gap: 30px;

  li {
    a {
      color: var( --color-secondary);
      text-decoration: none;
      font-weight: 600;
      padding: 10px 15px;
      border-radius: 25px;
      transition: all 0.3s ease;
      position: relative;

      &:hover {
        color: var( --color-primary);
        background: rgba(var(--color-primary), 0.1);
        transform: translateY(-2px);
      }

      &.active {
        color: var(--color-white);
        background: var( --color-primary);
      }
    }
  }
}

.mobile-menu-toggle {
  display: none;
  flex-direction: column;
  justify-content: center;
  cursor: pointer;
  padding: 10px;
  width: 46px;
  height: 46px;
  position: relative;
  z-index: 1201;

  span {
    width: 25px;
    height: 3px;
    background: var( --color-primary);
    margin: 3px 0;
    transition: 0.3s ease;
    border-radius: 2px;
  }

  &.active {
    span:nth-child(1) {
      transform: translateY(9px) rotate(45deg);
    }

    span:nth-child(2) {
      opacity: 0;
    }

    span:nth-child(3) {
      transform: translateY(-9px) rotate(-45deg);
    }
  }
}

.mobile-menu {
  display: block;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  width: min(85vw, 340px);
  background: rgba(var(--color-white), 0.98);
  backdrop-filter: blur(20px);
  border-left: 1px solid rgba(var(--color-primary), 0.1);
  box-shadow: -10px 0 30px rgba(var(--color-black), 0.12);
  transform: translateX(100%);
  transition: transform 0.35s ease;
  z-index: 100;

  &.active {
    transform: translateX(0);
  }

  .nav {
    flex-direction: column;
    padding: 90px 20px 20px;
    gap: 12px;

    li {
      a {
        display: block;
        text-align: left;
        padding: 15px;
      }
    }
  }
}

@media (max-width: 968px) {
  .header-content {
    padding: 0 15px;
  }
  
  nav .nav {
    display: none;
  }

  .mobile-menu .nav {
    display: flex;
    background-color: var(--color-white);
    height: 100vh;
  }
  
  .mobile-menu-toggle {
    display: flex;
  }
  
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