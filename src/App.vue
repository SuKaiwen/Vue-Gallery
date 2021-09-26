<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Body
    :photoArray = "photos.photoArray"
  />
</template>

<script>
import Body from './components/Body.vue'

export default {
  name: 'App',
  components: {
    Body
  },

  data(){
    return{
      photos:{
        photoArray: [],
      },

      user:{
        userArray: [],
      }
    }
  },

  methods:{
    async loadImg(){
      const res = await fetch(`https://api.unsplash.com/search/photos/?query='auckland'&per_page=9&client_id=${process.env.VUE_APP_API_KEY}`);
      const results = await res.json();
      const sorted = results.results.sort((a, b) => (a.height/a.width) > (b.height/b.width) ? -1: 1);
      this.photos.photoArray = sorted;
      console.log(this.photos.photoArray);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
