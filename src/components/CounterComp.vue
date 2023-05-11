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

  <div class="col col-sm-2">
    <div>
    <div class="card" style="width: 18rem;">
      <h5 class="card-title">{{ titulo }}</h5>
     <img src="../../public/img.png" class="card-img-top" alt="">
     <div class="card-body">
       <button class="btn btn-sm btn-primary" @click="decrementar">Disminuir -</button>
       <button @click="resetear" class="btn btn-sm btn-primary">Resetear</button>
       <button @click="incrementar" class="btn btn-sm btn-primary">Aumentar +</button>
       <p :class="classCont">Contador: {{ cont }}</p>
     </div>
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