<template>
    <div class="block-archive">
        <ul class="block-archive__list">
            <li v-for="(image, index) in archive.fields.images" :key="index" class="block-archive__list-item">
                <div class="block-archive__image-container">
                    <ImageContentfulRenderer :image="image" class="block-archive__image" />
                </div>
                <div class="block-archive__infos">
                    <p class="block-archive__title">
                        {{ archive.fields.projectTitle }} 
                    </p>
                    <div class="block-archive__date">
                        {{ getYear(archive.fields.date) }}
                    </div>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
    import ImageContentfulRenderer from '~/components/partials/ImageContentfulRenderer';

    export default {
        components: {
            ImageContentfulRenderer
        },
        methods: {
            getYear: function(date) {
                return new Date(date).getFullYear();
            }
        },
        props: {
            archive: {
                type: Object,
                required: true
            },
        },
    }
</script>

<style>
</style>