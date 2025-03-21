<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rafie Hafizi Abenteuer</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            color: #333;
            padding: 20px;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        h1 {
            text-align: center;
        }
        .output {
            margin-bottom: 20px;
        }
        button {
            padding: 10px;
            font-size: 16px;
            cursor: pointer;
            margin-right: 10px;
            border: none;
            background-color: #4CAF50;
            color: white;
            border-radius: 5px;
        }
        button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Rafie Hafizi Abenteuer</h1>
        <div class="output" id="gameOutput"></div>
        <button id="attackButton">Angreifen</button>
        <button id="fleeButton">Fliehen</button>
    </div>

    <script>
        // Charaktere und Gegner
        const player = {
            name: "Rafie Hafizi",
            health: 100,
            attack: 20
        };

        const enemy = {
            name: "Dämonenkrieger",
            health: 50,
            attack: 10
        };

        // Anzeige der Spiel-Output
        const gameOutput = document.getElementById('gameOutput');

        // Funktion, um das Spiel zu starten
        function startGame() {
            gameOutput.innerHTML = `${player.name} betritt die Welt der Abenteuer!<br>Ein böser ${enemy.name} erscheint!<br><br>Was wirst du tun?`;
        }

        // Funktion, um den Angriff auszuführen
        function attack() {
            enemy.health -= player.attack;
            gameOutput.innerHTML += `<br>${player.name} greift ${enemy.name} an!<br>${enemy.name} hat nun ${enemy.health} Leben.`;

            if (enemy.health <= 0) {
                gameOutput.innerHTML += `<br>${enemy.name} wurde besiegt! ${player.name} hat gewonnen!`;
                disableButtons();
            } else {
                player.health -= enemy.attack;
                gameOutput.innerHTML += `<br>${enemy.name} greift ${player.name} an!<br>${player.name} hat nun ${player.health} Leben.`;

                if (player.health <= 0) {
                    gameOutput.innerHTML += `<br>${player.name} wurde besiegt! Spiel beendet.`;
                    disableButtons();
                }
            }
        }

        // Funktion zum Fliehen
        function flee() {
            gameOutput.innerHTML += `<br>${player.name} flieht vor dem Kampf!<br>Spiel beendet.`;
            disableButtons();
        }

        // Buttons deaktivieren, wenn das Spiel zu Ende ist
        function disableButtons() {
            document.getElementById('attackButton').disabled = true;
            document.getElementById('fleeButton').disabled = true;
        }

        // Ereignisse an die Buttons anhängen
        document.getElementById('attackButton').addEventListener('click', attack);
        document.getElementById('fleeButton').addEventListener('click', flee);

        // Spiel starten
        startGame();
    </script>

</body>
</html>
