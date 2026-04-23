<script setup>
import { useI18n } from 'vue-i18n';
import ServiceCard from './ServiceCard.vue';

const { t } = useI18n({ useScope: 'global' });

const services = [
    {
        id: 'first',
        titleKey: 'services.items.first.title',
        descriptionKey: 'services.items.first.description',
        iconClass: 'pi pi-hourglass',
        imageSrc: '',
        imageAlt: '',
    },
    {
        id: 'second',
        titleKey: 'services.items.second.title',
        descriptionKey: 'services.items.second.description',
        iconClass: 'pi pi-truck',
        imageSrc: '',
        imageAlt: '',
    },
    {
        id: 'third',
        titleKey: 'services.items.third.title',
        descriptionKey: 'services.items.third.description',
        iconClass: 'pi pi-cog',
        imageSrc: '',
        imageAlt: '',
    },
    {
        id: 'fourth',
        titleKey: 'services.items.fourth.title',
        descriptionKey: 'services.items.fourth.description',
        iconClass: 'pi pi-briefcase',
        imageSrc: '',
        imageAlt: '',
    },
    {
        id: 'fifth',
        titleKey: 'services.items.fifth.title',
        descriptionKey: 'services.items.fifth.description',
        iconClass: 'pi pi-building',
        imageSrc: '',
        imageAlt: '',
    },
    {
        id: 'sixth',
        titleKey: 'services.items.sixth.title',
        descriptionKey: 'services.items.sixth.description',
        iconClass: 'pi pi-users',
        imageSrc: '',
        imageAlt: '',
    },
];
</script>

<template>
<section class="services" id="services">
    <div class="container">
        <h2 class="section-title">{{ t('services.title') }}</h2>
        <div class="services-grid">
            <ServiceCard
                v-for="service in services"
                :key="service.id"
                :title="t(service.titleKey)"
                :description="t(service.descriptionKey)"
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
    background: linear-gradient(135deg, #f0f9f0 0%, #7a98eb 50%, var(--color-white) 100%);
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