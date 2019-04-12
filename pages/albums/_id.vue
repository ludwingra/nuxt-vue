<template lang="html">
  <div class="container">

    <header>
      <nuxt-link to="/">Volver</nuxt-link>
      <h1 class="title">{{album.title}}</h1>
    </header>

    <div class="columns is-multiline">
      <div class="column is-one-quarter" v-for="photo in photos" :key="photo.id">
        <img :src="photo.url" :alt="photo.title">
      </div>
    </div>
  </div>
</template>

<script>

import router from 'vue-router';
import axios from 'axios';
import env from '../../config/env';

export default {
  name: 'AlbumIndvPage',
  data() {
    return {
      album: {},
      photos: []
    }
  },
  created: async function(){
    let albumId = this.$route.params.id;
    let albumRes = await axios.get(`${env.endpoint}/albums/${albumId}`);
    this.album = albumRes.data;

    let photosRes = await axios.get(`${env.endpoint}/albums/${albumId}/photos`);
    this.photos = photosRes.data;
  }
}
</script>

<style lang="css" scoped>



</style>
