<template>
   <div class="anekdotsList">
      <div v-for="anekdot in anekdots" >
         <div v-if="anekdot.liked === true" class="anekdotItemLiked">
            {{anekdot.joke}}
            <div>
               <button
                  @click="$emit('dislike', anekdot)"
                  class="btn-like"
               >
                  Dislike
               </button>
            </div>
         </div>
         <div v-else class="anekdotItem">
            {{anekdot.joke}}
            <div>
               <button
                  @click="$emit('like', anekdot)"
                  class="btn-like"
               >
                  Like
               </button>
            </div>
         </div>
      </div>
   </div>
</template>

<script>
export default {
   props: {
      anekdots: {
         type: Array
      },
      keysLocalStorage: {
         type: Array
      }
   }
}
</script>

<style>
.anekdotsList{
   display: flex;
   flex-direction: column;
}
.anekdotItem {
   margin: 10px 0px;
   padding: 5px;
   border: 1px solid black;
   word-wrap: break-word;
}.anekdotItemLiked {
   margin: 10px 0px;
   padding: 5px;
   border: 1px solid black;
   word-wrap: break-word;
   background-color: rgb(42, 207, 130);
}
.btn-like {
   margin: 5px;
   padding: 5px 10px;
   background-color: transparent;
   border: 1px solid rgb(10, 2, 85);
   border-radius: 5px;
   cursor: pointer;
}
</style>