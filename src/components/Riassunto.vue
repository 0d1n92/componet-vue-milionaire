<template>
  <div id="riassunto">
    <table>
      <thead>
        <tr>
         <th>Domanda</th>
         <th>Risposta</th>
         <th>Risultato</th>
        </tr>
      </thead>
      <tr v-for="(risposte, index) in story" :key=index>
        <td>{{guess[risposte].domanda}}</td>
        <td>{{guess[risposte].clicked}}</td>
        <td>{{guess[risposte].guessed}}</td>
      </tr>
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

<style>

</style>