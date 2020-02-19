<template>
    <section class="section-archives-grid">
        <div class="container section-archives-grid__container">
            <ul class="section-archives-grid__list">
                <li v-for="(archive, index) in archives" :key="index" class="section-archives-grid__list-item">
                    <BlockArchives :archive="archive" />
                </li>
            </ul>
        </div>
    </section>
</template>

<script>
    import BlockArchives from '~/components/partials/BlockArchives';

    export default {
        components: {
            BlockArchives
        },
        props: {
            archives: {
                type: Array,
                required: true
            },
        },
    }
</script>

<style>
</style>

