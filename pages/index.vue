<template>
  <main class="main page-home">
    <div class="scroll-container">
      <HeaderHome :data="data" />
      <SectionProjectGrid :projects="projects" />
      <SectionFooterLink :link="'archives'" :content="'archives'" :data="archives" />
    </div>
  </main>
</template>

<script>
  import { createClient } from '~/plugins/contentful.js';

  // partials
  import RichTextRenderer from 'contentful-rich-text-vue-renderer';
  import ImageContentfulRendered from '~/components/partials/ImageContentfulRenderer';

  //headers
  import HeaderHome from '../components/headers/HeaderHome';

  //sections
  import SectionProjectGrid from '../components/sections/SectionProjectGrid';
  import SectionFooterLink from '../components/sections/SectionFooterLink';

  const client = createClient();

  export default {
    components: {
      RichTextRenderer,
      ImageContentfulRendered,
      HeaderHome,
      SectionProjectGrid,
      SectionFooterLink
    },
    methods: {

    },
    asyncData ({ env }) {
      return Promise.all([
        client.getEntries({
          'content_type': 'home'
        }),
        client.getEntries({
          'content_type': 'projects'
        }),
        client.getEntries({
          'content_type': 'archivesPage'
        }),
      ]).then(([data, projects, archives]) => {
        return {
          data: data.items[0],
          projects: projects.items,
          archives: archives.items[0]
        }
      }).catch(console.error)
    }
  }
</script>

<style>
</style>

