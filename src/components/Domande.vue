<template>
<div class="overlay">
  
  <div id="domanda">
      <p>{{domanda}}</p>
      <div class="triangle-right"></div>
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

<style>

#domanda {
  height: 50px;
  display: flex;
  position: relative;
  align-items: center;
 
}

#domanda p {
  line-height: 48px;
  border-top: 1px solid white;
  border-bottom: 1px solid white;
  border-radius: 8px;
}

.overlay {
  width: 100% ;
  display: flex;
  margin: 40px 0;
  height: 50px;
  justify-content: center;
  overflow: hidden;
}

 .triangle-right {
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

/* .triangle-right {
    display: inline-block;
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 48px 0 48px 200px;
    border-color: transparent transparent transparent #6980fe;
} */

#domanda::before {
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


</style>