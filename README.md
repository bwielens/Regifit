<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Regifit - Register Your Fitness Tour</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Roboto', sans-serif;
      background-color: #000;
      color: #fff;
    }

    header {
      background-color: #111;
      padding: 2rem;
      text-align: center;
    }

    .logo {
      font-size: 3rem;
      color: #e60000;
      font-weight: 700;
    }

    .slogan {
      font-size: 1.2rem;
      color: #ccc;
      margin-top: 0.5rem;
    }

    .hero {
      text-align: center;
      padding: 4rem 2rem;
    }

    .hero h1 {
      font-size: 2.5rem;
      color: #e60000;
    }

    .hero p {
      font-size: 1.2rem;
      color: #ddd;
      max-width: 600px;
      margin: 1rem auto;
    }

    .cta-button {
      background-color: #e60000;
      color: #fff;
      padding: 1rem 2rem;
      font-size: 1rem;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 2rem;
    }

    .form-section {
      padding: 2rem;
      max-width: 600px;
      margin: 0 auto;
    }

    .form-section h2 {
      color: #e60000;
      margin-bottom: 1rem;
    }

    .form-section input,
    .form-section button {
      width: 100%;
      padding: 1rem;
      margin-bottom: 1rem;
      border: none;
      border-radius: 5px;
      font-size: 1rem;
    }

    .form-section input {
      background-color: #222;
      color: #fff;
    }

    .form-section button {
      background-color: #e60000;
      color: #fff;
      cursor: pointer;
    }

    .log-section {
      padding: 2rem;
      max-width: 600px;
      margin: 0 auto;
    }

    .log-section h3 {
      margin-bottom: 1rem;
      color: #e60000;
    }

    .log-entry {
      background-color: #111;
      padding: 1rem;
      border-radius: 5px;
      margin-bottom: 1rem;
    }

    footer {
      text-align: center;
      padding: 2rem;
      background-color: #111;
      font-size: 0.9rem;
      color: #555;
    }
  </style>
</head>
<body>
  <header>
    <div class="logo">REGIFIT</div>
    <div class="slogan">REGISTER YOUR FITNESS TOUR</div>
  </header>

  <section class="hero">
    <h1>Jouw persoonlijke fitness tracker</h1>
    <p>Met Regifit houd je eenvoudig al je trainingsresultaten bij en deel je ze met je personal trainer. Krachtig, overzichtelijk en 100% gericht op jouw doelen.</p>
  </section>

  <section class="form-section">
    <h2>Nieuwe trainingssessie</h2>
    <input type="text" id="exercise" placeholder="Oefening (bijv. Squat)" />
    <input type="number" id="sets" placeholder="Aantal sets" />
    <input type="number" id="reps" placeholder="Aantal herhalingen" />
    <input type="number" id="weight" placeholder="Gewicht (kg)" />
    <button onclick="saveWorkout()">Opslaan</button>
  </section>

  <section class="log-section">
    <h3>Training log</h3>
    <div id="log"></div>
  </section>

  <footer>
    &copy; 2025 Regifit. Alle rechten voorbehouden.
  </footer>

  <script>
    function saveWorkout() {
      const exercise = document.getElementById('exercise').value;
      const sets = document.getElementById('sets').value;
      const reps = document.getElementById('reps').value;
      const weight = document.getElementById('weight').value;
      const entry = `${exercise} - ${sets} sets van ${reps} reps (${weight} kg)`;
      const logContainer = document.getElementById('log');

      const div = document.createElement('div');
      div.className = 'log-entry';
      div.textContent = entry;
      logContainer.prepend(div);

      // Optioneel: opslaan in localStorage
      const log = JSON.parse(localStorage.getItem('regifit-log') || '[]');
      log.unshift(entry);
      localStorage.setItem('regifit-log', JSON.stringify(log));

      // Velden leegmaken
      document.getElementById('exercise').value = '';
      document.getElementById('sets').value = '';
      document.getElementById('reps').value = '';
      document.getElementById('weight').value = '';
    }

    // Log laden bij opstarten
    window.onload = function () {
      const log = JSON.parse(localStorage.getItem('regifit-log') || '[]');
      const logContainer = document.getElementById('log');
      log.forEach(entry => {
        const div = document.createElement('div');
        div.className = 'log-entry';
        div.textContent = entry;
        logContainer.appendChild(div);
      });
    }
  </script>
</body>
</html>
