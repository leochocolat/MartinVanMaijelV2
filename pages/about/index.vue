<template>
  <div class="page-project">
    <h1>
      {{ data.fields.pageName }}
    </h1>
  </div>
</template>

<script>
  import { createClient } from '~/plugins/contentful.js';

  const client = createClient();

  export default {
    asyncData ({ env }) {
      return Promise.all([
        client.getEntries({
          'content_type': 'aboutPage'
        }),
      ]).then(([data]) => {
        return {
          data: data.items[0],
        }
      }).catch(console.error)
    }
  }
</script>

<style>
</style>

