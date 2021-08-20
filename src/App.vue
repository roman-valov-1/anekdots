<template>
   <div class="app">
      <search-form @getList="getAnekdots"/>
      <anekdots-list 
         @like="likeAnekdot" 
         @dislike="dislikeAnekdot"
         :anekdots="anekdots"
         :keysLocalStorage="keysLocalStorage"
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
         anekdots: [],
         keysLocalStorage: []
      }
   },
   mounted() {
      if (localStorage.key) {
         this.keysLocalStorage = Object.keys(localStorage)
         console.log(this.keysLocalStorage)
      }
   },
   methods: {
      getAnekdots(array) {
         this.anekdots = array.map(el => {
            if (this.keysLocalStorage.includes(String(el.id))) {
               return {...el, liked: true};
            } else {
               return {...el, liked: false};
            }
         });
         
      },
      likeAnekdot(anekdot) {
         let likedAnekdot = this.anekdots.find(el => el.id === anekdot.id);
         likedAnekdot.liked = true;
         localStorage.setItem(`${likedAnekdot.id}`, JSON.stringify(likedAnekdot));
      },
      dislikeAnekdot(anekdot) {
         let dislikedAnekdot = this.anekdots.find(el => el.id === anekdot.id);
         dislikedAnekdot.liked = false;
         localStorage.removeItem(`${dislikedAnekdot.id}`);
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