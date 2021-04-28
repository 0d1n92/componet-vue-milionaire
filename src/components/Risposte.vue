<template>
  <div class="wapper_answer">
    <p :class="Myclass"  @click="check"> {{answer}}</p>
  </div>  
 
</template>

<script>
export default {
  
  name: "risposte",

  props: {

    answer: {
      type: String,
    },

    index: {
      type: Number,
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

.wapper_answer {
  width: 250px;
  display: flex;
  justify-content: center;
  position: relative;
  margin: 40px 0;
  height: 50px;
  overflow: hidden;
}  

.wapper_answer p{
  width: 200px;
  line-height: 48px;
  justify-content: center;
  display: flex;
  position: relative;
  align-items: center;
  border-top: 1px solid white;
  border-bottom: 1px solid white;
  border-radius: 8px;
}

.wapper_answer p::after {
  content: '';
  position: absolute;
  height: 47px;
  right: -10px;
  overflow: hidden;
  width: 47px;
  border-radius: 8px;
  border: 1px solid white;
  transform: rotate(45deg);
  border-bottom: none;
  border-left:none;

}

.wapper_answer p::before {
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