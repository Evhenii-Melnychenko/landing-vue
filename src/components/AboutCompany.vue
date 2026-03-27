<script setup>

</script>

<template>
  <section class="about-our-company" id="about-our-company">
        <div class="container">
            <div class="about-our-company-content">
                <h2>About our company</h2>
                <p class="about-description-main">At <strong>our company</strong>, Lorem ipsum dolor sit amet. <strong>Lorem, ipsum dolor</strong> Lorem ipsum dolor sit amet, consectetur adipisicing elit. Provident, ipsa autem. Animi error recusandae repudiandae? <span class="counties-highlight">city1, city2, city3, city4, city5, city6, city7</span>.</p>
                <p class="about-description-secondary">We are not just a company – we help you <span class="dreams-highlight">Lorem ipsum dolor sit amet</span> with <span class="dreams-highlight">Lorem, ipsum dolor</span> Lorem, ipsum dolor.</p>
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
  background: var(--color-white);
  padding: 60px 50px;
  border-radius: 25px;
  box-shadow: 0 20px 60px rgba(0,87,27,0.15);
  border: 3px solid rgba(0,87,27,0.1);
}

.about-description-main {
  font-size: 1.3rem;
  line-height: 1.8;
  color: #333333;
  margin-bottom: 30px;
  text-align: justify;
}

.about-description-secondary {
  font-size: 1.2rem;
  line-height: 1.8;
  color: #555;
  text-align: justify;
  padding: 25px;
  background: linear-gradient(
    135deg,
    rgba(0,87,27,0.05) 0%,
    rgba(0,123,36,0.08) 100%
  );
  border-radius: 15px;
  border-left: 5px solid var( --color-primary);
}

.counties-highlight {
  background: linear-gradient(120deg, var( --color-primary) 0%, var( --color-primary-light) 100%);
  color: var(--color-white);
  padding: 4px 12px;
  border-radius: 8px;
  font-weight: 700;
}

.dreams-highlight {
  color: var( --color-primary);
  font-weight: 700;
  font-size: 1.1em;
}

</style>