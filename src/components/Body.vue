<template>
  <div>
    <h1>Vuegram</h1>
    <button v-on:click="loadImg">Tests results</button>
    <div v-for="photo in photoArray" :key="photo.id">
        <img :src="photo.urls.small" />
        <p>Description: {{photo.description}}</p>
        <p>Alt: {{photo.alt_description}}</p>
        <p>Created: {{photo.created_at}}</p>
        <p>Likes: {{photo.likes}}</p>
        <div v-for="tags in photo.tags" :key="tags.title">
            <p>{{tags.title}}</p>
        </div>
        <p>Size: {{photo.width}}px x {{photo.height}}px</p>
        <p>By {{photo.user.first_name}} {{photo.user.last_name}} | @{{photo.user.username}}</p>
        <br />
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    photoArray: Array,
  },

  methods:{
    loadImg(){
      this.$parent.loadImg();
    },
  }
}
</script>

<style scoped>

</style>
