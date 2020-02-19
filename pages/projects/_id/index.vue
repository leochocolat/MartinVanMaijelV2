<template>
  <main class="main page-home">
    <div class="scroll-container">
      <HeaderProject :data="data" />
      <SectionProject :data="data" />
      <SectionFooterLink v-if="isNextProjectAvailable(projects)" :link="`projects/${getNextProject()}`" :content="'next'" class="page-home__section-footer-link-next" />
      <SectionFooterLink v-if="enablePreviousProject(projects)" :link="`projects/${getPreviousProject()}`" :content="'previous'" />
    </div>
  </main>
</template>

<script>
  import { createClient } from '~/plugins/contentful.js';

  //headers
  import HeaderProject from '~/components/headers/HeaderProject';

  //section
  import SectionProject from '~/components/sections/SectionProject';
  import SectionFooterLink from '~/components/sections/SectionFooterLink';

  const client = createClient();

  export default {
    components: {
      HeaderProject,
      SectionProject,
      SectionFooterLink
    },
    methods: {
      getNextProject: function () {
        let currentIndex = parseInt(this.$route.params.id);
        return currentIndex + 1;
      },
      getPreviousProject: function () {
        let currentIndex = parseInt(this.$route.params.id);
        return currentIndex - 1;
      },
      isNextProjectAvailable: function (projects) {
        let currentIndex = parseInt(this.$route.params.id);
        return !(!projects[currentIndex + 1]);
      },
      enablePreviousProject(projects) {
        let currentIndex = parseInt(this.$route.params.id);
        return (!projects[currentIndex + 1] && projects[currentIndex - 1])
      }
    },
    asyncData ({ env, params }) {
      return Promise.all([
        client.getEntries({
          'content_type': 'projects'
        }),
      ]).then(([data]) => {
        return {
          data: data.items[params.id],
          projects: data.items
        }
      }).catch(console.error)
    },
    validate ({ params }) {
      return Promise.all([
          client.getEntries({
              'content_type': 'projects'
          }),
      ]).then(([data]) => {
          return data.items[params.id] != null;
      }).catch(console.error)
    }
  }
</script>

<style>
</style>

