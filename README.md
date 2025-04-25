<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
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
    .question, .result, #start-screen, #music-experience {
      display: none;
    }
    .active {
      display: block !important;
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
    .result {
      font-size: 1.2em;
      margin-top: 2em;
    }
    a {
      color: #ff69b4;
      font-weight: bold;
      text-decoration: none;
    }
  </style>
</head>
<body>
  <h1>京女生診断！あなたにぴったりの部活は？</h1>

  <!-- スタート画面 -->
  <div id="start-screen" class="active">
    <p>あなたにぴったりの部活を診断しよう！</p>
    <button onclick="startQuiz()">始める</button>

    function startQuiz() {
  document.getElementById('start-screen').style.display = 'none'; // ← これでスタート画面ごと消える
  questions[current].classList.add('active');
}

  </div>

  <!-- 質問 -->
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
      <p>Q3. どんな雰囲気の部活がいい？</p>
      <button onclick="nextQuestion()">優しい先輩がいる部活</button>
      <button onclick="nextQuestion()">初心者歓迎の部活</button>
      <button onclick="nextQuestion()">自分のペースで続けられる部活</button>
    </div>
  </div>

  <!-- 音楽経験 -->
  <div id="music-experience">
    <p>Q4. 音楽経験はありますか？</p>
    <button onclick="showResult('no')">ない</button>
    <button onclick="showResult('yes')">ある</button>
  </div>

  <!-- 結果 -->
  <div id="result" class="result">
    <p>＼あなたにぴったりの部活は…／</p>
    <h2>🎶 マンドリンオーケストラ部！ 🎶</h2>
    <p id="experience-message"></p>
    <p>楽器体験の応募フォームはこちらから👇</p>
    <p><a href="https://docs.google.com/forms/d/1Kgp0YwwheMONJPUA0qfHBguXWYVfGkEaKyF_hlECfoQ/viewform?edit_requested=true" target="_blank">▶ 楽器体験に応募する</a></p>
  </div>

  <script>
    let current = 0;
    const questions = document.querySelectorAll('.question');
    const questionContainer = document.getElementById('question-container');
    const startScreen = document.getElementById('start-screen');
    const musicExperience = document.getElementById('music-experience');
    const result = document.getElementById('result');
    const experienceMessage = document.getElementById('experience-message');

    function startQuiz() {
      startScreen.classList.remove('active');
      questions[current].classList.add('active');
    }

    function nextQuestion() {
      if (current < questions.length - 1) {
        questions[current].classList.remove('active');
        current++;
        questions[current].classList.add('active');
      } else {
        questions[current].classList.remove('active');
        musicExperience.classList.add('active');
      }
    }

    function showResult(experience) {
      musicExperience.classList.remove('active');
      result.classList.add('active');

      if (experience === 'no') {
        experienceMessage.innerText = "音楽経験がなくても、安心して上達できるマンドリンオーケストラ部がおすすめ！";
      } else {
        experienceMessage.innerText = "音楽経験があるあなたはさらに楽しめます！大学で新しいことに挑戦してみませんか？新しい音楽仲間と一緒に奏でよう♪";
      }
    }
  </script>
</body>
</html>
