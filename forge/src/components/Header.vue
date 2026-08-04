<template>
    <header class="app">
    <div class="brand">
      <span class="logo">FORGE</span>
      <span class="tag">Training</span>
    </div>
    <button class="btn-lib" @click="modalSeance" id="openLib"><span class="dot"></span> Séances</button>
  </header>

     <div
      v-if="modalOuverte"
      class="modal"
      @click.self="fermerModal"
    >
    
      <div class="modal-content">
        <button
          class="close"
          type="button"
          aria-label="Fermer la fenêtre"
          @click="fermerModal"
        >
          &times;
        </button>
        <h2>titre de la modal</h2>
        <p>Bonjour ceci est une fenetre modal.</p>
    </div>
    </div>


</template>

<script setup>
    import { ref } from 'vue' 
    const modalOuverte =ref(false);
    function modalSeance() {
        modalOuverte.value = true;
    }
    function fermerModal() {
        modalOuverte.value = false;
    }

   
</script>

<style scoped>
main {
            font-family: Arial, Helvetica, sans-serif;
            padding: 40px;
        }
        .modal{
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(5, 1, 1, 0.6);
            justify-content: center;
            align-items: center;
            display: flex;
        }
        .modal-content { 
            justify-content: center;
            align-items: center;
            background: rgb(125, 19, 19);
            padding: 20px;
            width: 400px;
            max-width: 90%;
            border-radius: 10px;
            position: relative; 
            box-shadow: 0px 10px 30px rgba(0,0,0,0.3);
        }
        .close {
            position: absolute;
            top: 10px;
            right: 15px;
            font-size: 28px ;
            cursor: pointer;
        }
</style>