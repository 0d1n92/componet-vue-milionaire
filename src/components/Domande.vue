<template>
<div class="overlay">
  
  <div id="domanda">
      <p>{{domanda}}</p>
  </div>

</div>  
  
</template>

<script>
export default {
  name:"Domande",

  props: {
    
      //proprietà del nostro componente, il modo con cui un compenente figlio riceve i dati dal componenete padre
      domanda: {

      type: String, //variabile del mio componente che ricevo in input dal padre

      },
      
  },
}  
</script>

<style lang="scss">

#domanda {
  height: 50px;
  display: flex;
  position: relative;
  align-items: center;
  p {
    line-height: 48px;
    border-top: 1px solid white;
    border-bottom: 1px solid white;
    border-radius: 8px;
  }
  &::after{
  content: '';
  position: absolute;
  height: 47px;
  right: -10px;
  width: 47px;
  border-radius: 8px;
  border: 1px solid white;
  transform: rotate(45deg);
  border-bottom: none;
  border-left:none;
  }
  &::before {
  content: '';
  position: absolute;
  height: 47px;
  left: -10px;
  width: 47px;
  border-radius: 8px;
  border: 1px solid white;
  transform: rotate(45deg);
  border-top: none;
  border-right:none;
  }

}

.overlay {
  width: 100% ;
  display: flex;
  margin: 40px 0;
  height: 50px;
  justify-content: center;
  overflow: hidden;
}

</style>