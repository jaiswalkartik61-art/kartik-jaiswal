html
<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>नंबर गेसिंग गेम</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: #f0f2f5; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; }
        .game-container { background: white; padding: 30px; border-radius: 15px; box-shadow: 0 10px 25px rgba(0,0,0,0.1); text-align: center; max-width: 400px; width: 90%; }
        h1 { color: #1a73e8; }
        input { width: 80%; padding: 12px; margin: 20px 0; border: 2px solid #ddd; border-radius: 8px; font-size: 18px; outline: none; }
        button { background: #1a73e8; color: white; border: none; padding: 12px 25px; border-radius: 8px; cursor: pointer; font-size: 16px; transition: 0.3s; }
        button:hover { background: #1557b0; }
        #message { margin-top: 20px; font-weight: bold; color: #333; }
    </style>
</head>
<body>

<div class="game-container">
    <h1>संख्या पहचानो!</h1>
    <p>1 से 100 के बीच की संख्या गेस करें</p>
    <input type="number" id="guessInput" placeholder="नंबर डालें..." min="1" max="100">
    <br>
    <button onclick="checkGuess()">चेक करें</button>
    <p id="message"></p>
    <button onclick="resetGame()" style="background:#34a853; display:none;" id="resetBtn">फिर से खेलें</button>
</div>

<script>
    let randomNumber = Math.floor(Math.random() * 100) + 1;
    let attempts = 0;

    function checkGuess() {
        const userGuess = document.getElementById('guessInput').value;
        const message = document.getElementById('message');
        const resetBtn = document.getElementById('resetBtn');
        attempts++;

        if (userGuess == randomNumber) {
            message.innerHTML = `बधाई हो! 🎉 आपने ${attempts} बार में सही नंबर चुना।`;
            message.style.color = "green";
            resetBtn.style.display = "inline-block";
        } else if (userGuess > randomNumber) {
            message.innerHTML = "थोड़ा कम! (Too High) 📉";
            message.style.color = "red";
        } else if (userGuess < randomNumber) {
            message.innerHTML = "थोड़ा ज्यादा! (Too Low) 📈";
            message.style.color = "red";
        }
    }

    function resetGame() {
        randomNumber = Math.floor(Math.random() * 100) + 1;
        attempts = 0;
        document.getElementById('guessInput').value = '';
        document.getElementById('message').innerHTML = '';
        document.getElementById('resetBtn').style.display = "none";
    }
</script>

</body>
</html>
