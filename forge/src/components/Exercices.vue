<script setup>
     import { ref } from 'vue' 
     const message = ref('Bonjour vue') ;
     const compteur = ref(0)  ;
     function add() {
         compteur.value ++;
     }
     function AfficherSaisie(event) {
         message.value = event.target.value;
     }
     const exo =  ref('') ;


</script>
<template>
     <div>
          <h1> test</h1>
          <h2> {{  message }}</h2>
          <button @click="add">Compteur</button>
          <p>Compteur : {{ compteur }} </p>
          <input type="text" @input="AfficherSaisie">
          <input type="text" v-model="exo">
          <p> {{ exo }}  </p>
     </div>
</template>
