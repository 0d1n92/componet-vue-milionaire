<template>
  <div>
    <p>{{domanda}}</p>
  </div>
  
</template>

<script>
export default {
  name:"Domande",

  props: {
    
      //proprietà del nostro componente, il modo con cui un compenente figlio riceve i dati dal componenete padre
      domanda: {

      type: String, //variabile del mio componente che ricevo in input dal padre

      }

      
  },
}  
</script>

<style>

</style>