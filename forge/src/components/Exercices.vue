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

</script>
<template>
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
</template>
