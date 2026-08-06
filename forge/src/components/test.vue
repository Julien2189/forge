<script setup>
import { reactive } from 'vue';

    const PROGRAMS =reactive( [
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
])
function ajouterSerie(exercice) {
    exercice.s ++;
    console.log('+1');
}
function ajouterRepetition(exercice){
  exercice.r ++;
}
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
        <button @click="ajouterSerie(exercice)">Ajouter series</button>
        <p>series : {{ exercice.s }}</p>
        <button @click="ajouterRepetition(exercice)">Ajouter repetitions</button>
        <p>Repetitions: {{ exercice.r }}</p>
        </div>
        </div>

    </main>

</template>

<style scoped>
main {
  --ink: #0e1014;
  --surface: #16191f;
  --elev: #1e222b;
  --elev-2: #272c36;
  --line: #2c313b;
  --text: #f5f3ee;
  --muted: #8b909b;
  --gold: #f2c14e;
  --rest: #38e1d0;

  min-height: 100vh;
  padding: 40px 20px;

  background:
    radial-gradient(
      1100px 700px at 85% -10%,
      rgba(242, 193, 78, 0.07),
      transparent 55%
    ),
    radial-gradient(
      900px 600px at -10% 110%,
      rgba(56, 225, 208, 0.06),
      transparent 55%
    ),
    var(--ink);

  color: var(--text);
  font-family: "Space Grotesk", Arial, sans-serif;
}

h1 {
  margin-bottom: 35px;
  color: var(--gold);
  text-align: center;
  font-size: 42px;
  letter-spacing: 1px;
}

.seance {
  max-width: 800px;
  margin: 0 auto 30px;
  padding: 25px;

  background-color: var(--surface);
  border: 1px solid var(--line);
  border-radius: 16px;

  box-shadow: 0 18px 50px rgba(0, 0, 0, 0.45);
}

.seance h2 {
  margin-top: 0;
  margin-bottom: 20px;
  color: var(--gold);
  text-align: center;
  font-size: 28px;
}

.liste-exercices {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 20px;
}

.exercice {
  width: 250px;
  padding: 20px;

  background-color: var(--elev);
  border: 1px solid var(--line);
  border-radius: 12px;

  text-align: center;

  transition:
    transform 0.2s,
    border-color 0.2s,
    box-shadow 0.2s;
}

.exercice:hover {
  transform: translateY(-5px);
  border-color: var(--gold);
  box-shadow: 0 10px 25px rgba(242, 193, 78, 0.12);
}

.exercice h3 {
  margin-top: 0;
  margin-bottom: 15px;
  color: var(--rest);
  font-size: 20px;
}

.exercice p {
  margin: 10px 0;
  color: var(--muted);
}

.exercice strong {
  color: var(--text);
}

@media (max-width: 600px) {
  main {
    padding: 25px 10px;
  }

  h1 {
    font-size: 34px;
  }

  .seance {
    padding: 15px;
  }

  .exercice {
    width: 100%;
  }
}
</style>