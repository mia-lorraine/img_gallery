<template>
  <div id="app">
    <h3> Vue Albums List </h3>
    <!-- <p v-for="album in albums" :key="album.id"> {{album.title}} </p> -->

    <table v-bind:colspan="5">
    <!-- <tr v-for="photo in photos" :key="photo.id"> 
      <td> <img v-bind:src="photo.url" v-bind:alt="photo.title"> </td> -->
      <div v-for="photo in photos" :key="photo.id">
      <tr>
        <td> {{photo.id}}</td>
        <td> {{photo.title}}</td>
     </tr>
     </div>
    </table>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'app',
  data() {
    return {
      albums: [], //array with all the data
      photos: [],
    };
  },
  mounted() {
    axios.all([ 
    axios.get('https://jsonplaceholder.typicode.com/albums'),
    axios.get('https://jsonplaceholder.typicode.com/photos')
    ])
    .then(axios.spread((albumRes, photosRes) => {
      this.albums = albumRes.data,
      this.photos = photosRes.data
      // console.log(this.albums, this.photos)
    })
  ) 
  },
};
</script>

<style>
body {
  width: 80%;
  margin: 2em auto 0 auto;
}
</style>
