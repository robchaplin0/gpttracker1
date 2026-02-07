<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Daily Habits</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Crimson+Pro:wght@300;400;600&family=DM+Sans:wght@400;500;700&display=swap" rel="stylesheet">

  <style>
    :root {
      --bg: #fafaf9;
      --surface: #ffffff;
      --text: #1a1a1a;
      --muted: #737373;
      --border: #e5e5e5;
      --accent: #059669;
      --accent-light: #d1fae5;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      font-family: 'DM Sans', sans-serif;
      background: var(--bg);
      color: var(--text);
      min-height: 100vh;
    }

    .container {
      max-width: 680px;
      margin: 0 auto;
      background: var(--surface);
      min-height: 100vh;
    }

    header {
      padding: 48px 32px;
      border-bottom: 1px solid var(--border);
      text-align: center;
    }

    header h1 {
      font-family: 'Crimson Pro', serif;
      font-size: 40px;
      font-weight: 300;
    }

    header p {
      color: var(--muted);
      margin-top: 6px;
    }

    .client {
      display: inline-block;
      margin-top: 20px;
      padding: 6px 14px;
      background: var(--accent-light);
      color: var(--accent);
      border-radius: 6px;
      font-size: 14px;
    }

    main { padding: 32px; }

    .date-nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 32px;
    }

    .date-nav button {
      background: none;
      border: 1px solid var(--border);
      padding: 8px 16px;
      border-radius: 8px;
      cursor: pointer;
    }

    .date-nav button:disabled {
      opacity: 0.3;
      cursor: not-allowed;
    }

    .date {
      font-weight: 500;
    }

    h2 {
      font-family: 'Crimson Pro', serif;
      font-weight: 400;
      margin-bottom: 16px;
      text-align: center;
    }

    .habit {
      display: flex;
      align-items: center;
      padding: 16px 0;
      border-bottom: 1px solid var(--border);
      cursor: pointer;
    }

    .habit input {
      margin-right: 16px;
    }

    .habit.done span {
      opacity: 0.5;
      text-decoration: line-through;
    }

    .empty {
      text-align: center;
      padding: 64px 16px;
      color: var(--muted);
    }

    .add {
      margin-top: 32px;
      display: flex;
      gap: 12px;
    }

    .add input {
      flex: 1;
      padding: 12px;
      border-radius: 8px;
      border: 1px solid var(--border);
    }

    .add button {
      padding: 12px 20px;
      border-radius: 8px;
      border: none;
      background: var(--text);
      color: white;
      cursor: pointer;
    }

    .stats {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
      margin-top: 40px;
      border-top: 1px solid var(--border);
      padding-top: 32px;
      text-align: center;
    }

    .stat strong {
      font-family: 'Crimson Pro', serif;
      font-size: 32px;
      display: block;
    }

    .stat span {
      font-size: 12px;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: 0.05em;
    }
  </style>
</head>

<body>
<div class="container">
  <header>
    <h1>Daily Habits</h1>
    <p>Build habits that compound</p>
    <div class="client" id="clientName"></div>
  </header>

  <main id="app"></main>
</div>

<script>
/* =======================
   CONFIG
======================= */

const SCHEMA_VERSION = 2;

/* =======================
   UTILITIES
======================= */

function iso(date) {
  return date.toISOString().split("T")[0];
}

function today() {
  const d = new Date();
  d.setHours(0,0,0,0);
  return d;
}

function addDays(date, n) {
  const d = new Date(date);
  d.setDate(d.getDate() + n);
  return d;
}

/* =======================
   STATE
======================= */

function storageKey(clientId) {
  return `habit_tracker_v2_${clientId}`;
}

function initialState(clientId) {
  return {
    meta: {
      schemaVersion: SCHEMA_VERSION,
      clientId,
      createdAt: new Date().toISOString()
    },
    habits: {},
    logs: {}
  };
}

function loadState(clientId) {
  const raw = localStorage.getItem(storageKey(clientId));
  if (!raw) return initialState(clientId);
  return JSON.parse(raw);
}

function saveState(clientId, state) {
  localStorage.setItem(storageKey(clientId), JSON.stringify(state));
}

/* =======================
   APP
======================= */

let clientId = "";
let state = null;
let viewingDate = today();

function init() {
  const params = new URLSearchParams(location.search);
  clientId = params.get("client");

  if (!clientId) {
    document.getElementById("app").innerHTML = `
      <div class="empty">
        <h2>Setup Required</h2>
        <p>Open this tracker with your personal link.</p>
        <p><code>?client=your-name</code></p>
      </div>`;
    return;
  }

  document.getElementById("clientName").textContent =
    clientId.split("-").map(w => w[0].toUpperCase() + w.slice(1)).join(" ");

  state = loadState(clientId);
  render();
}

/* =======================
   HABITS
======================= */

function addHabit(name) {
  const id = crypto.randomUUID();
  state.habits[id] = {
    id,
    name,
    createdAt: iso(today()),
    active: true
  };
  saveState(clientId, state);
  render();
}

function toggleHabit(habitId) {
  const day = iso(viewingDate);
  state.logs[day] ??= {};

  const current = state.logs[day][habitId];
  state.logs[day][habitId] = current === "done" ? "missed" : "done";

  saveState(clientId, state);
  render();
}

/* =======================
   STATS
======================= */

function statsForDay(date) {
  const log = state.logs[iso(date)] || {};
  const habits = Object.values(state.habits).filter(h => h.active && h.createdAt <= iso(date));
  const done = habits.filter(h => log[h.id] === "done").length;
  return {
    done,
    total: habits.length,
    percent: habits.length ? Math.round(done / habits.length * 100) : 0
  };
}

function streak() {
  let count = 0;
  let d = addDays(today(), -1);

  while (true) {
    const s = statsForDay(d);
    if (s.total > 0 && s.done === s.total) {
      count++;
      d = addDays(d, -1);
    } else break;
  }
  return count;
}

/* =======================
   RENDER
======================= */

function render() {
  const app = document.getElementById("app");
  const s = statsForDay(viewingDate);

  app.innerHTML = `
    <div class="date-nav">
      <button onclick="changeDate(-1)">← Prev</button>
      <div class="date">${viewingDate.toDateString()}</div>
      <button onclick="changeDate(1)" ${viewingDate >= today() ? "disabled" : ""}>Next →</button>
    </div>

    <h2>Today’s Commitments</h2>

    ${renderHabits()}

    <div class="add">
      <input id="newHabit" placeholder="Add a new habit"/>
      <button onclick="handleAdd()">Add</button>
    </div>

    <div class="stats">
      <div class="stat"><strong>${s.done}/${s.total}</strong><span>Today</span></div>
      <div class="stat"><strong>${s.percent}%</strong><span>Complete</span></div>
      <div class="stat"><strong>${streak()}</strong><span>Streak</span></div>
    </div>
  `;
}

function renderHabits() {
  const habits = Object.values(state.habits).filter(h => h.active);
  const log = state.logs[iso(viewingDate)] || {};

  if (!habits.length) {
    return `<div class="empty">Add your first habit below</div>`;
  }

  return habits.map(h => `
    <div class="habit ${log[h.id] === "done" ? "done" : ""}"
         onclick="toggleHabit('${h.id}')">
      <input type="checkbox" ${log[h.id] === "done" ? "checked" : ""}/>
      <span>${h.name}</span>
    </div>
  `).join("");
}

function handleAdd() {
  const input = document.getElementById("newHabit");
  if (!input.value.trim()) return;
  addHabit(input.value.trim());
  input.value = "";
}

function changeDate(n) {
  viewingDate = addDays(viewingDate, n);
  render();
}

init();
</script>
</body>
</html>
