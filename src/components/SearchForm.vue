<template>
   <div>
      <form @submit.prevent>
         <h3>Поиск анекдота по слову на английском</h3>
         <div>
            <input
            :value="searchString"
            @input="searchString = $event.target.value"
            class="input"
            type="text" 
            placeholder="Введите слово для поиска"
            >
         </div>
         <button @click="getAnekdots" class="btn">Искать</button>
      </form>
   </div>
</template>

<script>
import axios from 'axios';

export default {
   data () {
      return {
         searchString: '',
         anekdotsArray: []
      }
   },
   methods: {
      async getAnekdots() {
         try {
            const response = await axios.get(`https://v2.jokeapi.dev/joke/Any?type=single&contains=${this.searchString}&amount=10`);

            if (response.data.error === false) {
               this.anekdotsArray = response.data.jokes;
            } else if(response.data.error === true) {
               alert("Совпадений не найдено!");
               this.anekdotsArray = [];
            }
         } catch (e) {
            alert("Error");
         }
         this.searchString = '';
         this.$emit('getList', this.anekdotsArray);
      }
   }
   
}
</script>

<style>
.input {
   width: 100%;
   padding: 5px 10px;
   margin: 10px 0px;
}
.btn {
   width: 100%;
   padding: 5px 10px;
   margin-bottom: 10px;
   cursor: pointer;
}
</style>