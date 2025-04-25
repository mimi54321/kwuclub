<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>京女生診断ゲーム</title>
  <style>
    body {
      font-family: sans-serif;
      background-color: #fefefe;
      text-align: center;
      padding: 2em;
    }
    .hidden {
      display: none;
    }
    .question, .result {
      display: none;
    }
    .active {
      display: block;
    }
    button {
      display: block;
      margin: 1em auto;
      padding: 1em 2em;
      font-size: 1em;
      background-color: #ffb6c1;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }
    h1 {
      font-size: 1.8em;
      margin-bottom: 1em;
    }
    .result {
      font-size: 1.2em;
      margin-top: 2em;
    }
    a.form-link {
      display: inline-block;
      margin-top: 1.5em;
      padding: 0.8em 1.2em;
      background-color: #f06292;
      color: white;
      text-decoration: none;
      border-radius: 8px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div id="start-screen" class="active">
    <h1>京女生診断！<br>あなたにぴったりの部活は？</h1>
    <button onclick="startGame()">スタート</button>
  </div>

  <div id="question-container">
    <div class="question">
      <p>Q1. 放課後はどう過ごしたい？</p>
      <button onclick="nextQuestion()">おしゃべりしながらゆるっと活動したい</button>
      <button onclick="nextQuestion()">ひとりで黙々と打ち込める時間がほしい</button>
      <button onclick="nextQuestion()">みんなで目標に向かってがんばりたい</button>
    </div>

    <div class="question">
      <p>Q2. 興味があるものは？</p>
      <button onclick="nextQuestion()">音楽</button>
      <button onclick="nextQuestion()">楽しいこと</button>
      <button onclick="nextQuestion()">ちょっと人と違うこと</button>
    </div>

    <div class="question">
      <p>Q3. 音楽経験はある？</p>
      <button onclick="showResult(true)">ある！</button>
      <button onclick="showResult(false)">ない！</button>
    </div>
  </div>

  <div id="result" class="result">
    <p>＼あなたにぴったりの部活は…／</p>
    <h2>🎶 マンドリンオーケストラ部！ 🎶</h2>
    <p id="experience-message"></p>
    <a class="form-link" href="https://docs.google.com/forms/d/1Kgp0YwwheMONJPUA0qfHBguXWYVfGkEaKyF_hlECfoQ/viewform" target="_blank">
      🎵 楽器体験に応募する
    </a>
  </div>

  <script>
    let current = 0;
    const questions = document.querySelectorAll('.question');
    const startScreen = document.getElementById('start-screen');
    const result = document.getElementById('result');

    function startGame() {
      startScreen.classList.remove('active');
      current = 0;
      questions[current].classList.add('active');
    }

    function nextQuestion() {
      if (current < questions.length - 1) {
        questions[current].classList.remove('active');
        current++;
        questions[current].classList.add('active');
      }
    }

    function showResult(hasExperience) {
      questions[current].classList.remove('active');
      result.classList.add('active');

      const message = document.getElementById('experience-message');
      if (hasExperience) {
        message.textContent = "音楽経験があるあなたはさらに楽しめます！大学で新しいことに挑戦してみませんか？新しい音楽仲間と一緒に奏でよう♪";
      } else {
        message.textContent = "音楽経験がなくても、安心して上達できるマンドリンオーケストラ部がおすすめ！";
      }
    }
  </script>
</body>
</html>
