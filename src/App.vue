<template>
  <div id="app">
    <header>
        <img src="img/logo.svg" alt="milionaire">
    </header>
    <main>
      <div v-if="!finished" id="container">
        <Domande :domanda="SelectedQuery.domanda" />

        <div  id="container_risposte">
          <Risposte  v-for="(risposte, index) in SelectedQuery.risposte "  @control="validateAnswer(risposte.bool,index,risposte.Risposta )" :answer="risposte.Risposta" :key="index"  :Myclass="risposte.class" />
        </div> 
      </div>   
      <div v-else>
        <Riassunto :story="story" :guess="Query" />  
      </div> 
        
   
    </main>  
    
  </div>
</template>

<script>
import Domande from "./components/Domande.vue";
import Risposte from "./components/Risposte.vue";
import Riassunto from "./components/Riassunto.vue";

export default {
  name: "App",
  components: {
    Domande,
    Risposte,
    Riassunto
  },
  
  data () {
    return {

      story: [],

      finished: false,

      answerStory:[],
    
      SelectedQuery: " ",
      
      Query: [
         
       {
         'domanda': "Di che materiale è fatta la punta di un giavellotto olimpico?",

         'guessed': 'sbagliata',

         'clicked': null,
        
         'risposte': [
           {
           'Risposta': 'Metallo',
           'bool':  true,
           'class': 'risposte'
            
           },

          {
           'Risposta': 'Legno',
           'bool': false,
            'class': 'risposte'
          },

          {
           'Risposta': 'PVC',
           'bool': false,
            'class': 'risposte'
          },

          {
           'Risposta': 'Pietra',
           'bool': false,
            'class': 'risposte'
           }
         ],


       },
        {
         'domanda': "Chi è stato il primo calciatore italiano a vincere la Scarpa d'Oro, il premio che si assegna al miglior goleador del calcio europeo?",

         'guessed': 'sbagliata',

         'clicked': null,
      
         'risposte': [
           {
           'Risposta': 'Luca Tony',
           'bool':  true,
            'class': 'risposte'
           },

          {
           'Risposta': 'Roberto Baggio',
           'bool': false,
            'class': 'risposte'
          },

          {
           'Risposta': 'Paolo Rossi',
           'bool': false,
            'class': 'risposte'
          },

          {
           'Risposta': 'Francesco Totti',
           'bool': false,
            'class': 'risposte'
           }
         ],

       },
        {
         'domanda': "Nell'Italia Repubblicana, quale tra i partiti politici elencati non ha espresso almeno un presidente del consiglio che militasse nelle sue fila?",

          'guessed': 'sbagliata',

          'clicked': null,

          'risposte': [
           {
           'Risposta': 'Partito Liberali',
           'bool':  true,
            'class': 'risposte'
           },

          {
           'Risposta': 'Partito Comunista',
           'bool': false,
           'class': 'risposte'
          },

          {
           'Risposta': 'Democrazia Cristiana',
           'bool': false,
            'class': 'risposte'
          },

          {
           'Risposta': 'Forza Italia',
           'bool': false,
            'class': 'risposte'
           }
         ],


       },

        {
         'domanda': "Il verbo leggere deriva dal latino legere, affine a un verbo greco che originariamente significava anche... ?",

         'guessed': 'sbagliata',

         'clicked': null,


          'risposte': [
           {
           'Risposta': 'Raccogliere',
           'bool':  true,
            'class': 'risposte'
           },

          {
            'Risposta': 'Leggere',
            'bool': false,
            'class': 'risposte'
          },

          {
            'Risposta': 'Imparare',
            'bool': false,
            'class': 'risposte'
          },

          {
            'Risposta': 'Apprendere',
            'bool': false,
            'class': 'risposte'
           }
         ],


       },
        {
         'domanda': "Secondo uno studio pubblicato dalla Harvard Medical School, quale tra le attività elencate brucia più calorie in 30 minuti",

         'guessed': 'sbagliata',

         'clicked': null,

        'risposte': [
           {
            'Risposta': 'interrare piante',
            'bool':  true,
            'class': 'risposte'
           },

          {
            'Risposta': 'Nuotare',
            'bool': false,
            'class': 'risposte'
          },

          {
            'Risposta': 'Leggere',
            'bool': false,
            'class': 'risposte'
          },

          {
            'Risposta': 'Sciare',
            'bool': false,
            'class': 'risposte'
           }
         ],

       },
        {
          'domanda': "Dieci anni fa veniva caricata una foto che apriva la rivoluzionaria era di un nuovo social network: Instagram.Oltre a un cane, cosa ritraeva?",

          'guessed': 'sbagliata',

          'clicked': null,

         'risposte': [
           {
            'Risposta': 'Piede femminile',
            'bool':  true,
            'class': 'risposte'
           },

          {
           'Risposta': 'Cane',
           'bool': false,
           'class': 'risposte'
          },

          {
           'Risposta': 'Cibo',
           'bool': false,
            'class': 'risposte'
          },

          {
           'Risposta': 'Mazzo di fiori',
           'bool': false,
           'class': 'risposte'
           }
         ],

       },

      ]
      
    }
  },

  methods : {

    shaffle: function (array) {
    //nome algoritmo Fisher–Yates Shuffle
    let currentIndex = array.length; 
    let temporaryValue= 0; 
    let randomIndex = 0;

    // While there remain elements to shuffle...
    while (0 !== currentIndex) {

      // prendo un elemento a caso dal array
      randomIndex = Math.floor(Math.random() * currentIndex);
      currentIndex -= 1;

     //utilizzo ultimo elemento dell'array come valore random
     //utilizzo primo elemento dell'array come elemento ancora da mescolare
      temporaryValue = array[currentIndex];
      array[currentIndex] = array[randomIndex];
      array[randomIndex] = temporaryValue;
    }

      return array;
    },


    randomQuery: function ()  {
  
      const min=0;
      const max= this.Query.length;
      let x = Math.floor(Math.random() * (max - min)) + min;
      
      if(this.story.length < max)  {
      //controllo che la domando non è ripetuta
        while(this.story.includes(x)) {

          x = Math.floor(Math.random() * (max - min)) + min; 

        }
        //pusho nell'array indice che uso per il controllo dei dupplicati
        this.story.push(x);

        this.SelectedQuery=this.Query[x];
      } else if (this.story.length == max){

        this.finished=true;
      }

        
        //mescolo le risposte
        this.shaffle(this.SelectedQuery.risposte)
      
      
    },

    validateAnswer: function (value,index, text) {
      const self = this;
     
      this.Query[this.story[this.story.length-1]].clicked=  text;
      

      if(value==true) {
        //cambio valore storico della domanda
       
        console.log('storia',this.story);
        this.Query[this.story.length-1].guessed="coretta"
       

        this.SelectedQuery.risposte[index].class+=" green";
        
      } else {

        
        this.SelectedQuery.risposte[index].class+=" red";

      }
       
      setTimeout(function(){ 

        self.randomQuery();
        
        self.SelectedQuery.risposte[index].class="risposte";

      }, 3000);

      console.log(this.Query);

    }
  },

  mounted () {
    
    this.randomQuery();
    
  }

}
</script>

<style lang="scss">

/* RESET */
* {
margin: 0;
padding: 0;
box-sizing: border-box;
}
button,input,optgroup,select,textarea {
font-family: inherit; /* 1 */
font-size: 100%; /* 1 */
line-height: 1.15; /* 1 */
margin: 0; /* 2 */
border: 0;
}
select:focus,
button:focus,
input:focus,
textarea:focus {
border: 0;
outline: none;
}
/*RESET CLOSE*/

body {
  height: 100vh;
  background-color: #11093a;
  color: white;
  
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

main {

display: flex;
flex-direction: column;
align-items: center;
  
} 

#container {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

header {
 background-color: #130c7d;
}

header img {
  height: 180px;
  margin:35px
}

#container_risposte {
  width: 600px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}


</style>
