<template>
   <div>
      <form @submit.prevent>
         <h3>Поиск анекдота по слову на английском</h3>
         <div>
            <input
            class="input"
            type="text" 
            placeholder="Введите слово для поиска"
            >
         </div>
         <button class="btn">Искать</button>
      </form>
   </div>
</template>

<script>
export default {
   
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
}
</style>