---
layout: default
title: Student Blog
---

## Raunak's Page

Go to my [Github account](https://github.com/raunak2007) !!

I currently live in San Diego and was born in Bangalore, India. I started coding since the age of 6 and my first experience with code was the [code.org](code.org) Hour of Code in 2nd grade and since then, I have had many pleasurable experiences with programming in the past decade, which have resulted in 1052 Github commits. My hobbies are playing basketball, listening to music, doing math problems, and most important of them all, programming in various languages.

Picture of Me:
![image](https://github.com/raunak2007/csa-pages/assets/41299387/65d35b24-2dd7-42e1-808d-9a342e7c6613)

Pair Picture:
![image](https://github.com/raunak2007/csa-pages/assets/41299387/ddc84408-6a1c-4840-a9f3-d78cdad01565)

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
  <button onclick="calculateSin()">sin</button>
  <button onclick="calculateCos()">cos</button>
  <button onclick="calculateTan()">tan</button>
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

  function calculateSin() {
    let currentValue = parseFloat(document.getElementById("result").value);
    let result = Math.sin(currentValue);
    document.getElementById("result").value = result;
  }

  function calculateCos() {
    let currentValue = parseFloat(document.getElementById("result").value);
    let result = Math.cos(currentValue);
    document.getElementById("result").value = result;
  }

  function calculateTan() {
    let currentValue = parseFloat(document.getElementById("result").value);
    let result = Math.tan(currentValue);
    document.getElementById("result").value = result;
  }
</script>
</body>
