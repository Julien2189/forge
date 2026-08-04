<template>

<!-- Chrono dock -->
<div class="chrono" id="chrono">
  <div class="chrono-inner">
    <div class="ring-wrap">
      <svg width="74" height="74" viewBox="0 0 74 74">
        <circle class="ring-bg" cx="37" cy="37" r="32"></circle>
        <circle class="ring-fg" id="ringFg" cx="37" cy="37" r="32"></circle>
      </svg>
      <div class="ring-num" id="ringNum">0%</div>
    </div>
    <div class="chrono-mid">
      <div class="chrono-state" id="chronoState">Chrono prêt</div>
      <div class="chrono-time" id="chronoTime">00:00</div>
      <div class="chrono-from" id="chronoFrom">Valide une série ou touche “Repos” pour lancer la récup</div>
    </div>
    <div class="chrono-ctrl">
      <button class="cc" id="ccMinus" title="-15s">−15</button>
      <button class="cc play" id="ccPlay" title="Démarrer / Pause">▶</button>
      <button class="cc" id="ccPlus" title="+15s">+15</button>
      <button class="cc" id="ccReset" title="Réinitialiser">↺</button>
    </div>
  </div>
</div>

</template>