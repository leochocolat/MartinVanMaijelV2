<template>
    <header class="header-project">
        <div class="container container--big header-project__container-big">
            <a href="/" class="button header-project__nav-link">close</a>
        </div>
        <div class="container header-project__container">
            <div class="header-project__block-introduction">
                <div class="header-project__image-container">
                    <ImageContentfulRenderer :image="data.fields.heroImage" class="header-project__image" />
                </div>
                <h1 class="header-project__heading">
                    <RichTextRenderer :document="data.fields.heading" />
                </h1>
                <div class="header-project__introduction-content">
                    <div class="header-project__introduction-left">
                        <div class="header-project__introduction-title">
                            Info
                        </div>
                        <p class="header-project__introduction-text">
                            {{ data.fields.info }}
                        </p>
                    </div>
                    <div class="header-project__introduction-right">
                        <div class="header-project__introduction-title">
                            {{ data.fields.projectTitle }}
                        </div>
                        <p class="header-project__introduction-text">
                            {{ data.fields.description }}
                        </p> 
                    </div>
                </div>
                <div class="header-project__scroll-down">
                    Scroll down
                </div>
            </div>
        </div>
    </header>
</template>

<script>
import RichTextRenderer from 'contentful-rich-text-vue-renderer';
import ImageContentfulRenderer from '~/components/partials/ImageContentfulRenderer';

export default {
    props: {
        data: {
            type: Object,
            required: true
        },
    },
    components: {
        RichTextRenderer,
        ImageContentfulRenderer
    }
}
</script>

<style>

</style>