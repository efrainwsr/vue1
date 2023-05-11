
<script>
  export default{
    data () {
      return {
        msg: "Formulario",
        state: 3,
        estado: "Inactivo",
        input1:""
      }
    },

    methods:{
      validarForm(){
        if(this.input1 =="" || this.input ===null){
          this.state = false
          this.estado = "Inactivo"
        }else{
          this.state = true
          this.estado = "Activo"
        }
      }
    }
  }
</script>


<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3 class="">{{ input1 }}</h3>
    <input @keyup="validarForm" type="text" v-model="input1">
    <button :disabled="!state" type="button">{{ estado }}</button>
    <p v-if="!state" class="red">Campo obligatorio</p>
  </div>
</template>



<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

.hasError{
  color: green
}

.red{
  color: red;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
