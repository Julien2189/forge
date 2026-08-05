<script setup>
    const PROGRAMS = [
  {
    id: "debutant",
    name: "Programme débutant",

    days: [
      {
        name: "Séance A",

        ex: [
          {
            n: "Squat",
            m: "Jambes",
            s: 3,
            r: 10
          },
          {
            n: "Pompes",
            m: "Pectoraux",
            s: 3,
            r: 8
          }
        ]
      },

      {
        name: "Séance B",

        ex: [
          {
            n: "Fentes",
            m: "Jambes",
            s: 3,
            r: 12
          },
          {
            n: "Gainage",
            m: "Abdominaux",
            s: 3,
            r: "30 secondes"
          }
        ]
      }
    ]
  }
]
</script>
<template>
    <main>
        <h1>{{ PROGRAMS[0].name  }}</h1>
        <div
        v-for="seance in PROGRAMS[0].days":key="name" class="seance">
        <h3>{{ seance.name }}</h3>
        <div 
        v-for="exercice in seance.ex":key="exercice.n" class="exercice">
        <h3>{{ exercice.n }}</h3>
        <p>muscle : {{ exercice.m }}</p>
        <p>series : {{ exercice.s }}</p>
        <p>Repetitions: {{ exercice.r }}</p>
        </div>
        </div>

    </main>

</template>
<style scoped>
    .seance {
        display: flex;
        justify-content: center;
        background-color: wheat;
        align-items: center;
        text-align: center;
        border: 1 px solid red;
    }
</style>