<script setup>
import { ref } from 'vue';

</script>
<template>
<div class="days" id="days">

  <button class="day-tab active">
    <div class="dnum">JOUR 1</div>
    <div class="dname">Séance A</div>
    <div class="dmeta">5 exos · 0%</div>
  </button>

  <button class="day-tab">
    <div class="dnum">JOUR 2</div>
    <div class="dname">Séance B</div>
    <div class="dmeta">5 exos · 0%</div>
  </button>

  <button class="day-tab">
    <div class="dnum">JOUR 3</div>
    <div class="dname">Séance C</div>
    <div class="dmeta">5 exos · 0%</div>
  </button>

</div>

</template>

<style scoped>
:root {
  --surface: #16191f;
  --line: #2c313b;
  --text: #f5f3ee;
  --muted: #8b909b;
  --muted-2: #5a606c;

  --gold: #f2c14e;
  --rest: #38e1d0;
  --rest-dim: #1c5a54;

  --radius-sm: 10px;
}
/* ---------- Boutons des jours ---------- */

.days {
  display: flex;
  gap: 8px;
  overflow-x: auto;
  padding-bottom: 8px;
  margin-bottom: 14px;
  scrollbar-width: none;
}

/* Cache la barre de défilement */
.days::-webkit-scrollbar {
  display: none;
}

.day-tab {
  flex: 0 0 auto;
  min-width: 104px;
  padding: 10px 14px;

  background: var(--surface);
  border: 1px solid var(--line);
  border-radius: var(--radius-sm);

  color: var(--text);
  font: inherit;
  text-align: left;

  cursor: pointer;
  transition: 0.18s;
}

.day-tab .dnum {
  font-family: "Bebas Neue", sans-serif;
  font-size: 13px;
  letter-spacing: 1.5px;
  color: var(--muted-2);
}

.day-tab .dname {
  font-size: 14px;
  font-weight: 600;
  white-space: nowrap;
}

.day-tab .dmeta {
  margin-top: 3px;
  font-size: 11px;
  color: var(--muted);
}

/* Jour actuellement sélectionné */
.day-tab.active {
  border-color: var(--gold);
  background: linear-gradient(
    180deg,
    rgba(242, 193, 78, 0.12),
    transparent
  );
}

.day-tab.active .dnum {
  color: var(--gold);
}

/* Séance terminée */
.day-tab.done-day {
  border-color: var(--rest-dim);
}

.day-tab.done-day .dnum {
  color: var(--rest);
}

</style>
