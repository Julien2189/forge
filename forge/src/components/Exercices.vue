<script setup>
     import { ref } from 'vue' 

       const monthTitle = document.querySelector("#monthTitle");
    const calendarDays = document.querySelector("#calendarDays");
    const selectedDate = document.querySelector("#selectedDate");

    const previousButton = document.querySelector("#previousMonth");
    const nextButton = document.querySelector("#nextMonth");

    const today = new Date();

    let displayedDate = new Date(
      today.getFullYear(),
      today.getMonth(),
      1
    );

    function displayCalendar() {
      calendarDays.innerHTML = "";

      const year = displayedDate.getFullYear();
      const month = displayedDate.getMonth();

      const monthName = displayedDate.toLocaleDateString("fr-FR", {
        month: "long",
        year: "numeric"
      });

      monthTitle.textContent = monthName;

      /*
        Dernier jour du mois :
        new Date(année, mois suivant, 0)
      */
      const numberOfDays = new Date(year, month + 1, 0).getDate();

      /*
        Jour de la semaine du premier jour.

        JavaScript :
        dimanche = 0
        lundi = 1

        On transforme pour obtenir :
        lundi = 0
        dimanche = 6
      */
      const firstDay = new Date(year, month, 1).getDay();

      const emptyCells = firstDay === 0
        ? 6
        : firstDay - 1;

      // Cases vides avant le premier jour
      for (let i = 0; i < emptyCells; i++) {
        const emptyDay = document.createElement("div");
        emptyDay.classList.add("day", "empty");

        calendarDays.appendChild(emptyDay);
      }

      // Création des jours du mois
      for (let dayNumber = 1; dayNumber <= numberOfDays; dayNumber++) {
        const dayElement = document.createElement("button");

        dayElement.classList.add("day");
        dayElement.textContent = dayNumber;

        const isToday =
          dayNumber === today.getDate() &&
          month === today.getMonth() &&
          year === today.getFullYear();

        if (isToday) {
          dayElement.classList.add("today");
        }

        dayElement.addEventListener("click", function () {
          document.querySelectorAll(".day").forEach(function (day) {
            day.classList.remove("selected");
          });

          dayElement.classList.add("selected");

          const clickedDate = new Date(year, month, dayNumber);

          selectedDate.textContent =
            "Date sélectionnée : " +
            clickedDate.toLocaleDateString("fr-FR");
        });

        calendarDays.appendChild(dayElement);
      }
    }

    previousButton.addEventListener("click", function () {
      displayedDate.setMonth(displayedDate.getMonth() - 1);
      displayCalendar();
    });

    nextButton.addEventListener("click", function () {
      displayedDate.setMonth(displayedDate.getMonth() + 1);
      displayCalendar();
    });

    displayCalendar();

</script>
<template>
 
  <div class="calendar">

    <div class="calendar-header">
      <button id="previousMonth">‹</button>

      <h2 id="monthTitle"></h2>

      <button id="nextMonth">›</button>
    </div>

    <div class="weekdays">
      <div>Lun</div>
      <div>Mar</div>
      <div>Mer</div>
      <div>Jeu</div>
      <div>Ven</div>
      <div>Sam</div>
      <div>Dim</div>
    </div>

    <div class="days" id="calendarDays"></div>

    <p class="selected-date" id="selectedDate">
      Clique sur une date
    </p>

  </div>
  <main class="programmes-container">
    
  </main>
  

</template>

<style scoped>
:root {
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

 * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;

      background: #0e1014;
      color: #f5f3ee;
      font-family: Arial, sans-serif;
    }

    .calendar {
      width: 380px;
      padding: 20px;

      background: #16191f;
      border: 1px solid #2c313b;
      border-radius: 16px;
    }

    .calendar-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

    .calendar-header h2 {
      margin: 0;
      font-size: 22px;
      text-transform: capitalize;
    }

    .calendar-header button {
      width: 40px;
      height: 40px;

      background: #1e222b;
      color: #f2c14e;
      border: 1px solid #2c313b;
      border-radius: 8px;

      font-size: 20px;
      cursor: pointer;
    }

    .calendar-header button:hover {
      border-color: #f2c14e;
    }

    .weekdays,
    .days {
      display: grid;
      grid-template-columns: repeat(7, 1fr);
      gap: 6px;
    }

    .weekdays {
      margin-bottom: 8px;
    }

    .weekdays div {
      text-align: center;
      color: #8b909b;
      font-size: 13px;
      font-weight: bold;
    }

    .day {
      aspect-ratio: 1;
      display: flex;
      justify-content: center;
      align-items: center;

      background: #1e222b;
      border: 1px solid transparent;
      border-radius: 8px;

      cursor: pointer;
    }

    .day:hover {
      border-color: #f2c14e;
    }

    .empty {
      background: transparent;
      cursor: default;
    }

    .today {
      background: #f2c14e;
      color: #16191f;
      font-weight: bold;
    }

    .selected {
      border-color: #38e1d0;
      color: #38e1d0;
    }

    .selected.today {
      color: #16191f;
      border-color: #38e1d0;
    }

    .selected-date {
      margin-top: 16px;
      color: #8b909b;
      text-align: center;
      font-size: 14px;
    }
</style>
