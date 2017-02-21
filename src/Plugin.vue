<template>
  <div class="uk-margin-small-bottom">
      <span class="form__topic">Title</span> 
      <input v-model="model.title" class="uk-width-1-1" type="text" name="title">
      <span class="uk-text-muted form__hint"></span>
  </div>
  <div class="uk-margin-small-bottom">
      <span class="form__topic">Description</span> 
      <input v-model="model.description" class="uk-width-1-1" type="text" name="description">
      <span class="uk-text-muted form__hint">A one to two sentence description for this object.</span>
  </div>
  <hr>
  <div><a class="uk-float-right link" href="https://ogp.me/" target="_blank" title="What is Open Graph?">What is Open Graph?</a></div>
  <div class="uk-margin-small-bottom">
      <span class="form__topic">OG Title</span> 
      <input v-model="model.og_title" class="uk-width-1-1" type="text" name="og_title">
      <span class="uk-text-muted form__hint">The title of your object.</span>
  </div>
  <div class="uk-margin-small-bottom">
      <span class="form__topic">OG Site Name</span> 
      <input v-model="model.og_site_name" class="uk-width-1-1" type="text" name="og_site_name">
      <span class="uk-text-muted form__hint">The name which should be displayed for the overall site</span>
  </div>
  <div class="uk-margin-small-bottom">
      <span class="form__topic">OG Description</span> 
      <input v-model="model.og_description" class="uk-width-1-1" type="text" name="og_description">
      <span class="uk-text-muted form__hint">A one to two sentence description of your object.</span>
  </div>
  <div class="uk-margin-small-bottom">
      <span class="form__topic">OG Image</span> 
      <fileupload :model.sync="model.og_image"></fileupload>
      <span class="uk-text-muted form__hint">An image URL which should represent your object.</span>
  </div>
  <hr>
  <div><a class="uk-float-right link" href="https://dev.twitter.com/cards/getting-started" target="_blank" title="What is a Twitter Card?">What is a Twitter Card?</a></div>
  <div class="uk-margin-small-bottom">
      <span class="form__topic">Twitter Title</span> 
      <input v-model="model.twitter_title" class="uk-width-1-1" type="text" name="twitter_title">
      <span class="uk-text-muted form__hint">The title of your object.</span>
  </div>
  <div class="uk-margin-small-bottom">
      <span class="form__topic">Twitter Site</span> 
      <input v-model="model.twitter_site" class="uk-width-1-1" type="text" name="twitter_site">
      <span class="uk-text-muted form__hint">The name which should be displayed for the overall site</span>
  </div>
  <div class="uk-margin-small-bottom">
      <span class="form__topic">Twitter Description</span> 
      <input v-model="model.twitter_description" class="uk-width-1-1" type="text" name="twitter_description">
      <span class="uk-text-muted form__hint">A one to two sentence description of your object.</span>
  </div>
  <div class="uk-margin-small-bottom">
      <span class="form__topic">Twitter Image</span> 
      <fileupload :model.sync="model.twitter_image"></fileupload>
      <span class="uk-text-muted form__hint">An image URL which should represent your object.</span>
  </div>
</template>

<script>
export default {
  mixins: [window.Storyblok.plugin],
  methods: {
    initWith: function() {
      return {
        plugin: 'meta',
        title: 'Your title',
        description: 'Your description',
        og_title: 'Your Open Graph Title',
        og_description: 'Your description',
        og_image: '',
        og_site_name: 'Your site name (e.g Storyblok)',
        twitter_title: 'Your title',
        twitter_site: '@your_site',
        twitter_description: 'Your description',
        twitter_image: ''
      }
    }
  },
  events: {
    'plugin:created': function() {
      console.log('plugin:created')
    },
    'plugin:destroyed': function() {
      console.log('plugin:destroyed')
    }
  },
  watch: {
    'model': {
      handler: function (value) {
        this.$emit('changed-model', value);
      },
      deep: true
    }
  }
}
</script>

<style>
</style>
