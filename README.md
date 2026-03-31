<!DOCTYPE html>
<html>
<head>
  <title>My First App</title>
  <style>
    body {
      font-family: Arial;
      text-align: center;
      background-color: #0f172a;
      color: white;
    }

    .box {
      margin-top: 100px;
    }

    button {
      padding: 10px 20px;
      background-color: #22c55e;
      border: none;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }
  </style>
</head>

<body>

  <div class="box">
    <h1>Welcome</h1>
    <h2>Balance: $1000</h2>
    <input type="number" id="betAmount" placeholder="Enter your bet" style="padding:8px; width:150px; margin-bottom:10px;">
    <button onclick="placeBet()">Place Bet</button>
    <p id="result"></p>
  </div>

  <script>
let balance = 1000;

function placeBet() {
  // Get bet amount from user
  let betInput = document.getElementById("betAmount").value;
  let bet = parseInt(betInput);

  // Check if bet is valid
  if (isNaN(bet) || bet <= 0) {
    alert("Enter a valid bet amount!");
    return;
  }

  if (bet > balance) {
    alert("You don't have enough balance!");
    return;
  }

  let resultText = document.getElementById("result");

  // subtract bet
  balance -= bet;

  // 50% chance to win double
  if (Math.random() > 0.5) {
    balance += bet * 2;
    resultText.innerText = "You won!";
  } else {
    resultText.innerText = "You lost!";
  }

  // update balance on screen
  document.querySelector("h2").innerText = "Balance: $" + balance;

  // clear input for next bet
  document.getElementById("betAmount").value = "";
}
  </script>

</body>
</html>
