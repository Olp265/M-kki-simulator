<!DOCTYPE html>
<html lang="fi">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Mökki-peli</title>
<style>
  body { font-family: Arial, sans-serif; margin: 10px; background: #d3f2d3; }
  #game { max-width: 480px; margin: auto; background: #fff; padding: 15px; border-radius: 8px; }
  button { margin: 5px; padding: 10px; font-size: 1em; }
  #messages { border: 1px solid #aaa; height: 120px; overflow-y: auto; padding: 5px; background: #eef9ee; }
  #stats { margin-bottom: 15px; }
  .neighbor { cursor: pointer; color: blue; text-decoration: underline; }
  #store-items button { display: block; margin: 5px 0; }
</style>
</head>
<body>
<div id="game">
  <h2>Mökki-peli</h2>
  <div id="stats">
    Raha: <span id="money">10</span> €<br/>
    Marjat: <span id="berries">0</span><br/>
    Kalat: <span id="fish">0</span><br/>
    Nuotio valmis: <span id="fire">Ei</span>
  </div>

  <div>
    <button onclick="collectBerries()">Kerää marjoja (+1)</button>
    <button onclick="fish()">Kalasta (+1 kala)</button>
    <button onclick="makeFire()">Tee nuotio (5 marjaa)</button>
    <button onclick="goToStore()">Mene kauppaan</button>
    <button onclick="talkToNeighbor()">Juttele naapuriin</button>
  </div>

  <div id="messages"></div>

  <div id="store" style="display:none;">
    <h3>Kauppa</h3>
    <div id="store-items">
      <button onclick="buyItem('Marjat', 3)">Osta marjat 3 €</button>
      <button onclick="buyItem('Kala', 5)">Osta kala 5 €</button>
      <button onclick="buyItem('Nuotio puut', 10)">Osta nuotion puut 10 €</button>
      <button onclick="leaveStore()">Poistu kaupasta</button>
    </div>
  </div>
</div>

<script>
let money = 10;
let berries = 0;
let fishCount = 0;
let fire = false;

const neighbors = ['Matti', 'Maija', 'Jussi'];

function updateStats() {
  document.getElementById('money').textContent = money;
  document.getElementById('berries').textContent = berries;
  document.getElementById('fish').textContent = fishCount;
  document.getElementById('fire').textContent = fire ? 'Kyllä' : 'Ei';
}

function logMessage(msg) {
  const messages = document.getElementById('messages');
  const p = document.createElement('p');
  p.textContent = msg;
  messages.appendChild(p);
  messages.scrollTop = messages.scrollHeight;
}

function collectBerries() {
  berries++;
  logMessage('Keräsit yhden marjan.');
  updateStats();
}

function fish() {
  fishCount++;
  logMessage('Sait yhden kalan.');
  updateStats();
}

function makeFire() {
  if (berries >= 5) {
    berries -= 5;
    fire = true;
    logMessage('Nuotio on nyt valmis! Hyvä lämpö mökille.');
  } else {
    logMessage('Ei tarpeeksi marjoja nuotion tekemiseen. Tarvitset 5 marjaa.');
  }
  updateStats();
}

function goToStore() {
  document.getElementById('store').style.display = 'block';
  logMessage('Olet kaupassa. Voit ostaa tavaroita.');
}

function leaveStore() {
  document.getElementById('store').style.display = 'none';
  logMessage('Poistit kaupasta.');
}

function buyItem(item, price) {
  if (money >= price) {
    money -= price;
    if (item === 'Marjat') berries++;
    if (item === 'Kala') fishCount++;
    if (item === 'Nuotio puut') fire = true;
    logMessage(`Ostit ${item} hintaan ${price} €.`);
  } else {
    logMessage('Ei tarpeeksi rahaa.');
  }
  updateStats();
}

function talkToNeighbor() {
  const neighbor = neighbors[Math.floor(Math.random() * neighbors.length)];
  const messagesToSay = [
    `Naapuri ${neighbor}: "Hei, mukava nähdä sinua mökillä!"`,
    `Naapuri ${neighbor}: "Onko kalaonni ollut suotuisa tänään?"`,
    `Naapuri ${neighbor}: "Oletko kerännyt marjoja? Ne ovat herkullisia."`,
  ];
  const msg = messagesToSay[Math.floor(Math.random() * messagesToSay.length)];
  logMessage(msg);
}

updateStats();
</script>
</body>
</html>
