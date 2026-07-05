<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>연봉 계산기 PRO</title>

<style>
body{
  font-family: Arial;
  background:#f4f6f9;
  margin:0;
  padding:20px;
}

.container{
  max-width:520px;
  margin:auto;
}

h2{
  text-align:center;
}

.card{
  background:white;
  padding:18px;
  border-radius:12px;
  box-shadow:0 4px 10px rgba(0,0,0,0.08);
  margin-bottom:15px;
}

label{
  font-size:14px;
}

input{
  width:100%;
  padding:10px;
  margin:8px 0;
  border:1px solid #ddd;
  border-radius:8px;
}

button{
  width:100%;
  padding:10px;
  border:none;
  border-radius:8px;
  background:#4f7cff;
  color:white;
  font-weight:bold;
  cursor:pointer;
}

.result{
  margin-top:10px;
  font-weight:bold;
}

.small{
  font-size:12px;
  color:#666;
}
</style>
</head>

<body>

<div class="container">

<h2>💰 연봉 / 실수령 계산기 PRO</h2>

<!-- 1. 연봉 → 시급 -->
<div class="card">
<h3>💵 연봉 → 시급</h3>
<input id="salary" type="number" placeholder="연봉 입력">
<button onclick="calcHourly()">계산</button>
<div class="result" id="hourlyResult"></div>
</div>

<!-- 2. 시급 → 연봉 -->
<div class="card">
<h3>⏰ 시급 → 연봉</h3>
<input id="hourly" type="number" placeholder="시급 입력">
<button onclick="calcSalary()">계산</button>
<div class="result" id="salaryResult"></div>
</div>

<!-- 3. 세전 → 세후 -->
<div class="card">
<h3>🧾 세전 → 세후 (간이)</h3>
<input id="gross" type="number" placeholder="월급 입력">
<button onclick="calcNet()">계산</button>
<div class="small">※ 4대보험 약 9% 기준</div>
<div class="result" id="netResult"></div>
</div>

</div>

<script>

const MONTH_HOURS = 209;

// 1️⃣ 연봉 → 시급
function calcHourly(){
  let salary = Number(document.getElementById("salary").value);
  if(!salary) return;

  let hourly = salary / (MONTH_HOURS * 12);

  document.getElementById("hourlyResult").innerHTML =
    "💵 시급: " + Math.round(hourly).toLocaleString() + "원";
}

// 2️⃣ 시급 → 연봉
function calcSalary(){
  let hourly = Number(document.getElementById("hourly").value);
  if(!hourly) return;

  let salary = hourly * MONTH_HOURS * 12;

  document.getElementById("salaryResult").innerHTML =
    "💰 연봉: " + Math.round(salary).toLocaleString() + "원";
}

// 3️⃣ 세전 → 세후 (4대보험 약 9%)
function calcNet(){
  let gross = Number(document.getElementById("gross").value);
  if(!gross) return;

  let insurance = gross * 0.09;
  let net = gross - insurance;

  document.getElementById("netResult").innerHTML =
    "📉 실수령: " + Math.round(net).toLocaleString() + "원 (약)";
}

</script>

</body>
</html>
