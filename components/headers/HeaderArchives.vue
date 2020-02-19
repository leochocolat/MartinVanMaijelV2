<template>
    <header class="header-archives">
        <div class="container container--big header-archives__container-big">
            <a href="/" class="button header-archives__button">
                close
            </a>
        </div>
        <div class="container header-archives__container">
            <div class="header-archives__content">
                <h1 class="header-archives__heading">
                    <RichTextRenderer :document="data.fields.heading" />
                </h1>
                <div class="header-archives__block-infos">
                    <div class="header-archives__block-infos-title">
                        {{ data.fields.startDate }}
                        <span class="separator"></span> 
                        {{ data.fields.startDate }} 
                    </div>
                    <div class="header-archives__block-infos-introduction">
                        {{ data.fields.introduction }} 
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>

<script>
    import RichTextRenderer from 'contentful-rich-text-vue-renderer';

    export default {
        props: {
            data: {
                type: Object,
                required: true
            },
        },
        components: {
            RichTextRenderer
        }
    }
</script>

<style>
</style>

