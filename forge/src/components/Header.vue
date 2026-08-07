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

     const PROGRAMS = [
  {
    id:"fullbody",
    name:"Full Body Débutant",
    desc:"3 séances/semaine, tout le corps à chaque fois. Idéal pour démarrer.",
    days:[
      {name:"Séance A", ex:[
        {n:"Squat",            m:"Jambes", s:3, r:"10", rest:120},
        {n:"Développé couché", m:"Pecs",   s:3, r:"10", rest:120},
        {n:"Rowing barre",     m:"Dos",    s:3, r:"10", rest:90},
        {n:"Développé militaire",m:"Épaules",s:3,r:"12", rest:90},
        {n:"Gainage",          m:"Abdos",  s:3, r:"40s", rest:45},
      ]},
      {name:"Séance B", ex:[
        {n:"Soulevé de terre", m:"Dos",    s:3, r:"8",  rest:150},
        {n:"Développé incliné",m:"Pecs",   s:3, r:"10", rest:120},
        {n:"Tractions assistées",m:"Dos",  s:3, r:"8",  rest:120},
        {n:"Fentes",           m:"Jambes", s:3, r:"12", rest:90},
        {n:"Crunch",           m:"Abdos",  s:3, r:"15", rest:45},
      ]},
      {name:"Séance C", ex:[
        {n:"Presse à cuisses", m:"Jambes", s:4, r:"12", rest:120},
        {n:"Dips",             m:"Pecs",   s:3, r:"10", rest:90},
        {n:"Tirage horizontal",m:"Dos",    s:3, r:"12", rest:90},
        {n:"Élévations latérales",m:"Épaules",s:3,r:"15",rest:60},
        {n:"Curl biceps",      m:"Biceps", s:3, r:"12", rest:60},
      ]},
    ]
  },
  {
    id:"ppl",
    name:"Push / Pull / Legs",
    desc:"Le grand classique : pousser, tirer, jambes. Pour progresser sérieusement.",
    days:[
      {name:"Push", ex:[
        {n:"Développé couché",   m:"Pecs",   s:4, r:"8",  rest:150},
        {n:"Développé incliné haltères",m:"Pecs",s:3,r:"10",rest:120},
        {n:"Développé militaire",m:"Épaules",s:4, r:"10", rest:120},
        {n:"Élévations latérales",m:"Épaules",s:4,r:"15",rest:60},
        {n:"Extensions triceps", m:"Triceps",s:3, r:"12", rest:60},
      ]},
      {name:"Pull", ex:[
        {n:"Tractions",          m:"Dos",    s:4, r:"8",  rest:150},
        {n:"Rowing barre",       m:"Dos",    s:4, r:"10", rest:120},
        {n:"Tirage vertical",    m:"Dos",    s:3, r:"12", rest:90},
        {n:"Curl barre",         m:"Biceps", s:3, r:"10", rest:75},
        {n:"Curl marteau",       m:"Biceps", s:3, r:"12", rest:60},
      ]},
      {name:"Legs", ex:[
        {n:"Squat",              m:"Jambes", s:4, r:"8",  rest:180},
        {n:"Presse à cuisses",   m:"Jambes", s:4, r:"12", rest:120},
        {n:"Leg curl",           m:"Ischios",s:3, r:"12", rest:90},
        {n:"Fentes marchées",    m:"Jambes", s:3, r:"12", rest:90},
        {n:"Mollets debout",     m:"Mollets",s:4, r:"15", rest:45},
      ]},
    ]
  },
  {
    id:"upperlower",
    name:"Haut / Bas",
    desc:"4 séances : on alterne le haut et le bas du corps deux fois par semaine.",
    days:[
      {name:"Haut A", ex:[
        {n:"Développé couché",   m:"Pecs",   s:4, r:"8",  rest:150},
        {n:"Rowing barre",       m:"Dos",    s:4, r:"10", rest:120},
        {n:"Développé militaire",m:"Épaules",s:3, r:"10", rest:90},
        {n:"Curl biceps",        m:"Biceps", s:3, r:"12", rest:60},
        {n:"Extensions triceps", m:"Triceps",s:3, r:"12", rest:60},
      ]},
      {name:"Bas A", ex:[
        {n:"Squat",              m:"Jambes", s:4, r:"8",  rest:180},
        {n:"Soulevé roumain",    m:"Ischios",s:4, r:"10", rest:120},
        {n:"Presse à cuisses",   m:"Jambes", s:3, r:"12", rest:120},
        {n:"Mollets debout",     m:"Mollets",s:4, r:"15", rest:45},
        {n:"Gainage",            m:"Abdos",  s:3, r:"45s",rest:45},
      ]},
      {name:"Haut B", ex:[
        {n:"Développé incliné",  m:"Pecs",   s:4, r:"10", rest:120},
        {n:"Tractions",          m:"Dos",    s:4, r:"8",  rest:150},
        {n:"Élévations latérales",m:"Épaules",s:4,r:"15",rest:60},
        {n:"Tirage horizontal",  m:"Dos",    s:3, r:"12", rest:90},
        {n:"Dips",               m:"Triceps",s:3, r:"10", rest:90},
      ]},
      {name:"Bas B", ex:[
        {n:"Soulevé de terre",   m:"Dos",    s:4, r:"6",  rest:180},
        {n:"Fentes bulgares",    m:"Jambes", s:3, r:"10", rest:120},
        {n:"Leg curl",           m:"Ischios",s:3, r:"12", rest:90},
        {n:"Leg extension",      m:"Quadris",s:3, r:"15", rest:75},
        {n:"Crunch lesté",       m:"Abdos",  s:3, r:"15", rest:45},
      ]},
    ]
  },
  {
    id:"hiit",
    name:"Cardio HIIT Maison",
    desc:"Sans matériel, récup courtes. Brûle-graisse à faire en 25 min.",
    days:[
      {name:"Circuit 1", ex:[
        {n:"Burpees",            m:"Full",   s:4, r:"40s", rest:20},
        {n:"Mountain climbers",  m:"Cardio", s:4, r:"40s", rest:20},
        {n:"Squats sautés",      m:"Jambes", s:4, r:"40s", rest:20},
        {n:"Pompes",             m:"Pecs",   s:4, r:"30s", rest:20},
        {n:"Gainage",            m:"Abdos",  s:4, r:"45s", rest:20},
      ]},
      {name:"Circuit 2", ex:[
        {n:"Jumping jacks",      m:"Cardio", s:4, r:"45s", rest:20},
        {n:"Fentes alternées",   m:"Jambes", s:4, r:"40s", rest:20},
        {n:"Pompes diamant",     m:"Triceps",s:4, r:"30s", rest:25},
        {n:"Relevés de jambes",  m:"Abdos",  s:4, r:"40s", rest:20},
        {n:"Talons-fesses",      m:"Cardio", s:4, r:"45s", rest:20},
      ]},
    ]
  },
];

    const modalOuverte =ref(false);

    function modalSeance() {
        modalOuverte.value = true;
    }
    
    function fermerModal() {
        modalOuverte.value = false;
    }

   

</script>
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
        <section
      v-for="programme in PROGRAMS"
      :key="programme.id"
      class="programme"
    >
      <h1>{{ programme.name }}</h1>

      <p class="programme-description">
        {{ programme.desc }}
      </p>

      <!-- Chaque séance : Séance A, Séance B, Push, Pull... -->
      <div
        v-for="exo in programme.days"
        :key="exo.name"
        class="jour"
      >
        <h2>{{ exo.name }}</h2>

        <!-- Chaque exercice -->
        <div
          v-for="exercice in exo.ex"
          :key="exercice.n"
          class="seance"
        >
          <p>{{ exercice.n }}</p>
        </div>
      </div>
    </section>

    </div>
    </div>
  <main class="programmes-container">
    
  </main>
  
      <!--
     <div>
          <h1> test</h1>
          <h2> {{  message }}</h2>
          <button @click="add">Compteur</button>
          <p>Compteur : {{ compteur }} </p>
          <input type="text" @input="AfficherSaisie">
          <input type="text" v-model="exo">
          <p v-if="compteur <5 ">Trop peu de serie</p>
          <p v-if="compteur >= 5 && compteur <= 10 ">bonne series</p>
          <p v-if="compteur > 10">Grosse seance</p>
     </div>
    -->
</template>

<style scoped>
:global(:root) {
  --ink: #0e1014;
  --surface: #16191f;
  --elev: #1e222b;
  --elev-2: #272c36;
  --line: #2c313b;
  --text: #f5f3ee;
  --muted: #8b909b;
  --gold: #f2c14e;
  --rest: #38e1d0;
  --radius: 16px;
  --radius-sm: 10px;
}

.app {
  max-width: 1100px;
  margin: 0 auto;
  padding: 22px 18px;

  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 16px;
}

.brand {
  display: flex;
  align-items: baseline;
  gap: 10px;
}

.logo {
  color: var(--gold);
  font-size: 34px;
  font-weight: 900;
  letter-spacing: 3px;
}

.tag {
  color: var(--muted);
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 3px;
  text-transform: uppercase;
}

.btn-lib {
  display: flex;
  align-items: center;
  gap: 8px;

  padding: 10px 14px;

  background: var(--surface);
  border: 1px solid var(--line);
  border-radius: var(--radius-sm);

  color: var(--text);
  font: inherit;
  font-weight: 600;

  cursor: pointer;
}

.btn-lib:hover {
  color: var(--gold);
  border-color: var(--gold);
}

.dot {
  width: 7px;
  height: 7px;

  background: var(--gold);
  border-radius: 50%;
}
/* Fond sombre qui recouvre tout l'écran */
.modal {
  position: fixed;
  inset: 0;
  z-index: 1000;

  display: flex;
  justify-content: center;
  align-items: center;

  padding: 20px;

  background: rgba(5, 7, 10, 0.82);
  backdrop-filter: blur(8px);
}

/* Fenêtre du modal */
.modal-content {
  position: relative;

  width: min(100%, 950px);
  max-height: 90vh;
  overflow-y: auto;

  padding: 35px 25px 25px;

  background: #0e1014;
  border: 1px solid #2c313b;
  border-radius: 18px;

  box-shadow: 0 25px 70px rgba(0, 0, 0, 0.65);
}

/* Bouton de fermeture */
.close {
  position: absolute;
  top: 12px;
  right: 15px;

  width: 38px;
  height: 38px;

  display: flex;
  justify-content: center;
  align-items: center;

  background: #1e222b;
  border: 1px solid #2c313b;
  border-radius: 10px;

  color: #f5f3ee;
  font-size: 27px;
  line-height: 1;

  cursor: pointer;
  transition: 0.2s;
}

.close:hover {
  color: #f2c14e;
  border-color: #f2c14e;
  transform: rotate(90deg);
}
/* Conteneur principal */
.programmes-container {
  max-width: 1100px;
  margin: 0 auto;
  padding: 30px 18px 100px;
  color: var(--text);
}

/* Un programme complet */
.programme {
  margin-bottom: 50px;
  padding: 24px;

  background: var(--surface);
  border: 1px solid var(--line);
  border-radius: var(--radius);
}

/* Nom du programme */
.programme > h1 {
  margin: 0 0 8px;

  color: var(--gold);

  font-size: clamp(28px, 5vw, 42px);
  font-weight: 700;
  letter-spacing: 1px;
}

/* Description du programme */
.programme-description {
  margin: 0 0 24px;

  color: var(--muted);
  font-size: 14px;
  line-height: 1.6;
}

/* Une séance complète : Séance A, Push, Pull... */
.jour {
  margin-top: 20px;
  padding: 18px;

  background: var(--ink);
  border: 1px solid var(--line);
  border-radius: var(--radius);
}

/* Nom de la séance */
.jour > h2 {
  margin: 0 0 14px;
  padding-bottom: 10px;

  color: var(--rest);

  border-bottom: 1px solid var(--line);

  font-size: 23px;
  font-weight: 600;
}

/* Une carte d'exercice */
.seance {
  position: relative;
  overflow: hidden;

  margin-top: 12px;
  padding: 16px 18px;

  background: var(--elev);
  border: 1px solid var(--line);
  border-radius: var(--radius-sm);

  transition:
    transform 0.2s,
    border-color 0.2s,
    box-shadow 0.2s;
}

/* Barre dorée à gauche */
.seance::before {
  content: "";

  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;

  width: 4px;

  background: var(--gold);
}

/* Effet au survol */
.seance:hover {
  transform: translateY(-2px);

  border-color: var(--gold);

  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
}

/* Nom de l'exercice */
.seance p {
  margin: 0;

  color: var(--text);

  font-size: 16px;
  font-weight: 600;
}

/* Responsive téléphone */
@media (max-width: 600px) {
  .programmes-container {
    padding: 20px 12px 80px;
  }

  .programme {
    padding: 16px;
  }

  .jour {
    padding: 14px;
  }

  .programme > h1 {
    font-size: 30px;
  }

  .jour > h2 {
    font-size: 20px;
  }
}
</style>
