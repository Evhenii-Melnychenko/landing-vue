<script setup>
import ServiceCard from './ServiceCard.vue';

const services = [
    {
        title: 'Title of Service',
        description: 'Description of the service goes here.',
        iconClass: 'pi pi-hourglass',
        imageSrc: '',
        imageAlt: '',
    },
    {
        title: 'Title of Service',
        description: 'Description of the service goes here.',
        iconClass: 'pi pi-truck',
        imageSrc: '',
        imageAlt: '',
    },
    {
        title: 'Title of Service',
        description: 'Description of the service goes here.',
        iconClass: 'pi pi-cog',
        imageSrc: '',
        imageAlt: '',
    },
    {
        title: 'Title of Service',
        description: 'Description of the service goes here.',
        iconClass: 'pi pi-briefcase',
        imageSrc: '',
        imageAlt: '',
    },
    {
        title: 'Title of Service',
        description: 'Description of the service goes here.',
        iconClass: 'pi pi-building',
        imageSrc: '',
        imageAlt: '',
    },
    {
        title: 'Title of Service',
        description: 'Description of the service goes here.',
        iconClass: 'pi pi-users',
        imageSrc: '',
        imageAlt: '',
    },
];
</script>

<template>
<section class="services" id="services">
    <div class="container">
        <h2 class="section-title">Our Services</h2>
        <div class="services-grid">
            <ServiceCard
                v-for="service in services"
                :key="`${service.title}-${service.iconClass}`"
                :title="service.title"
                :description="service.description"
                :icon-class="service.iconClass"
                :image-src="service.imageSrc"
                :image-alt="service.imageAlt"
            />
        </div>
    </div>
</section>
</template>

<style  lang="scss" scoped>
.services {
    padding: 100px 0;
    background: linear-gradient(135deg, #f0f9f0 0%, #e8f8e8 50%, var(--color-white) 100%);
    position: relative;

    &::before {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="25" cy="25" r="1" fill="rgba(0,87,27,0.1)"/><circle cx="75" cy="75" r="1" fill="rgba(0,87,27,0.1)"/></svg>') repeat;
        opacity: 0.5;
    }
}
        
.section-title {
    text-align: center;
    font-size: 2.8rem;
    color: var( --color-primary);
    margin-bottom: 3rem;
    font-weight: 700;
    position: relative;
    z-index: 2;
}
        
.services-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 30px;
    margin-top: 50px;
    position: relative;
    z-index: 2;
}

@media (max-width: 968px) {
    .section-title {
        font-size: 2.2rem;
    }
    
    .services-grid {
        grid-template-columns: 1fr;
    }
}       
</style>