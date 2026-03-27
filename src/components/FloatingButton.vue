<template>
    <a href="tel:123456789" class="fab" title="Call Now">
        <i class="pi pi-phone"></i>
    </a>
</template>

<style lang="scss" scoped>

.fab {
    position: fixed;
    bottom: 30px;
    right: 30px;
    width: 70px;
    height: 70px;
    background: var( --color-primary);
    color: var(--color-white);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.5rem;
    text-decoration: none;
    box-shadow: 0 8px 25px rgba(0, 87, 27, 0.3);
    transition: all 0.3s ease;
    z-index: 10;

    &:hover {
        transform: scale(1.1);
        background: var( --color-primary-light);
    }
}

</style>