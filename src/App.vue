<template>
  <div id="app">
    <h3> Vue Albums List </h3>
    <!-- <p v-for="album in albums" :key="album.id"> {{album.title}} </p>  -->
  
    <!-- <div v-for="photo in photos" :key="photo.id"> -->
        <table v-bind:colspan="5">
          <thead>
            <td> album ID </td>
            <td> album title </td>
            <td> photo title</td>
            <td> photo thumbnail </td>
          </thead>
          <tr v-for="photo in photos" :key="photo.id">
            <td> {{photo.albumId}}</td>
              <td> 
                {{ photo.albumId === 1 ? "quidem molestiae enim" : false }}
                {{ photo.albumId === 2 ? "sunt qui excepturi placeat culpa" : false }}
                {{ photo.albumId === 3 ? "omnis laborum odio" : false }}
                {{ photo.albumId === 4 ? "non esse culpa molestiae omnis sed optio" : false }}
                {{ photo.albumId === 5 ? "eaque aut omnis a" : false }}
                {{ photo.albumId === 6 ? "natus impedit quibusdam illo est" : false }}
                {{ photo.albumId === 7 ? "quibusdam autem aliquid et et quia" : false }}
                {{ photo.albumId === 8 ? "qui fuga est a eum" : false }}
                {{ photo.albumId === 9 ? "saepe unde necessitatibus rem" : false }}
                {{ photo.albumId === 10 ? "distinctio laborum qui" : false }}

             </td>
            <td> {{photo.title}} </td>
            <td> <img src = photo.thumbnailUrl alt="photo"/> </td>
          </tr>
        </table>
  </div> <!-- app div --> 
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
