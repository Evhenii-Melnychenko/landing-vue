<script setup>

const currentYear = new Date().getFullYear();

</script>

<template>
   <footer class="footer">
        <div class="container">
            <div class="footer-divider"></div>
            <div class="footer-bottom">
                <p class="footer-license">&copy; {{ currentYear }} Company's Name. All rights reserved.</p>
            </div>
        </div>
    </footer>
</template> 

<style lang="scss" scoped>
.footer {
    background: var( --color-primary);
    color: var(--color-white);
    padding: 30px 0;
    text-align: center;

    p {
        font-size: 1rem;
        margin: 0;
        opacity: 0.95;
    }
}
</style>