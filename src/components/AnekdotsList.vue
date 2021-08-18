<template>
   <div class="anekdotsList">
      <div v-for="anekdot in anekdots" >
         <div class="anekdotItem">{{anekdot.body}}</div>
      </div>
   </div>
</template>

<script>
export default {
   props: {
      anekdots: {
         type: Array
      }
   }
}
</script>

<style>
.anekdotsList{
   display: flex;
   flex-direction: column;
   border: 1px solid black;
}
.anekdotItem {
   margin: 10px 10px;
   padding: 5px;
   border: 1px solid black;
}
</style>