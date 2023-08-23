<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Advanced Calculator</title>
<style>
  body {
    font-family: Arial, sans-serif;
  }
  #calculator {
    width: 300px;
    margin: 50px auto;
    border: 1px solid #ccc;
    padding: 10px;
    border-radius: 5px;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  }
  input[type="text"] {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 3px;
  }
  button {
    width: 48%;
    padding: 10px;
    margin: 5px;
    border: none;
    border-radius: 3px;
    cursor: pointer;
  }
</style>
</head>
<body>
<div id="calculator">
  <input type="text" id="result" readonly>
  <button onclick="clearResult()">C</button>
  <button onclick="appendToResult('7')">7</button>
  <button onclick="appendToResult('8')">8</button>
  <button onclick="appendToResult('9')">9</button>
  <button onclick="appendToResult('+')">+</button>
  <button onclick="appendToResult('4')">4</button>
  <button onclick="appendToResult('5')">5</button>
  <button onclick="appendToResult('6')">6</button>
  <button onclick="appendToResult('-')">-</button>
  <button onclick="appendToResult('1')">1</button>
  <button onclick="appendToResult('2')">2</button>
  <button onclick="appendToResult('3')">3</button>
  <button onclick="appendToResult('*')">*</button>
  <button onclick="appendToResult('0')">0</button>
  <button onclick="calculateResult()">=</button>
  <button onclick="appendToResult('/')">/</button>
  <button onclick="calculateSqrt()">√</button>
  <button onclick="calculatePower()">^</button>
</div>
<script>
  function clearResult() {
    document.getElementById("result").value = "";
  }

  function appendToResult(value) {
    document.getElementById("result").value += value;
  }

  function calculateResult() {
    let result = eval(document.getElementById("result").value);
    document.getElementById("result").value = result;
  }

  function calculateSqrt() {
    let currentValue = parseFloat(document.getElementById("result").value);
    if (currentValue >= 0) {
      let result = Math.sqrt(currentValue);
      document.getElementById("result").value = result;
    } else {
      document.getElementById("result").value = "Error";
    }
  }

  function calculatePower() {
    let currentValue = parseFloat(document.getElementById("result").value);
    let exponent = parseFloat(prompt("Enter exponent:"));
    if (!isNaN(exponent)) {
      let result = Math.pow(currentValue, exponent);
      document.getElementById("result").value = result;
    } else {
      document.getElementById("result").value = "Error";
    }
  }
</script>
</body>
