const express = require('express');
const app = express();
const port = process.env.PORT || 3000;

app.use(express.json());

// Variable globale pour stocker les dernières données reçues
let latestData = null;

// Route POST pour recevoir les données de l'ESP32
app.post('/data', (req, res) => {
  latestData = req.body;
  console.log('Données reçues :', latestData);
  res.json({ status: 'OK', message: 'Données reçues' });
});

// Route GET pour afficher les données (page HTML simple)
app.get('/', (req, res) => {
  res.send(`
    <html>
      <head>
        <title>Données ESP32</title>
        <meta http-equiv="refresh" content="2" />
      </head>
      <body>
        <h1>Données ESP32 (mise à jour toutes les 2 secondes)</h1>
        <pre>${JSON.stringify(latestData, null, 2) || 'Aucune donnée reçue'}</pre>
      </body>
    </html>
  `);
});

app.listen(port, () => {
  console.log(`Serveur démarré sur http://localhost:${port}`);
});
