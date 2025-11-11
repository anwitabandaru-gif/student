---
title: SAT Vocabulary Practice
layout: post
permalink: /vocabgame
description: Study 1000 words from Sparknotes for the SAT
author: Anwita Bandaru
---

## SAT Vocabulary Quiz: 1000 Words

> Test your SAT vocabulary knowledge. Your progress will automatically save in your browser’s local storage.

<div align="center">

<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>SAT Vocabulary Quiz — 1000 Words</title>
  <style>
    body{font-family:Inter,ui-sans-serif;background:#0f1724;color:#e2e8f0;padding:2rem;}
    .container{max-width:960px;margin:auto;}
    .card{background:#1e293b;padding:1.5rem;border-radius:1rem;margin-top:1rem;box-shadow:0 8px 20px rgba(0,0,0,0.5);}    
    .btn{background:#334155;color:#7dd3fc;border:none;border-radius:.5rem;padding:.6rem 1.2rem;margin-top:1rem;cursor:pointer;}
    .btn:hover{background:#475569;}
    .option{background:#0b1220;padding:.75rem;border-radius:.5rem;margin:.25rem 0;cursor:pointer;}
    .option.selected{border:1px solid #7dd3fc;}
    .progress{height:10px;background:#1e3a8a;border-radius:6px;overflow:hidden;margin-top:8px;}
    .bar{height:100%;background:linear-gradient(90deg,#7dd3fc,#c084fc);width:0%;transition:width .3s ease;}
    .meta{color:#9aa8bf;margin-top:8px}
    #explainBox{margin-top:1rem;display:none;color:#dff3ff;}
  </style>
</head>
<body>
  <div class="container">
    <h1>SAT Vocabulary Quiz — 1000 Words</h1>
    <p>Test your SAT vocabulary knowledge! Progress saves automatically.</p>

    <div class="card" id="quizCard">
      <div id="definitionBox" style="font-size:18px;font-weight:600;margin-bottom:12px">Loading words...</div>
      <div id="options"></div>
      <button id="submitBtn" class="btn">Submit</button>
      <button id="nextBtn" class="btn" style="display:none;">Next</button>
      <div id="explainBox"></div>
      <div class="progress"><div class="bar" id="progressBar"></div></div>
      <p id="scoreText" class="meta">0 correct out of 1000</p>
    </div>
  </div>

  <script>
    let masterList = [];
    let pool = [];
    let current = null;
    let correctSet = new Set(JSON.parse(localStorage.getItem("satCorrectWords") || "[]"));

    const definitionBox = document.getElementById("definitionBox");
    const optionsEl = document.getElementById("options");
    const submitBtn = document.getElementById("submitBtn");
    const nextBtn = document.getElementById("nextBtn");
    const explainBox = document.getElementById("explainBox");
    const scoreText = document.getElementById("scoreText");
    const progressBar = document.getElementById("progressBar");

    async function loadWords() {
      const response = await fetch("sat_vocab_json.json");
      const data = await response.json();
      masterList = data.words;
      pool = masterList.slice();
      updateScore();
      nextQuestion();
    }

    function updateScore() {
      scoreText.textContent = `${correctSet.size} correct out of 1000`;
      const pct = ((correctSet.size / 1000) * 100).toFixed(1);
      progressBar.style.width = pct + "%";
    }

    function nextQuestion() {
      explainBox.style.display = "none";
      nextBtn.style.display = "none";
      submitBtn.style.display = "inline-block";
      optionsEl.innerHTML = "";

      if (pool.length === 0) pool = masterList.slice();

      const idx = Math.floor(Math.random() * pool.length);
      current = pool.splice(idx, 1)[0];
      definitionBox.textContent = current.definition;

      const distractors = new Set();
      while (distractors.size < 3) {
        const rand = masterList[Math.floor(Math.random() * masterList.length)].word;
        if (rand !== current.word) distractors.add(rand);
      }

      const choices = [current.word, ...Array.from(distractors)].sort(() => Math.random() - 0.5);
      for (const choice of choices) {
        const div = document.createElement("div");
        div.className = "option";
        div.textContent = choice;
        div.onclick = () => {
          document.querySelectorAll(".option").forEach(o => o.classList.remove("selected"));
          div.classList.add("selected");
        };
        optionsEl.appendChild(div);
      }
    }

    submitBtn.onclick = () => {
      const sel = document.querySelector(".option.selected");
      if (!sel) {
        alert("Choose an option first.");
        return;
      }
      const chosen = sel.textContent.trim();
      const correct = current.word;
      const isCorrect = chosen === correct;
      explainBox.style.display = "block";
      optionsEl.querySelectorAll(".option").forEach(o => o.style.pointerEvents = "none");

      if (isCorrect) {
        explainBox.textContent = `✅ Correct — ${current.word}: ${current.definition}`;
        correctSet.add(current.word);
        localStorage.setItem("satCorrectWords", JSON.stringify([...correctSet]));
        updateScore();
        nextBtn.style.display = "inline-block";
        submitBtn.style.display = "none";
      } else {
        explainBox.innerHTML = `❌ Incorrect — Correct: <b>${current.word}</b><br><br><b>Definitions:</b><br>`;
        document.querySelectorAll(".option").forEach(opt => {
          const w = masterList.find(e => e.word === opt.textContent);
          if (w) {
            const def = w.definition;
            explainBox.innerHTML += `<div><b>${w.word}</b>: ${def}</div>`;
          }
        });
        nextBtn.style.display = "inline-block";
        submitBtn.style.display = "none";
        pool.push(current);
      }
    };

    nextBtn.onclick = () => nextQuestion();

    loadWords();
  </script>
</body>
</html>

</div>
