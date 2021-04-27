<template>
 
    <li  @click="check"> {{answer}}</li>
  
</template>

<script>
export default {
  
  name: "risposte",

  props: {

    answer: {
      type: String,
    },

    Myclass: {
      type: String,
    },

    


  },

  data () {
    return {
      myvar:"",
      
    }
  },

  methods: {
    check: function () {
      
      this.$emit('control', this.myvar);
      console.log(this.myvar);
    }
  }
 

}
</script>

<style>
.green {
  background-color: green;
  animation-name: lampeggiogreen;
  animation-duration: 2s;
}

.red {
  background-color: red;
  animation-name: lampeggiored;
  animation-duration: 2s;
}

@keyframes lampeggiogreen {
  0%   {background-color: green;}
  25%  {background-color:  transparent;}
  50%  {background-color: green;}
  100% {background-color:transparent ;}
}

@keyframes lampeggiored {
  0%   {background-color: red;}
  25%  {background-color:  transparent;}
  50%  {background-color: red;}
  100% {background-color:transparent ;}
}


</style>