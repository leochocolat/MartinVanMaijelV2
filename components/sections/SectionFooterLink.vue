<template>
    <section class="section-footer-link">
        <div class="container container--big section-footer-link__container-big">
            <a :href="`/${ link }`" class="section-footer-link__link">{{ content }}</a>
        </div>
    </section>
</template>

<script>
    export default {
        props: {
            link: {
                type: String,
                required: true
            },
            content: {
                type: String,
                required: true
            }
        },
    }
</script>

<style>
</style>

