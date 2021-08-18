<template>
   <div class="app">
      <search-form/>
      <anekdots-list :anekdots="anekdots"/>
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
         anekdots: [
            {id:1, body: "sadasdasd"},
            {id:2, body: "sadasdasd"},
            {id:3, body: "sadasdasd"},
            {id:4, body: "sadasdasd"},
         ]
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