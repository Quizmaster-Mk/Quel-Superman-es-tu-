<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Quel Superman êtes-vous ?</title>
  <style>
    body {
      font-family: 'Courier New', monospace;
      background-color: #0d1a57; /* Bleu foncé Superman */
      color: #fff;
      margin: 0;
      padding: 20px;
      text-align: center;
    }

    h1 {
      color: #ffcc00; /* Jaune emblématique */
      text-shadow: 2px 2px 5px #c60000; /* Rouge Superman */
      font-size: 40px;
      margin-bottom: 20px;
    }

    img.logo {
      max-width: 200px;
      margin-bottom: 20px;
    }

    .question {
      margin: 20px 0;
      background-color: #1a237e; /* Bleu foncé */
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(255, 204, 0, 0.7);
    }

    .options button {
      background-color: #c62828; /* Rouge Superman */
      color: #fff;
      padding: 10px 20px;
      border: none;
      margin: 5px;
      font-size: 18px;
      cursor: pointer;
      border-radius: 5px;
      transition: all 0.3s ease;
    }

    .options button:hover {
      background-color: #ffcc00;
      color: #0d1a57;
      transform: scale(1.1);
    }

    .result {
      background-color: #1a237e;
      padding: 20px;
      border-radius: 10px;
      margin-top: 20px;
      display: none;
      box-shadow: 0 0 10px rgba(255, 204, 0, 0.7);
    }

    .score {
      font-size: 18px;
      margin-top: 10px;
      color: #ffcc00;
    }
  </style>
</head>
<body>
  <img class="logo" src="https://zupimages.net/up/25/15/4ubo.png" alt="Logo Superman">
  <h1>Quel Superman êtes-vous ?</h1>

  <div id="quiz-container">
    <div class="question" id="question-container">
      <h2 id="question-text"></h2>
      <div class="options" id="options-container"></div>
    </div>
  </div>

  <div class="result" id="result-container">
    <h2>Vous êtes...</h2>
    <p id="result-text"></p>
    <p class="score">Votre résultat est basé sur vos choix !</p>
    <button onclick="startQuiz()">Recommencer le quiz</button>
  </div>

  <script>
    const questions = [
      { question: "Quel est votre plus grand atout ?", options: ["Force surhumaine", "Vitesse", "Vol", "Vision laser"], result: [0, 1, 2, 3] },
      { question: "Comment gérez-vous les situations de crise ?", options: ["Calmement", "Avec bravoure", "Avec stratégie", "Avec compassion"], result: [4, 5, 6, 7] },
      { question: "Quelle est votre faiblesse ?", options: ["Kryptonite", "Responsabilités", "Solitude", "Trop de cœur"], result: [8, 9, 0, 1] },
      { question: "Quel est votre lieu favori ?", options: ["Ferme familiale", "Ville animée", "Forteresse de solitude", "Bureau du Daily Planet"], result: [2, 3, 4, 5] },
      { question: "Votre plus grande peur ?", options: ["Échouer à sauver", "Perdre vos proches", "Être contrôlé", "Être incompris"], result: [6, 7, 8, 9] },
      { question: "Quel est votre but ultime ?", options: ["Protéger l'humanité", "Être un symbole d'espoir", "Vivre librement", "Comprendre votre place dans le monde"], result: [0, 1, 2, 3] },
      { question: "Comment vos amis vous décriraient ?", options: ["Loyal", "Inspirant", "Mystérieux", "Déterminé"], result: [4, 5, 6, 7] },
      { question: "Quel est votre style de combat ?", options: ["Direct", "Défensif", "Tactique", "Impressionnant"], result: [8, 9, 0, 1] },
      { question: "Un mot pour vous résumer ?", options: ["Espoir", "Courage", "Sacrifice", "Responsabilité"], result: [2, 3, 4, 5] },
      { question: "Votre plus grande qualité ?", options: ["Force morale", "Générosité", "Charisme", "Justice"] , result: [6, 7, 8, 9] }
    ];

    const characters = [
      { name: "Superman Classique", description: "Héros emblématique, force, vitesse, vol. Symbole d'espoir et de justice." },
      { name: "Clark Kent", description: "Journaliste discret, ancré dans l'humanité, plein d'empathie et de discernement." },
      { name: "Superman Red Son", description: "Une version alternative élevée en URSS, déterminé et implacable dans sa vision du bien." },
      { name: "Superman Prime", description: "Incarnation divine de Superman, puissance absolue et sagesse millénaire." },
      { name: "Superboy (Kon-El)", description: "Jeune clone impulsif mais héroïque, en quête d'identité." },
      { name: "Kal-L (Terre-2)", description: "Version plus classique et expérimentée de Superman, fondée sur la tradition." },
      { name: "Val-Zod", description: "Superman pacifiste et intellectuel venant d'une Terre alternative." },
      { name: "Cyborg Superman", description: "Héros brisé devenu machine, tiraillé entre vengeance et rédemption." },
      { name: "Bizarro", description: "Reflet imparfait de Superman, étrange mais sincère dans sa propre logique." },
      { name: "Eradicator", description: "Intelligence kryptonienne extrême, focalisée sur la survie de la culture kryptonienne." }
    ];

    let currentQuestion = 0;
    let userAnswers = [];

    function startQuiz() {
      currentQuestion = 0;
      userAnswers = [];
      document.getElementById('result-container').style.display = 'none';
      document.getElementById('quiz-container').style.display = 'block';
      showQuestion();
    }

    function showQuestion() {
      const question = questions[currentQuestion];
      document.getElementById('question-text').innerText = question.question;

      const optionsContainer = document.getElementById('options-container');
      optionsContainer.innerHTML = '';

      question.options.forEach((option, index) => {
        const button = document.createElement('button');
        button.innerText = option;
        button.onclick = () => {
          userAnswers.push(question.result[index]);
          currentQuestion++;
          if (currentQuestion < questions.length) {
            showQuestion();
          } else {
            showResult();
          }
        };
        optionsContainer.appendChild(button);
      });
    }

    function showResult() {
      const resultIndex = userAnswers.reduce((a, b) => a + b, 0) % characters.length;
      const result = characters[resultIndex];

      document.getElementById('result-text').innerText = `${result.name} - ${result.description}`;
      document.getElementById('quiz-container').style.display = 'none';
      document.getElementById('result-container').style.display = 'block';
    }

    startQuiz();
  </script>
</body>
</html>
