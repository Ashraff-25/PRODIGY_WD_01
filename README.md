# PRODIGY_WD_02
#HTML

<!DOCTYPE html>
<html lang="en">
<head>
 
  <meta charset="UTF-8">
  <title>Stopwatch</title>
  
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="stopwatch-container">
  
    <h1 id="display">00:00:00</h1>
    <div class="buttons">
      <button id="start">Start</button>
      <button id="pause">Pause</button>
      <button id="reset">Reset</button>
      <button id="lap">Lap</button>
    </div>
    <h1 style="color:brown;">Stop - Watch</h1>
    <ul id="laps"></ul>
  </div>
  <script src="script.js"></script>
</body>
</html>

#CSS

/* style.css */
body {
  font-family: Arial, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #e0f7fa;
}

.stopwatch-container {
  text-align: center;
}

#display {
  font-size: 3rem;
  margin-bottom: 20px;
}

button {
  margin: 5px;
  padding: 10px 20px;
  font-size: 1rem;
  border: none;
  background-color: teal;
  color: white;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #00695c;
}

#laps {
  margin-top: 20px;
  list-style: none;
  padding: 0;
}

#Javascript
// script.js
let [hours, minutes, seconds] = [0, 0, 0];
let display = document.getElementById("display");
let interval = null;

document.getElementById("start").onclick = () => {
  if (!interval) {
    interval = setInterval(startTimer, 1000);
  }
};

document.getElementById("pause").onclick = () => {
  clearInterval(interval);
  interval = null;
};

document.getElementById("reset").onclick = () => {
  clearInterval(interval);
  interval = null;
  [hours, minutes, seconds] = [0, 0, 0];
  display.innerText = "00:00:00";
  document.getElementById("laps").innerHTML = "";
};

document.getElementById("lap").onclick = () => {
  const lapTime = display.innerText;
  const lapItem = document.createElement("li");
  lapItem.textContent = lapTime;
  document.getElementById("laps").appendChild(lapItem);
};

function startTimer() {
  seconds++;
  if (seconds == 60) {
    seconds = 0;
    minutes++;
    if (minutes == 60) {
      minutes = 0;
      hours++;
    }
  }

  let h = hours < 10 ? "0" + hours : hours;
  let m = minutes < 10 ? "0" + minutes : minutes;
  let s = seconds < 10 ? "0" + seconds : seconds;

  display.innerText = `${h}:${m}:${s}`;
}



