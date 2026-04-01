<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8" />  
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />  
  <title>Truth or Fake</title>  
  <style>  
    * {  
      box-sizing: border-box;  
    }  
  
    body {  
      margin: 0;  
      font-family: Arial, sans-serif;  
      background: linear-gradient(135deg, #f3f4f6, #e5e7eb);  
      color: #1f2937;  
    }  
  
    .container {  
      max-width: 850px;  
      margin: 0 auto;  
      padding: 16px;  
    }  
  
    #header {  
      text-align: center;  
      margin: 24px 0 16px;  
      animation: fadeIn 0.8s ease;  
    }  
  
    #logo {  
      width: 150px;  
      max-width: 60%;  
      display: block;  
      margin: 0 auto 12px;  
      border-radius: 50%;  
      box-shadow: 0 6px 18px rgba(0, 0, 0, 0.18);  
      background: white;  
    }  
  
    h1 {  
      margin: 0;  
      font-size: 2rem;  
      color: #111827;  
    }  
  
    .subtitle {  
      margin-top: 8px;  
      color: #4b5563;  
      font-size: 1rem;  
    }  
  
    .card {  
      background: white;  
      border-radius: 16px;  
      padding: 20px;  
      margin-top: 18px;  
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.08);  
      animation: fadeIn 0.5s ease;  
    }  
  
    h2 {  
      margin-top: 0;  
      font-size: 1.4rem;  
    }  
  
    ul {  
      padding-left: 20px;  
      line-height: 1.7;  
    }  
  
    .highlight {  
      background: #eff6ff;  
      border-left: 4px solid #3b82f6;  
      padding: 12px 14px;  
      border-radius: 10px;  
      margin: 16px 0;  
      color: #1e3a8a;  
    }  
  
    #progress-container {  
      width: 100%;  
      height: 18px;  
      background: #e5e7eb;  
      border-radius: 999px;  
      overflow: hidden;  
      margin-bottom: 14px;  
    }  
  
    #progress-bar {  
      height: 100%;  
      width: 0%;  
      background: linear-gradient(90deg, #10b981, #34d399);  
      border-radius: 999px;  
      transition: width 0.35s ease;  
    }  
  
    .top-info {  
      display: flex;  
      justify-content: space-between;  
      align-items: center;  
      gap: 12px;  
      flex-wrap: wrap;  
      margin-bottom: 10px;  
    }  
  
    #question-number,  
    #timer,  
    #score {  
      font-weight: bold;  
      padding: 8px 12px;  
      border-radius: 10px;  
      background: #f9fafb;  
    }  
  
    #timer.warning {  
      background: #fef3c7;  
      color: #92400e;  
    }  
  
    #timer.danger {  
      background: #fee2e2;  
      color: #991b1b;  
    }  
  
    #question {  
      font-size: 1.3rem;  
      line-height: 1.5;  
      margin: 18px 0;  
      text-align: center;  
      min-height: 90px;  
      display: flex;  
      align-items: center;  
      justify-content: center;  
    }  
  
    .buttons {  
      display: flex;  
      gap: 14px;  
      justify-content: center;  
      flex-wrap: wrap;  
    }  
  
    button {  
      border: none;  
      border-radius: 12px;  
      padding: 14px 24px;  
      font-size: 1rem;  
      font-weight: bold;  
      cursor: pointer;  
      transition: transform 0.15s ease, opacity 0.2s ease, box-shadow 0.2s ease;  
      box-shadow: 0 6px 14px rgba(0, 0, 0, 0.08);  
    }  
  
    button:hover {  
      transform: translateY(-1px);  
      opacity: 0.95;  
    }  
  
    button:disabled {  
      opacity: 0.7;  
      cursor: not-allowed;  
      transform: none;  
    }  
  
    .btn-start {  
      width: 100%;  
      background: #2563eb;  
      color: white;  
      margin-top: 10px;  
    }  
  
    .true {  
      background: #16a34a;  
      color: white;  
      min-width: 140px;  
    }  
  
    .false {  
      background: #dc2626;  
      color: white;  
      min-width: 140px;  
    }  
  
    #feedback {  
      margin-top: 18px;  
      padding: 14px;  
      border-radius: 12px;  
      font-size: 1rem;  
      line-height: 1.6;  
      display: none;  
    }  
  
    .correct {  
      background: #dcfce7;  
      color: #166534;  
      border: 1px solid #86efac;  
    }  
  
    .wrong {  
      background: #fee2e2;  
      color: #991b1b;  
      border: 1px solid #fca5a5;  
    }  
  
    .timesup {  
      background: #fef3c7;  
      color: #92400e;  
      border: 1px solid #fcd34d;  
    }  
  
    #final {  
      text-align: center;  
      display: none;  
    }  
  
    #final-score {  
      font-size: 2rem;  
      font-weight: bold;  
      color: #111827;  
      margin: 12px 0;  
    }  
  
    #final-message {  
      font-size: 1.1rem;  
      line-height: 1.7;  
      margin-top: 10px;  
      color: #374151;  
    }  
  
    .footer-note {  
      text-align: center;  
      font-size: 0.95rem;  
      color: #6b7280;  
      margin-top: 18px;  
    }  
  
    @keyframes fadeIn {  
      from {  
        opacity: 0;  
        transform: translateY(6px);  
      }  
      to {  
        opacity: 1;  
        transform: translateY(0);  
      }  
    }  
  
    @media (max-width: 600px) {  
      h1 {  
        font-size: 1.7rem;  
      }  
  
      #logo {  
        width: 130px;  
      }  
  
      .card {  
        padding: 16px;  
      }  
  
      #question {  
        font-size: 1.1rem;  
        min-height: 110px;  
      }  
  
      .buttons {  
        flex-direction: column;  
      }  
  
      .true,  
      .false,  
      .btn-start {  
        width: 100%;  
      }  
  
      .top-info {  
        flex-direction: column;  
        align-items: stretch;  
      }  
  
      #question-number,  
      #timer,  
      #score {  
        text-align: center;  
      }  
    }  
  </style>  
</head>  
<body>  
  <div class="container">  
    <div id="header">  
      <img src="logo.png" alt="Truth or Fake Logo" id="logo" />  
      <h1>Truth or Fake</h1>  
      <div class="subtitle">Learn how to recognize fake news and test your skills.</div>  
    </div>  
  
    <div id="intro" class="card">  
      <h2>How to Distinguish Fake News from Real News</h2>  
      <p>  
        Fake news often looks convincing, but there are some important signs that can help you understand whether a piece of news is trustworthy or not.  
      </p>  
  
      <ul>  
        <li><strong>Check the source:</strong> reliable news usually comes from recognized newspapers, institutions, or official organizations.</li>  
        <li><strong>Look for the author:</strong> a real article often has a clear author and verifiable credentials.</li>  
        <li><strong>Check the date:</strong> old news may be shared again to create confusion.</li>  
        <li><strong>Read beyond the headline:</strong> fake news often uses shocking titles to attract attention.</li>  
        <li><strong>Look for evidence:</strong> real news contains data, quotes, or references to trustworthy sources.</li>  
        <li><strong>Compare with other sources:</strong> if the news is real, other reliable websites usually report it too.</li>  
        <li><strong>Watch for emotional language:</strong> fake news often tries to make readers angry, scared, or shocked.</li>  
      </ul>  
  
      <div class="highlight">  
        In this quiz, you will read 10 news statements. Decide whether each one is <strong>true</strong> or <strong>false</strong>.    
        You gain <strong>3 points</strong> for each correct answer.  
      </div>  
  
      <button class="btn-start" onclick="startQuiz()">Start Quiz</button>  
    </div>  
  
    <div id="quiz" class="card" style="display: none;">  
      <div id="progress-container">  
        <div id="progress-bar"></div>  
      </div>  
  
      <div class="top-info">  
        <div id="question-number">Question 1 / 10</div>  
        <div id="timer">Time: 10</div>  
        <div id="score">Score: 0</div>  
      </div>  
  
      <div id="question"></div>  
  
      <div class="buttons">  
        <button id="trueBtn" class="true" onclick="answer(true)">True</button>  
        <button id="falseBtn" class="false" onclick="answer(false)">False</button>  
      </div>  
  
      <div id="feedback"></div>  
    </div>  
  
    <div id="final" class="card">  
      <h2>Quiz Finished</h2>  
      <div id="final-score"></div>  
      <div id="final-message"></div>  
      <div class="footer-note">Created for a fake news awareness project.</div>  
    </div>  
  </div>  
  
  <script>  
    const questions = [  
      {  
        q: "Scientists confirm that drinking 2 liters of water per day boosts intelligence by 30%.",  
        a: false,  
        reason: "This is false because it makes an exaggerated and very precise claim without citing any scientific source. Drinking water is healthy, but there is no evidence that it increases intelligence by 30%."  
      },  
      {  
        q: "NASA successfully crashed a spacecraft into an asteroid to test planetary defense.",  
        a: true,  
        reason: "This is true. NASA carried out the DART mission to test whether a spacecraft could change the path of an asteroid."  
      },  
      {  
        q: "A man survived for 3 months eating only pizza and lost 20 kilograms.",  
        a: false,  
        reason: "This is false because it sounds sensational and unrealistic, and there is no credible evidence or medical source supporting the claim."  
      },  
      {  
        q: "The European Union approved a law requiring USB-C chargers for most electronic devices.",  
        a: true,  
        reason: "This is true. The EU approved rules introducing USB-C as a common charging standard for many devices."  
      },  
      {  
        q: "Sharks are evolving to walk on land because of climate change.",  
        a: false,  
        reason: "This is false. Some species can move in unusual ways, but the statement exaggerates the science and turns it into clickbait."  
      },  
      {  
        q: "Artificial intelligence has passed a university-level law exam.",  
        a: true,  
        reason: "This is true. Some AI systems have performed at or above the level required in law-related exams and tests."  
      },  
      {  
        q: "Eating chocolate every day doubles human lifespan, researchers say.",  
        a: false,  
        reason: "This is false because it uses an extreme health claim with no believable evidence. Real scientific studies do not make conclusions like this."  
      },  
      {  
        q: "Japan built a hotel staffed almost entirely by robots.",  
        a: true,  
        reason: "This is true. Japan created the Henn-na Hotel, known for using robots in many service roles."  
      },  
      {  
        q: "Aliens contacted Earth governments in 2024, according to leaked documents.",  
        a: false,  
        reason: "This is false. It is a vague conspiracy-style statement with no trustworthy proof and no official verification."  
      },  
      {  
        q: "Climate change is increasing the frequency and intensity of many extreme weather events.",  
        a: true,  
        reason: "This is true. Scientific research widely supports the link between climate change and many forms of extreme weather."  
      }  
    ];  
  
    let current = 0;  
    let score = 0;  
    let timeLeft = 10;  
    let timer = null;  
    let answered = false;  
  
    const intro = document.getElementById("intro");  
    const quiz = document.getElementById("quiz");  
    const finalScreen = document.getElementById("final");  
  
    const questionEl = document.getElementById("question");  
    const questionNumberEl = document.getElementById("question-number");  
    const timerEl = document.getElementById("timer");  
    const scoreEl = document.getElementById("score");  
    const progressBar = document.getElementById("progress-bar");  
    const feedbackEl = document.getElementById("feedback");  
    const trueBtn = document.getElementById("trueBtn");  
    const falseBtn = document.getElementById("falseBtn");  
    const finalScoreEl = document.getElementById("final-score");  
    const finalMessageEl = document.getElementById("final-message");  
  
    function startQuiz() {  
      intro.style.display = "none";  
      quiz.style.display = "block";  
      current = 0;  
      score = 0;  
      showQuestion();  
    }  
  
    function showQuestion() {  
      answered = false;  
      enableButtons();  
  
      const item = questions[current];  
      questionEl.textContent = item.q;  
      questionNumberEl.textContent = `Question ${current + 1} / ${questions.length}`;  
      scoreEl.textContent = `Score: ${score}`;  
      feedbackEl.style.display = "none";  
      feedbackEl.className = "";  
      feedbackEl.textContent = "";  
  
      updateProgressBar();  
  
      timeLeft = 10;  
      timerEl.textContent = `Time: ${timeLeft}`;  
      timerEl.classList.remove("warning", "danger");  
  
      clearInterval(timer);  
      timer = setInterval(() => {  
        timeLeft--;  
        timerEl.textContent = `Time: ${timeLeft}`;  
  
        if (timeLeft <= 5 && timeLeft > 2) {  
          timerEl.classList.add("warning");  
          timerEl.classList.remove("danger");  
        }  
  
        if (timeLeft <= 2) {  
          timerEl.classList.add("danger");  
          timerEl.classList.remove("warning");  
        }  
  
        if (timeLeft === 0) {  
          clearInterval(timer);  
          timeUp();  
        }  
      }, 1000);  
    }  
  
    function updateProgressBar() {  
      const progress = (current / questions.length) * 100;  
      progressBar.style.width = `${progress}%`;  
    }  
  
    function disableButtons() {  
      trueBtn.disabled = true;  
      falseBtn.disabled = true;  
    }  
  
    function enableButtons() {  
      trueBtn.disabled = false;  
      falseBtn.disabled = false;  
    }  
  
    function answer(userAnswer) {  
      if (answered) return;  
      answered = true;  
      clearInterval(timer);  
      disableButtons();  
  
      const item = questions[current];  
  
      if (userAnswer === item.a) {  
        score += 3;  
        feedbackEl.style.display = "block";  
        feedbackEl.className = "correct";  
        feedbackEl.innerHTML = `<strong>Correct.</strong> ${item.reason}`;  
      } else {  
        feedbackEl.style.display = "block";  
        feedbackEl.className = "wrong";  
        feedbackEl.innerHTML = `<strong>Wrong.</strong> ${item.reason}`;  
      }  
  
      scoreEl.textContent = `Score: ${score}`;  
      setTimeout(nextQuestion, 2600);  
    }  
  
    function timeUp() {  
      if (answered) return;  
      answered = true;  
      disableButtons();  
  
      const item = questions[current];  
      feedbackEl.style.display = "block";  
      feedbackEl.className = "timesup";  
      feedbackEl.innerHTML = `<strong>Time's up.</strong> ${item.reason}`;  
  
      setTimeout(nextQuestion, 2600);  
    }  
  
    function nextQuestion() {  
      current++;  
      if (current < questions.length) {  
        showQuestion();  
      } else {  
        endQuiz();  
      }  
    }  
  
    function endQuiz() {  
      clearInterval(timer);  
      quiz.style.display = "none";  
      finalScreen.style.display = "block";  
      progressBar.style.width = "100%";  
  
      const maxScore = questions.length * 3;  
      finalScoreEl.textContent = `${score} / ${maxScore}`;  
  
      let message = "";  
  
      if (score >= 27) {  
        message = "Excellent. You are very good at recognizing the signs of fake news and checking whether information is reliable.";  
      } else if (score >= 18) {  
        message = "Good job. You already know many useful strategies, but you should still pay close attention to sources, evidence, and sensational headlines.";  
      } else if (score >= 9) {  
        message = "Not bad, but there is room for improvement. Remember to check the source, the author, the date, and whether other reliable outlets report the same story.";  
      } else {  
        message = "Be careful. Fake news can be very convincing. Try to slow down, verify information, and never trust a headline immediately.";  
      }  
  
      finalMessageEl.textContent = message;  
    }  
  </script>  
</body>  
</html>  
