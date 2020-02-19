<template>
    <section class="section-project">
        <div  v-if="data.fields.images" class="container section-project__container">
            <ul class="section-project__list">
                <li v-for="(image, index) in data.fields.images" :key="index" class="section-project__list-item">
                    <div class="section-project__image-container">
                        <ImageContentfulRendered :image="image" class="section-project__image" />
                    </div>
                </li>
            </ul>
        </div>
    </section>
</template>

<script>
    import ImageContentfulRendered from '~/components/partials/ImageContentfulRenderer';

    export default {
        props: {
            data: {
                type: Object,
                required: true
            },
        },
        components: {
            ImageContentfulRendered
        }
    }
</script>

<style>
</style>

