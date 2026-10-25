# Home-gamehttps://YOUR-USERNAME.github.io/footyzone/
Replace YOUR-USERNAME with your GitHub username, then open the link to check it works.
<!DOCTYPE html>
<html lang="en">
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>FootyZone Quiz</title>
<style>
body {
  margin: 0;
  padding: 20px;
  background: #10291f;
  color: white;
  font-family: Arial, sans-serif;
}
.card {
  max-width: 450px;
  margin: 20px auto;
  padding: 22px;
  background: #214435;
  border-radius: 18px;
}
h1 { color: #8df0ae; }
button {
  display: block;
  width: 100%;
  padding: 14px;
  margin: 10px 0;
  border: 0;
  border-radius: 10px;
  font-size: 16px;
  cursor: pointer;
}
.answer { background: white; color: #10291f; }
#message { font-weight: bold; }
#next { background: #8df0ae; }
</style>
</head>
<body>
<div class="card">
  <h1>⚽ FootyZone</h1>
  <p>THE FOOTBALL QUIZ</p>
  <p id="progress"></p>
  <h2 id="question"></h2>
  <div id="answers"></div>
  <p id="message" aria-live="polite"></p>
  <p id="score">Score: 0</p>
  <button id="next" onclick="nextQuestion()">
    Next Question →
  </button>
</div>

<script>
const quiz = [
  {
    q: "How many players does one team start with on the pitch in a standard football match?",
    a: ["9", "10", "11", "12"],
    correct: 2
  },
  {
    q: "Which player can normally use their hands inside their own penalty area?",
    a: ["Striker", "Goalkeeper", "Midfielder", "Winger"],
    correct: 1
  },
  {
    q: "How long is a standard football match, excluding added time?",
    a: ["60 minutes", "70 minutes", "80 minutes", "90 minutes"],
    correct: 3
  },
  {
    q: "What colour card means a player is sent off?",
    a: ["Blue", "Green", "Red", "White"],
    correct: 2
  },
  {
    q: "What is it called when a player scores three goals in one match?",
    a: ["Hat-trick", "Clean sheet", "Corner", "Assist"],
    correct: 0
  }
];

let index = 0;
let points = 0;
let answered = false;

function showQuestion() {
  answered = false;
  document.getElementById("message").textContent = "";
  document.getElementById("next").textContent =
    index === quiz.length - 1 ? "See Final Score" : "Next Question →";
  document.getElementById("progress").textContent =
    "Question " + (index + 1) + " of " + quiz.length;
  document.getElementById("question").textContent = quiz[index].q;
  const area = document.getElementById("answers");
  area.innerHTML = "";

  quiz[index].a.forEach((answer, i) => {
    const button = document.createElement("button");
    button.className = "answer";
    button.textContent = answer;
    button.onclick = () => chooseAnswer(i);
    area.appendChild(button);
  });

  document.getElementById("score").textContent = "Score: " + points;
}

function chooseAnswer(choice) {
  if (answered) return;
  answered = true;

  if (choice === quiz[index].correct) {
    points++;
    document.getElementById("message").textContent = "✅ Correct!";
  } else {
    document.getElementById("message").textContent =
      "❌ Not quite. Answer: " + quiz[index].a[quiz[index].correct];
  }

  document.getElementById("score").textContent = "Score: " + points;
}

function nextQuestion() {
  if (index < quiz.length - 1) {
    index++;
    showQuestion();
  } else {
    document.querySelector(".card").innerHTML =
      "<h1>⚽ Full Time!</h1><h2>Your score: " +
      points + " / " + quiz.length +
      "</h2><p>Thanks for playing FootyZone!</p>" +
      '<button onclick="location.reload()">Play Again</button>';
  }
}

showQuestion();
</script>
</body>
</html>
# Home-game
