<template>
    <section class="section-footer-link">
        <div class="container container--big section-footer-link__container-big">
            <div class="section-footer-link__link-container">
                <a :href="`/${ link }`" class="section-footer-link__link">
                    {{ content }}
                </a>
                <span v-if="isPageArchive(data)" class="section-footer-link__infos">
                    <span class="section-footer-link__page-name">
                        <RichTextRenderer :document="data.fields.heading" />
                    </span>
                    <span class="section-footer-link__date">
                        / {{ data.fields.startDate }} - {{ data.fields.endDate }}
                    </span>
                </span>
                <span v-if="!isPageArchive(data)" :class="`section-footer-link__infos section-footer-link__infos--${content}`">
                    <span class="section-footer-link__page-name">
                        {{ data.fields.projectTitle }}
                    </span>
                    <span class="section-footer-link__date">
                        / {{ getYear(data.fields.publicationDate) }}
                    </span>
                </span>
            </div>
        </div>
    </section>
</template>

<script>
    import RichTextRenderer from 'contentful-rich-text-vue-renderer';

    export default {
        props: {
            link: {
                type: String,
                required: true
            },
            content: {
                type: String,
                required: true
            },
            data: {
                type: Object,
                required: true
            }
        },
        components: {
            RichTextRenderer
        },
        methods: {
            getYear: function(date) {
                return new Date(date).getFullYear();
            },
            isPageArchive: function(data) {
                return (data.fields.pageName === "Archives")
            } 
        }
    }
</script>

<style>
</style>

