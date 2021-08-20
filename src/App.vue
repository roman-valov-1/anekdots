<template>
   <div class="app">
      <search-form @getList="getAnekdots"/>
      <anekdots-list 
         @like="likeAnekdot" 
         @dislike="dislikeAnekdot"
         :anekdots="anekdots"
      />
   </div>
</template>

<script>
import AnekdotsList from "./components/AnekdotsList.vue";
import SearchForm from "./components/SearchForm.vue";

export default {
   components: {
      AnekdotsList,
      SearchForm
   },
   data() {
      return {
         anekdots: []
      }
   },
   methods: {
      getAnekdots(array) {
         this.anekdots = array.map(el => ({...el, liked: false}));
         console.log(this.anekdots);
      },
      likeAnekdot(anekdot) {
         let likedAnekdot = this.anekdots.find(el => el.id === anekdot.id);
         likedAnekdot.liked = true;
         console.log(this.anekdots);
      },
      dislikeAnekdot(anekdot) {
         let dislikedAnekdot = this.anekdots.find(el => el.id === anekdot.id);
         dislikedAnekdot.liked = false;
         console.log(this.anekdots);
      }
   }
}
</script>

<style>
* {
   box-sizing: border-box;
   margin: 0;
   padding: 0;
}
.app {
   margin: 0 auto;
   padding: 20px;
   max-width: 600px;
}
</style>