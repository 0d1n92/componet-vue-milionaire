<template>
  <div id="app">
      <Domande :domanda="SelectedQuery.domanda" />
      <ul>
        <Risposte v-for="(risposte, index) in SelectedQuery.risposte "  @control="validateAnswer(risposte.bool,index)" :answer="risposte.Risposta" :key="index"  :class="risposte.class" />
      </ul>
    
  </div>
</template>

<script>
import Domande from "./components/Domande.vue";
import Risposte from "./components/Risposte.vue";

export default {
  name: "App",
  components: {
    Domande,
    Risposte
  },
  
  data () {
    return {
    
      SelectedQuery: "",

      Class: "",
      
      Query: [
         
       {
         'domanda': "Di che materiale è fatta la punta di un giavellotto olimpico?",

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

        /*  'risposte': {

           'metallo': true,
           'legno': false,
           'bronzo': false,
           'alluminio': false,  

         } */
       },
        {
         'domanda': "Chi è stato il primo calciatore italiano a vincere la Scarpa d'Oro, il premio che si assegna al miglior goleador del calcio europeo?",

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


          /* 'risposte': {

           'Luca Toni': true,
           'Francesco Totti': false,
           'Roberto Baggio': false,
           'Paolo Rossi': false, 

         } */
       },
        {
         'domanda': "Nell'Italia Repubblicana, quale tra i partiti politici elencati non ha espresso almeno un presidente del consiglio che militasse nelle sue fila?",
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

          /* 'risposte': {

           'Partito liberale': true,
           'Partito Comunista': false,
           'Democrazia Cristiana': false,
           'Forza Italia': false, 
            
         } */
       },
        {
         'domanda': "Il verbo leggere deriva dal latino legere, affine a un verbo greco che originariamente significava anche... ?",
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

        /* 'risposte': {

           'Raccogliere': true,
           'Leggere': false,
           'Imparare': false,
           'Apprendere': false, 
            
         } */

       },
        {
         'domanda': "Secondo uno studio pubblicato dalla Harvard Medical School, quale tra le attività elencate brucia più calorie in 30 minuti",

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


           /* 'interrare piantine': true,
           'Nuotare': false,
           'Leggere': false,
           'Sciare': false,    */
         
       },
        {
         'domanda': "Dieci anni fa veniva caricata una foto che apriva la rivoluzionaria era di un nuovo social network: Instagram.Oltre a un cane, cosa ritraeva?",

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

    randomQuery: function ()  {
      const min=0;
      const max= this.Query.length;

      this.SelectedQuery = this.Query[ Math.floor(Math.random() * (max - min)) + min];
  
    },

    validateAnswer: function (value,index) {
      let self= this;
      let i= index;
      if(value==true) {
        this.SelectedQuery.risposte[index].class+=" green";
        
      } else {
        this.SelectedQuery.risposte[index].class+=" red";
      }
       
      setTimeout(function(){ self.randomQuery() 
        self.SelectedQuery.risposte[i].class="risposte"    
      }, 3000);
    }
    
  },

  mounted () {
    
    this.randomQuery();
    
  }

}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
