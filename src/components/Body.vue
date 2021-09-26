<template>
  <div>
    <h1>Vuegram</h1>
    <button v-on:click="loadImg">Tests results</button>
    <div v-for="photo in photoArray" :key="photo.id">
        <p>{{photo.description}}</p>
        <p>{{photo.alt_description}}</p>
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
