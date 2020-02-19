<template>
  <main class="main page-archives">
    <div class="scroll-container">
      <HeaderArchives :data="data" />
      <SectionArchivesGrid :archives="archives" />
    </div>
  </main>
</template>

<script>
  import { createClient } from '~/plugins/contentful.js';

  // partials
  import RichTextRenderer from 'contentful-rich-text-vue-renderer';
  import ImageContentfulRendered from '~/components/partials/ImageContentfulRenderer';

  //headers
  import HeaderArchives from '~/components/headers/HeaderArchives';

  //sections
  import SectionArchivesGrid from '~/components/sections/SectionArchivesGrid';

  const client = createClient();

  export default {
    components: {
      RichTextRenderer,
      ImageContentfulRendered,
      HeaderArchives,
      SectionArchivesGrid
    },
    methods: {

    },
    asyncData ({ env }) {
      return Promise.all([
        client.getEntries({
          'content_type': 'archivesPage'
        }),
        client.getEntries({
          'content_type': 'archivedProjects'
        }),
      ]).then(([data, archives]) => {
        return {
          data: data.items[0],
          archives: archives.items
        }
      }).catch(console.error)
    }
  }
</script>

<style>
</style>

