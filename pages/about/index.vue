<template>
  <div class="page-about">
    
    <div class="container container--big">
      <div class="page-about__brand">
          M
      </div>
      <a href="/" class="button page-about__button">close</a>
    </div>

    <div class="container container--big page-about__container-big">

      <div class="page-about__content">

        <div class="page-about__content-left">
          <h1 class="page-about__heading">
            <RichTextRenderer :document="data.fields.heading" />
          </h1>
          <div class="page-about__paragraph">
            <RichTextRenderer :document="data.fields.description" />
          </div>
          <div class="page-about__footer">
            <div class="page-about__infos">
              <ul class="page-about__socials">
                <li class="page-about__socials-item">
                  <a :href="data.fields.twitterLink" class="page-about__socials-link">Tw</a>
                </li>
                <li class="page-about__socials-item">
                  <a :href="data.fields.dribbbleLink" class="page-about__socials-link">Dr</a>
                </li>
                <li class="page-about__socials-item">
                  <a :href="data.fields.linkedinLink" class="page-about__socials-link">Li</a>
                </li>
              </ul>
              <a :href="`mailto:${data.fields.email}`" class="page-about__email">
                {{data.fields.email}}
              </a>
            </div>
          </div>
        </div>

        <div class="page-about__content-right">
          <div class="page-about__location">
            Based in {{ data.fields.city }}
            <div class="country">
              / {{ data.fields.country }}
            </div> 
          </div>

          <div class="page-about__image-container">
            <ImageContentfulRendered :image="data.fields.picture" class="page-about__image"/>
          </div>

          <div class="page-about__footer">
            Coded By
            <div class="author">
              <a href="https://leomouraire.com" target="_blank">Léo Mouraire</a>
            </div>
          </div>
        </div>

      </div>

    </div>

  </div>
</template>

<script>
  import { createClient } from '~/plugins/contentful.js';

  //partials
  import RichTextRenderer from 'contentful-rich-text-vue-renderer';
  import ImageContentfulRendered from '~/components/partials/ImageContentfulRenderer';

  const client = createClient();

  export default {
    components: {
      RichTextRenderer,
      ImageContentfulRendered
    },
    asyncData () {
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

