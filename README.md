<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>💖 My Valentine 💖</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
  margin: 0;
  height: 100vh;
  font-family: Arial, sans-serif;
  background: linear-gradient(135deg, #ffdde1, #ee9ca7);
  overflow: hidden;
}

.page {
  display: none;
  height: 100vh;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.active {
  display: flex;
}

.card {
  background: white;
  padding: 25px;
  border-radius: 20px;
  width: 90%;
  max-width: 320px;
  box-shadow: 0 15px 30px rgba(0,0,0,0.2);
}

button {
  margin-top: 15px;
  padding: 10px 20px;
  border-radius: 20px;
  border: none;
  background: #ff4d6d;
  color: white;
  font-size: 16px;
}

input {
  padding: 10px;
  width: 80%;
  border-radius: 20px;
  border: 1px solid #ff4d6d;
}

.heart {
  position: absolute;
  bottom: -20px;
  font-size: 20px;
  animation: floatUp 5s linear infinite;
}

@keyframes floatUp {
  0% { transform: translateY(0); opacity: 1; }
  100% { transform: translateY(-110vh); opacity: 0; }
}

.big-heart {
  font-size: 60px;
  animation: beat 1s infinite;
}

@keyframes beat {
  50% { transform: scale(1.2); }
}
</style>
</head>

<body>

<!-- 🎵 MUSIC -->
<audio id="music" loop>
  <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_8cfdc8f9c3.mp3" type="audio/mpeg">
</audio>

<!-- PAGE 1 -->
<div class="page active" id="page1">
  <div class="card">
    <h2>💌 Hi Valentine</h2>
    <p>What’s your name?</p>
    <input id="nameInput" placeholder="Your name 💕">
    <br>
    <button onclick="goPage2()">Continue 💖</button>
  </div>
</div>

<!-- PAGE 2 -->
<div class="page" id="page2">
  <div class="card">
    <div class="big-heart">💖</div>
    <p id="typing"></p>
    <button onclick="goPage3()">Next 💍</button>
  </div>
</div>

<!-- PAGE 3 -->
<div class="page" id="page3">
  <div class="card">
    <h2>💍 Will you be my Valentine?</h2>
    <button onclick="yes()">YES 💘</button>
  </div>
</div>

<!-- PAGE 4 -->
<div class="page" id="page4">
  <div class="card">
    <h2>🥰 YAY!</h2>
    <p>You just made my heart so happy 💖</p>
    <div class="big-heart">💓</div>
  </div>
</div>

<script>
let name = "";
let text = "";
let index = 0;

function goPage2() {
  name = document.getElementById("nameInput").value || "My Love";
  switchPage("page1", "page2");
  document.getElementById("music").play();
  text = `Happy Valentine's Day, ${name} 💕
You make my world brighter every day.`;
  typeText();
}

function typeText() {
  if (index < text.length) {
    document.getElementById("typing").innerHTML += text.charAt(index);
    index++;
    setTimeout(typeText, 50);
  }
}

function goPage3() {
  switchPage("page2", "page3");
}

function yes() {
  switchPage("page3", "page4");
}

function switchPage(from, to) {
  document.getElementById(from).classList.remove("active");
  document.getElementById(to).classList.add("active");
}

// Floating hearts
setInterval(() => {
  const heart = document.createElement("div");
  heart.className = "heart";
  heart.innerText = "💖";
  heart.style.left = Math.random() * 100 + "vw";
  heart.style.fontSize = Math.random() * 20 + 10 + "px";
  document.body.appendChild(heart);

  setTimeout(() => heart.remove(), 5000);
}, 500);
</script>

</body>
</html>




