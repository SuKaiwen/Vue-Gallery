<template>
  <div>
    <h1>Vuegram</h1>
    <button v-on:click="loadImg">Tests results</button>
    <div class="container">
        <div class="grid" >
            <div class="card-alt" v-for="photo in photoArray" :key="photo.id">
                <img class="photo" :src="photo.urls.small" />
                <div class="card-text">
                    <h3 v-if="photo.alt_description !== null">{{photo.alt_description}}</h3>
                    <h3 v-else>Unnamed</h3>
                    <br />
                    <p v-if="photo.description !== null">Description: {{photo.description}}</p>
                    <p v-else>No Description</p>
                    <br />
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
        justify-content: space-evenly;  
    }
    
    .grid{
        display:flex;
        flex-direction: row;
        flex:3;
        flex-wrap: wrap;
        padding:10px;
        max-width:80%;
        justify-content: space-evenly;
    }

    .card-alt{
        text-align: left;
        align-items: center;
        width:30%;
        position:relative;
        margin-top:20px;
    }

    .photo{
        width:100%;
        height:100%;
        object-fit: cover;
    }

    .card-alt:hover .card-text{
        opacity: 1;
        display:block;
        overflow: scroll;
        -ms-overflow-style: none;  /* Internet Explorer 10+ */
        scrollbar-width: none;  /* Firefox */
        height:100%;
    }

    .card-text::-webkit-scrollbar { /* WebKit */
        width: 0;
        height: 0;
    }

    .card-alt:hover .photo{
        opacity: 0.3;
    }

    .card-text{
        transition: .5s ease;
        opacity: 0;
        position: absolute;
        top: 0%;
        left: 0%;
        width:100%;
        padding:20px;
        text-align: left;
        position:absolute;
        overflow: hidden;
        background-attachment: fixed;
        display:none;
    }

    p{
        font-size: 14px;
    }

    @media (min-width:0px) and (max-width:600px){
        .grid{
            flex:1;
            max-width:80%;
        }

        .card-alt{
            width:100%;
        }
    }

    @media (min-width: 600px) and (max-width: 1024px){
        .grid{
            flex:2;
            max-width:90%;
        }

        .card-alt{
            width:45%;
        }
    }
</style>
