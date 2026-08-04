<script setup>

</script>

<template>
    
<div class="wrap">
  <header class="app">
    <div class="brand">
      <span class="logo">FORGE</span>
      <span class="tag">Training</span>
    </div>
    <button class="btn-lib" id="openLib"><span class="dot"></span> Séances</button>
  </header>

  <div class="prog-name" id="progName">—</div>
  <div class="prog-sub" id="progSub">—</div>

  <div class="days" id="days"></div>

  <div class="day-head">
    <h2 id="dayTitle">—</h2>
    <div class="progress">
      <div class="lbl"><span>Progression du jour</span><b id="progPct">0%</b></div>
      <div class="bar"><i id="progFill"></i></div>
    </div>
  </div>

  <div class="ex-list" id="exList"></div>

  <button class="add-ex" id="addEx">＋ Ajouter un exercice</button>

  <div class="day-actions">
    <button class="reset-day" id="resetDay">↺ Réinitialiser le jour</button>
  </div>
</div>
</template>

<style scoped>
</style>
