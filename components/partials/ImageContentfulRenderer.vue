<template>
    <img 
        :src="`https:${ image.fields.file.url }`" 
        :alt="image.fields.title" 
        :width="image.fields.file.details.image.width" 
        :height="image.fields.file.details.image.height" 
    >
</template>

<script>
    export default {
        props: {
            image: {
                type: Object,
                required: true
            },
        },
    }
</script>

<style>
</style>

