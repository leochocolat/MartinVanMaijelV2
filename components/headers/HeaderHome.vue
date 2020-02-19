<template>
    <header class="header-home">
        <div class="container header-home__container">
            <div class="header-home__brand">
                m / m
            </div>
            <a class="header-home__link button" href="/about">about</a>
            <div class="header-home__content">
                <ul class="header-home__social-list">
                    <li class="header-home__social-list-item">
                        <a :href="data.fields.twitterLink" target="_blank" class="header-home__social-link">Twitter</a>
                    </li>
                    <li class="header-home__social-list-item">
                        <a :href="data.fields.dribbbleLink" target="_blank" class="header-home__social-link">Dribbble</a>
                    </li>
                    <li class="header-home__social-list-item">
                        <a :href="data.fields.linkedinLink" target="_blank" class="header-home__social-link">Linkedin</a>
                    </li>
                </ul>
                <div class="header-home__description-container">
                    <h1 class="header-home__heading heading">
                        <RichTextRenderer :document="data.fields.subheading" class="paragraph"/>
                    </h1>
                    <div class="header-home__description paragraph">
                        <RichTextRenderer :document="data.fields.introduction" />
                    </div>
                </div>
            </div>
        </div>
        <div class="container container--big header-home__container-big">   
            <h2 class="giant-heading">
                {{ data.fields.heading }}
            </h2>
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

