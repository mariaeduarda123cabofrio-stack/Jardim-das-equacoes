<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<title>Jardim das Equações</title>
<style>
body {
  font-family: Arial, sans-serif;
  text-align: center;
  background: linear-gradient(#fceaff, #e0f7ff);
}

#game {
  margin-top: 50px;
}

.flower {
  font-size: 50px;
  transition: 0.5s;
}

.fairy {
  font-size: 40px;
  display: none;
  animation: float 2s infinite;
}

@keyframes float {
  0% {transform: translateY(0);}
  50% {transform: translateY(-10px);}
  100% {transform: translateY(0);}
}

button {
  padding: 10px;
  font-size: 16px;
}
</style>
</head>

<body>

<h1>🌸 Jardim das Equações 🌸</h1>
<p id="story">
A fada Flora precisa da sua ajuda! O vilão André roubou toda a Matemagia... resolva as contas para salvar o jardim!
</p>

<div id="game">
  <h2 id="question"></h2>
  <input type="number" id="answer">
  <button onclick="checkAnswer()">Responder</button>

  <p id="feedback"></p>

  <div class="flower" id="flower">🌱</div>
  <div class="fairy" id="fairy">🧚‍♀️✨</div>
</div>

<script>
let correctAnswer;
let stage = 0;

function newQuestion() {
  let a = Math.floor(Math.random() * 10);
  let b = Math.floor(Math.random() * 10);
  correctAnswer = a + b;
  document.getElementById("question").innerText = `${a} + ${b} = ?`;
}

function checkAnswer() {
  let userAnswer = document.getElementById("answer").value;

  if (userAnswer == correctAnswer) {
    stage++;

    document.getElementById("feedback").innerText = "✨ Muito bem! A Matemagia voltou!";

    document.getElementById("fairy").style.display = "block";

    let flowerStages = ["🌱", "🌿", "🌸", "🌺", "🌼"];
    document.getElementById("flower").innerText = flowerStages[Math.min(stage, 4)];

    setTimeout(() => {
      document.getElementById("fairy").style.display = "none";
    }, 1500);

  } else {
    document.getElementById("feedback").innerText = "💫 Tente novamente, você consegue!";
  }

  document.getElementById("answer").value = "";
  newQuestion();
}

newQuestion();
</script>

</body>
</html>
