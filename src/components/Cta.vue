<script setup>
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
    <section class="cta-section" id="get-started">
        <div class="container">
            <div class="cta-content">
                <h2>Title of Section</h2>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ab, ex omnis inventore veritatis reiciendis magnam!</p>
                <div class="cta-buttons">
                    <a href="#contact" class="cta-primary" @click.prevent="scrollToSection('contact')">Schedule Free Consultation</a>
                    <a href="tel:123456789" class="btn-secondary">Call (123) 456-789</a>
                </div>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
 .cta-section {
    background: linear-gradient(135deg, #f0f8f0 0%, #e8f5e8 100%);
    padding: 100px 0;
    text-align: center;
    position: relative;

    &::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><rect x="45" y="45" width="10" height="10" fill="rgba(0,87,27,0.05)" rx="2"/></svg>') repeat;
        opacity: 0.5;
    }
}
        
.cta-content {
    position: relative;
    z-index: 2;
    background: var(--color-white);
    padding: 60px 40px;
    border-radius: 20px;
    box-shadow: 0 20px 50px rgba(var(--color-primary), 0.15);
    border: 2px solid rgba(var(--color-primary), 0.1);

    h2 {
        font-size: 2.8rem;
        color: var(--color-primary);
        margin-bottom: 20px;
        font-weight: 700;
    }

    p {
        font-size: 1.2rem;
        margin-bottom: 40px;
        color: var(--color-secondary);
    }
}

.cta-buttons {
    display: flex;
    justify-content: center;
    gap: 20px;
    flex-wrap: wrap;
}
        
.btn-secondary {
    background: transparent;
    color: var( --color-primary);
    border: 2px solid var( --color-primary);
    padding: 15px 35px;
    font-size: 1.1rem;
    font-weight: 600;
    text-decoration: none;
    border-radius: 50px;
    transition: all 0.3s ease;

    &:hover {
        background: var( --color-primary);
        color: var(--color-white);
        transform: translateY(-2px);
    }
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
    box-shadow: 0 8px 25px rgba(var(--color-black), 0.2);
    transition: all 0.3s ease;
    animation: fadeInUp 0.8s ease-out 0.4s both;
    text-transform: uppercase;
    letter-spacing: 1px;

    &:hover {
        transform: translateY(-3px);
        box-shadow: 0 12px 35px rgba(var(--color-black), 0.3);
        background: var(--color-white);
    }
}
</style>