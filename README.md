index . html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculatrice</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="calculator">
    <div class="display" id="display">0</div>
    <div class="buttons">
      <button onclick="clearDisplay()">C</button>
      <button onclick="deleteLast()">DEL</button>
      <button onclick="appendOperator('/')">/</button>
      <button onclick="appendOperator('*')">*</button>

      <button onclick="appendNumber(7)">7</button>
      <button onclick="appendNumber(8)">8</button>
      <button onclick="appendNumber(9)">9</button>
      <button onclick="appendOperator('-')">-</button>

      <button onclick="appendNumber(4)">4</button>
      <button onclick="appendNumber(5)">5</button>
      <button onclick="appendNumber(6)">6</button>
      <button onclick="appendOperator('+')">+</button>

      <button onclick="appendNumber(1)">1</button>
      <button onclick="appendNumber(2)">2</button>
      <button onclick="appendNumber(3)">3</button>
      <button onclick="calculate()">=</button>

      <button onclick="appendNumber(0)" class="zero">0</button>
      <button onclick="appendNumber('.')">.</button>
    </div>
  </div>
  <script src="script.js"></script>
</body>
</html>

//style.css
body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background-color: blue;
    margin: 0;
  }
  
  .calculator {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
    width: 300px;
  }
  
  .display {
    background-color: #222;
    color: #fff;
    font-size: 2rem;
    text-align: right;
    padding: 10px;
    border-radius: 5px;
    margin-bottom: 10px;
  }
  
  .buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
  }
  
  button {
    font-size: 1.2rem;
    padding: 15px;
    border: none;
    border-radius: 5px;
    background-color: #f0f0f0;
    cursor: pointer;
    transition: background-color 0.2s;
  }
  
  button:hover {
    background-color: #ddd;
  }
  
  button:active {
    background-color: #bbb;
  }
  
  .zero {
    grid-column: span 2;
  }
   // script.js
   let display = document.getElementById("display");
let currentInput = "";

function appendNumber(number) {
  if (currentInput === "0" && number !== ".") {
    currentInput = number.toString();
  } else {
    currentInput += number;
  }
  updateDisplay();
}

function appendOperator(operator) {
  if (!/[+\-*/]$/.test(currentInput)) {
    currentInput += operator;
  }
  updateDisplay();
}

function clearDisplay() {
  currentInput = "";
  updateDisplay();
}

function deleteLast() {
  currentInput = currentInput.slice(0, -1);
  updateDisplay();
}

function calculate() {
  try {
    currentInput = eval(currentInput).toString();
  } catch (error) {
    currentInput = "Error";
  }
  updateDisplay();
}

function updateDisplay() {
  display.textContent = currentInput || "0";
}
