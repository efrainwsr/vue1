<script setup>

defineProps({
  titulo:"",
  })

import {ref, computed} from 'vue'
 
  const cont = ref(0)

  const incrementar = () => {
          cont.value++;
  }
  const decrementar = () =>{
          cont.value--;
        }
  const resetear = () => {
          cont.value = 0
        }

  const classCont = computed(() => {
    if (cont.value === 0) {
         return "zero";
        }
          return cont.value > 0 ? "positivo" : "negativo";
   });

</script>

<template>
  <div class="col-sm-3">
    <div class="card" style="width: 18rem;">
      <h5 class="card-title">{{ titulo }}</h5>
      <img src="img.png" class="card-img-top" alt="">
      <div class="card-body">
          
          <button type="button" @click="decrementar" class="btn btn-outline-primary btn-sm" >Disminuir -</button>
          <button type="button" @click="resetear" class="btn btn-outline-primary btn-sm">Resetear</button>
          <button type="button" @click="incrementar" class="btn btn-outline-primary btn-sm">Aumentar +</button>
  
       <p :class="classCont">Contador: {{ cont }}</p>
      </div>
    </div>
  </div>
 
  
  

  
</template>

<style scoped>
  .positivo{
	color: green
  }
  .negativo{
	color: red
  }
  .zero{
	color: black
  }
</style>