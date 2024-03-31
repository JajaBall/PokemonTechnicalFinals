# PokemonTechnicalFinals

// HTML// 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pokemon Battle</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="game">
    <div class="opponent">
      <img class="pokemon" src="charizard.png" />
      <div class="stats">
        <div class="pokeballs">
          <div class="pokeball"></div>
          <div class="pokeball"></div>
          <div class="pokeball"></div>
        </div>
        <div class="hp-count">100</div>
        <span class="name">Charizard</span>
        <span class="level">86</span>
      </div>
    </div>
    <div class="player">
      <img class="pokemon" src="blastoise.png" />
      <div class="stats">
        <div class="pokeballs">
          <div class="pokeball"></div>
          <div class="pokeball"></div>
          <div class="pokeball"></div>
        </div>
        <div class="hp-count">100</div>
        <span class="name">Blastoise</span>
        <span class="level">86</span>
      </div>
    </div>
    <div class="water"></div>
  </div>
  <div class="menu">
    <div class="message">
      What should Blastoise do?
    </div>
    <div class="actions">
      <button class="btn" onclick="attack('Water Cannon')">Water Cannon</button>
      <button class="btn" onclick="attack('Water Pulse')">Water Pulse</button>
      <button class="btn" onclick="attack('Surf')">Surf</button>
      <button class="btn" onclick="attack('Bite')">Bite</button>
    </div>
  </div>

  <script src="script.js"></script>
</body>
</html>


//CSS//

.game {
  height: 480px;
  width: 800px;
  background-image: url('pokemon-bg.png');
  background-size: 100% 100%;
  background-repeat: no-repeat;
  position: relative;
}

.menu {
  background-color: #333;
  height: 120px;
  width: 800px;
  color: white;
}

.pokemon {
  position: absolute;
  bottom: 10px;
  width: 160px;
  transition: transform 0.2s ease-in-out;
}

.pokemon.shake {
  animation: shake 0.3s ease-in-out;
}

.water {
  position: absolute;
  width: 20px;
  height: 20px;
  background-color: blue;
  border-radius: 50%;
  animation: waterMove 1s linear;
}

@keyframes shake {
  0% { transform: translateX(0); }
  25% { transform: translateX(-5px); }
  50% { transform: translateX(5px); }
  75% { transform: translateX(-5px); }
  100% { transform: translateX(0); }
}

@keyframes waterMove {
  0% { transform: translate(0, 0); opacity: 1; }
  100% { transform: translate(200px, -200px); opacity: 0; }
}

.player .pokemon {
  left: 100px;
}

.opponent .pokemon {
  right: 140px;
  bottom: 0;
  width: 100px;
}

.stats {
  background: #111;
  border: 2px solid black;
  border-radius: 8px;
  color: white;
  padding: 12px;
  position: absolute;
  top: 96px;
  left: 40px;
  width: 320px;
}

.pokeballs {
  display: inline-block;
}

.stats .pokeball {
  width: 25px;
  height: 25px;
  border-radius: 50%;
  background-color: red;
  float: left;
  margin: 5px;
}

.hp-count {
  float: right;
}

.actions {
  padding: 12px;
  display: flex;
  justify-content: center;
}

.btn {
  border-color: blue;
  border-style: solid;
  border-width: 1px;
  padding: 8px;
  margin: 0 5px;
  color: white;
  background-color: orange;
  font-family: Times New Roman;
  cursor: pointer;
}

.btn:focus {
  outline: none;
}


//JavaScript//

function attack(attackName) {
  var opponentPokemon = document.querySelector('.opponent .pokemon');
  opponentPokemon.classList.add('shake');
  setTimeout(function() {
    opponentPokemon.classList.remove('shake');
  }, 300);

  var water = document.querySelector('.water');
  water.style.left = '200px'; // Position the water at Blastoise's position
  water.style.bottom = '100px'; // Adjust the position as necessary
  water.style.opacity = '1'; // Make the water visible

  setTimeout(function() {
    water.style.opacity = '0'; // Hide the water after the animation
  }, 1000);

  // Add logic for the attack here
}
