<template>
  <div id="riassunto">
    <table id="table_riassunto">
      <thead>
        <tr>
         <th>Domanda</th>
         <th>Risposta</th>
         <th>Risultato</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(risposte, index) in story" :key=index>
          <td>{{guess[risposte].domanda}}</td>
          <td>{{guess[risposte].clicked}}</td>
          <td>{{guess[risposte].guessed}}</td>
        </tr>
      </tbody>
    </table>

  </div>
</template>

<script>
export default {

  props: {
    
    guess: {
      type: Array,
    },

    story: {
      type: Array,
    }
  }

}
</script>

<style lang="scss">

#table_riassunto {

  margin-top:50px;
  border-collapse: collapse; 
  tbody {
    tr {
      height: 50px;
      border-bottom: 1px solid white;
  
    }
  }
}  



</style>