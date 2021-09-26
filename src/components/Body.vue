<template>
  <div>
    <h1>Vuegram</h1>
    <button v-on:click="loadImg">Tests results</button>
    <div class="container">
        <div class="grid">
            <div class="card-alt" v-for="photo in photoArray" :key="photo.id">
                <img class="photo" :src="photo.urls.small" />
                <h3 v-if="photo.alt_description !== null">{{photo.alt_description}}</h3>
                <h3 v-else>Unnamed</h3>
                <br />
                <p>Description: {{photo.description}}</p>
                <p>Created: {{photo.created_at}}</p>
                <p>Likes: {{photo.likes}}</p>
                <br />
                <p>Tags: </p>
                <hr />
                <div class="container">
                    <div v-for="tags in photo.tags" :key="tags.title">
                        <va-button size="small" color="info">{{tags.title}}</va-button>
                    </div>
                </div>
                <hr />
                <p>Size: {{photo.width}}px x {{photo.height}}px</p>
                <br />
                <p>By {{photo.user.first_name}} {{photo.user.last_name}} | @{{photo.user.username}}</p>
                <br />
            </div>
        </div>
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
    .container{
        margin:auto;
        width:100%;
        display: flex;
        justify-content: center;
    }
    
    .grid{
        display:flex;
        flex-direction: row;
        flex:3;
        flex-wrap: wrap;
        padding:10px;
        max-width:70%;
        justify-content: space-evenly;
    }

    .card-alt{
        text-align: left;
        align-items: center;
        width:30%;
    }

    .photo{
        width:100%;
    }

    p{
        font-size: 14px;
    }
</style>
