<template>
  <div>
    <h1 class = "display-1">VUEGRAM</h1>
    <div class="search">
    <form>
        <input type="term" required v-model="term">
    </form>
    
    <button v-on:click="changeTerm(term)">Search</button>
    </div>
    <div class="top">
        <h1>Showing results for "{{message}}"... </h1>
    </div>
    <div class="container">
        <div class="grid" >
            <div class="card-alt" v-for="photo in photoArray" :key="photo.id">
                <img class="photo" :src="photo.urls.small" />
                <div class="card-text">
                    <div class="top-part">
                        <a :href="photo.links.html"><i class="fas fa-camera fa-2x"></i></a>
                        <a :href="photo.links.download"><i class="fas fa-download fa-2x"></i></a>
                    </div>
                    <div>
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
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    photoArray: Array,
    message: String,
  },

  data(){
      return{
          term:""
      }
  },

  methods:{
    changeTerm(term){
      this.$parent.changeTerm(term); 
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
        display:flex;
        flex-direction: column;
        overflow: scroll;
        -ms-overflow-style: none;  /* Internet Explorer 10+ */
        scrollbar-width: none;  /* Firefox */
        height:100%;
        background-color: rgba(0,0,0, 0.7);
        color:white;
    }

    .card-text::-webkit-scrollbar { /* WebKit */
        width: 0;
        height: 0;
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
        justify-content: space-between;
        
        display:none;
    }

    i{
        padding:5px;
    }

    p{
        font-size: 14px;
    }

    a{
        color:white;
    }

    a:hover{
        color:white;
    }

    .top{
        text-align: left;
        max-width:80%;
        margin:auto;
        padding:2%;
    }

    .top-part{
        text-align: right;
        justify-content: space-between;
    }

    .search{
        justify-content: center;
        display:flex;
        flex-direction: row;
        margin-top:50px;
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
