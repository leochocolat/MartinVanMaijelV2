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
            <div class="section-project__infos">
                <ul class="section-project__infos-list">
                    <li v-if="data.fields.teamMembers1" class="section-project__infos-list-item">
                        <RichTextRenderer :document="data.fields.teamMembers1" />
                    </li>
                    <li v-if="data.fields.teamMembers2" class="section-project__infos-list-item">
                        <RichTextRenderer :document="data.fields.teamMembers2" />
                    </li>
                    <li v-if="data.fields.teamMembers3" class="section-project__infos-list-item">
                        <RichTextRenderer :document="data.fields.teamMembers3" />
                    </li>
                    <li v-if="data.fields.teamMembers4" class="section-project__infos-list-item">
                        <RichTextRenderer :document="data.fields.teamMembers4" />
                    </li>
                    <li v-if="data.fields.teamMembers5" class="section-project__infos-list-item">
                        <RichTextRenderer :document="data.fields.teamMembers5" />
                    </li>
                    <li v-if="data.fields.teamMembers6" class="section-project__infos-list-item">
                        <RichTextRenderer :document="data.fields.teamMembers6" />
                    </li>
                    <li v-if="data.fields.teamMembers7" class="section-project__infos-list-item">
                        <RichTextRenderer :document="data.fields.teamMembers7" />
                    </li>
                    <li v-if="data.fields.teamMembers8" class="section-project__infos-list-item">
                        <RichTextRenderer :document="data.fields.teamMembers8" />
                    </li>
                    <li v-if="data.fields.teamMembers9" class="section-project__infos-list-item">
                        <RichTextRenderer :document="data.fields.teamMembers9" />
                    </li>
                </ul>
                <a :href="data.fields.url" target="_blank" class="section-project__infos-link">Visit Website</a>
            </div>
        </div>
    </section>
</template>

<script>
    import ImageContentfulRendered from '~/components/partials/ImageContentfulRenderer';
    import RichTextRenderer from 'contentful-rich-text-vue-renderer';

    export default {
        props: {
            data: {
                type: Object,
                required: true
            },
        },
        components: {
            ImageContentfulRendered,
            RichTextRenderer
        }
    }
</script>

<style>
</style>

