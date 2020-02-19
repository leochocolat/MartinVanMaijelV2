<template>
    <section class="section-project-grid">
        <div class="container section-project-grid__container">
            <ul class="section-project-grid__list">
                <li v-for="(project, index) in projects" :key="index" class="section-project-grid__list-item">
                    <BlockProject :data="project" :index="index" />
                </li>
            </ul>
        </div>
    </section>
</template>

<script>
    import RichTextRenderer from 'contentful-rich-text-vue-renderer';
    import BlockProject from '~/components/partials/BlockProject';

    export default {
        props: {
            projects: {
                type: Array,
                required: true
            },
        },
        components: {
            RichTextRenderer,
            BlockProject
        }
    }
</script>

<style>
</style>

