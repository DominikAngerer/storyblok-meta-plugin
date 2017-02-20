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
      <div class="uk-placeholder uk-margin-bottom-remove uk-margin-top-remove">
        <div class="uk-flex">
          <a class="uk-margin-right uk-form-file uk-button uk-button-small uk-button-primary" :class="{'uk-disabled': loading}">
            <span class="util__nobreak" v-if="loading"><i class="uk-icon-spin uk-icon-refresh"></i></span>
            <span class="util__nobreak" v-else>Browse</span>
            <input accept="image/x-png, image/gif, image/jpeg" v-on:change="upload('og_image', $event)" class="upload-select" type="file">
          </a>
          <input v-model="model.og_image" type="text" class="uk-form-small uk-flex-item-auto">
          <a class="uk-margin-left" v-if="model.og_image" href="{{ model.og_image }}" target="_blank"><i class="uk-icon-search"></i></a>
        </div>
      </div>
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
      <div class="uk-placeholder uk-margin-bottom-remove uk-margin-top-remove">
        <div class="uk-flex">
          <a class="uk-margin-right uk-form-file uk-button uk-button-small uk-button-primary" :class="{'uk-disabled': loading}">
            <span class="util__nobreak" v-if="loading"><i class="uk-icon-spin uk-icon-refresh"></i></span>
            <span class="util__nobreak" v-else>Browse</span>
            <input accept="image/x-png, image/gif, image/jpeg" v-on:change="upload(key, $event)" class="upload-select" type="file">
          </a>
          <input v-model="model.twitter_image" type="text" class="uk-form-small uk-flex-item-auto">
          <a class="uk-margin-left" v-if="model.twitter_image" href="{{ model.twitter_image }}" target="_blank"><i class="uk-icon-search"></i></a>
        </div>
      </div>
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
        og_site_name: 'Your description',
        twitter_title: 'Yout title',
        twitter_site: '@your_site',
        twitter_description: 'Your description',
        twitter_image: ''
      }
    },
    upload: function(key, event) {
      let file = event.target.files[0]

      if (!file) {
        return
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
