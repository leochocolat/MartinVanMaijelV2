<template>
    <div class="block-project">
        <a :href="`/projects/${ index }`"  class="block-project__link">
            <div class="block-project__container">
                <div class="block-project__image-container">
                    <ImageContentfulRendered :image="data.fields.heroImage" class="block-project__image" />
                </div>
                <div class="block-project__infos">
                    <span class="block-project__infos-title">
                        {{ data.fields.projectTitle }}
                    </span>
                    <span class="block-project__infos-date">
                        /{{ getYear(data.fields.publicationDate) }}
                    </span>
                </div>
            </div>
        </a>
    </div>
</template>

<script>
    import RichTextRenderer from 'contentful-rich-text-vue-renderer';
    import ImageContentfulRendered from '~/components/partials/ImageContentfulRenderer';

    export default {
        props: {
            data: {
                type: Object,
                required: true
            },
            index: {
                type: Number,
                required: true
            }
        },
        methods: {
            getYear: (date) => {
                return new Date(date).getFullYear();
            }
        },
        components: {
            RichTextRenderer,
            ImageContentfulRendered
        }
    }
</script>

<style>
</style>

