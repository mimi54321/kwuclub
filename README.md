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
    .result {
      font-size: 1.5em;
      margin-top: 2em;
    }
  </style>
</head>
<body>
  <h1>京女生診断！あなたにぴったりの部活は？</h1>

  <!-- スタート画面 -->
  <div id="start-screen" class="active">
    <button onclick="startQuiz()">診断スタート</button>
  </div>

　<!-- 質問部分 -->
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
     <button onclick="showResult()">優しい先輩がいる部活</button>
     <button onclick="showResult()">初心者歓迎の部活</button>
     <button onclick="showResult()">自分のペースで続けられる部活</button>
   </div>
</div>



  <!-- 結果画面 -->
  <div id="result" class="result">
    <p>＼あなたにぴったりの部活は…／</p>
    <h2>🎶 マンドリンオーケストラ部！ 🎶</h2>
    <p id="result-text"></p>
    <p>マンドリンオーケストラ部の体験に応募したい方は、下のリンクからどうぞ！</p>
    <a href="https://docs.google.com/forms/d/1Kgp0YwwheMONJPUA0qfHBguXWYVfGkEaKyF_hlECfoQ/viewform?edit_requested=true" target="_blank">楽器体験の応募フォーム</a>
  </div>

  <script>
    let current = 0;
    const questions = document.querySelectorAll('.question');

    function startQuiz() {
      document.getElementById('start-screen').style.display = 'none'; // スタート画面を非表示
      questions[current].classList.add('active'); // 最初の質問を表示
    }

    function nextQuestion() {
      if (current < questions.length - 1) {
        questions[current].classList.remove('active');
        current++;
        questions[current].classList.add('active');
      }
    }

    function showResult() {
      questions[current].classList.remove('active');
      document.getElementById('
