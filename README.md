# Quiz-fun
Films musiques années 2000
<!DOCTYPE html>
<html>
<head>
  <title>Quiz Fun</title>
  <style>
    body { font-family: Arial, sans-serif; max-width: 400px; margin: auto; padding: 20px; }
    button { margin: 5px 0; width: 100%; }
  </style>
</head>
<body>
  <h2>Quiz Culture Générale</h2>
  <div id="quiz"></div>
  <button id="nextBtn" style="display:none;">Question suivante</button>
  <p id="result"></p>

  <script>
    const questions = [
      { q: "Quelle est la capitale de la France ?", options: ["Paris", "Lyon", "Marseille"], answer: 0 },
      { q: "Combien y a-t-il de continents ?", options: ["5", "6", "7"], answer: 2 },
      { q: "Qui a écrit 'Les Misérables' ?", options: ["Victor Hugo", "Molière", "Zola"], answer: 0 }
    ];

    let current = 0, score = 0;

    function showQuestion() {
      let quizDiv = document.getElementById('quiz');
      quizDiv.innerHTML = `<p>${questions[current].q}</p>`;
      questions[current].options.forEach((opt, i) => {
        quizDiv.innerHTML += `<button onclick="checkAnswer(${i})">${opt}</button>`;
      });
      document.getElementById('result').innerText = '';
      document.getElementById('nextBtn').style.display = 'none';
    }

    function checkAnswer(selected) {
      if(selected === questions[current].answer) {
        score++;
        document.getElementById('result').innerText = "Bonne réponse ! 🎉";
      } else {
        document.getElementById('result').innerText = "Mauvaise réponse.";
      }
      document.querySelectorAll('#quiz button').forEach(btn => btn.disabled = true);
      document.getElementById('nextBtn').style.display = 'block';
    }

    document.getElementById('nextBtn').onclick = function() {
      current++;
      if(current < questions.length) {
        showQuestion();
      } else {
        document.getElementById('quiz').innerHTML = `<h3>Quiz terminé ! Score : ${score}/${questions.length}</h3>`;
        this.style.display = 'none';
      }
    }

    showQuestion();
  </script>
</body>
</html>
