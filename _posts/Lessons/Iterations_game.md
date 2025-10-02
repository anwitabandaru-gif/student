---
title: Iterations Game — Learn loops (JavaScript & Python)
layout: base
permalink: /interations_game/
---

# Iterations Game — Multiple Choice (JavaScript / Python)

Choose a language, read the snippet, and pick the correct output or behavior. You will get immediate "Correct" or "Incorrect" feedback and an explanation.

<div id="quiz">
  <div style="margin-bottom:10px;">
    <label><input type="radio" name="lang" value="js" checked> JavaScript</label>
    <label style="margin-left:10px;"><input type="radio" name="lang" value="py"> Python</label>
  </div>

  <div id="card" style="border:1px solid #ccc;padding:12px;border-radius:6px;background:#fafafa;">
    <h3 id="qnum">Question 1</h3>
    <pre id="code" style="background: 
    #272822;color: #f8f8f2;padding:10px;border-radius:4px;overflow:auto;"></pre>
    <div id="choices"></div>
    <div style="margin-top:8px;">
      <button id="submit">Submit</button>
      <button id="next" style="margin-left:8px;">Next</button>
      <button id="explain" style="margin-left:8px;">Show Explanation</button>
    </div>
    <p id="result" style="font-weight:bold;margin-top:8px;"></p>
    <div id="explainText" style="margin-top:6px;color:#333;"></div>
  </div>
</div>

<script>
(function(){
  const questions = [
    {
      codeJS: "for (let i = 0; i < 3; i++) {\n  console.log(i);\n}",
      codePy: "for i in range(3):\n    print(i)",
      choices: ["0 1 2", "1 2 3", "0 1 2 3", "Error"],
      answer: 0,
      explain: "Loops start at 0 and run while i < 3, producing 0,1,2."
    },
    {
      codeJS: "let i = 0;\nwhile (i < 3) {\n  i += 2;\n  console.log(i);\n}",
      codePy: "i = 0\nwhile i < 3:\n    i += 2\n    print(i)",
      choices: ["0 2", "2 4", "2", "0 1 2"],
      answer: 1,
      explain: "Each loop iteration increases i by 2 then prints. Values printed: 2 then 4."
    },
    {
      codeJS: "const arr = [1,2,3];\nfor (const x of arr) console.log(x * 2);",
      codePy: "for x in [1,2,3]:\n    print(x * 2)",
      choices: ["2 4 6", "1 2 3", "2,4,6,8", "Error"],
      answer: 0,
      explain: "Each element is multiplied by 2: 2,4,6."
    },
    {
      codeJS: "for (let i=0;i<5;i++){\n  if (i===2) break;\n  console.log(i);\n}",
      codePy: "for i in range(5):\n    if i == 2:\n        break\n    print(i)",
      choices: ["0 1", "0 1 2", "2 3 4", "0 1 2 3 4"],
      answer: 0,
      explain: "break stops the loop when i equals 2, so only 0 and 1 are printed."
    },
    {
      codeJS: "for (let i=0;i<4;i++){\n  if (i%2===0) continue;\n  console.log(i);\n}",
      codePy: "for i in range(4):\n    if i % 2 == 0:\n        continue\n    print(i)",
      choices: ["1 3", "0 2", "0 1 2 3", "0 1 3"],
      answer: 0,
      explain: "continue skips even i (0 and 2), so only odd values 1 and 3 are printed."
    }
  ];

  let idx = 0;
  let selected = null;

  const codeEl = document.getElementById('code');
  const choicesEl = document.getElementById('choices');
  const resultEl = document.getElementById('result');
  const explainEl = document.getElementById('explainText');
  const qnumEl = document.getElementById('qnum');

  function getLang() {
    return document.querySelector('input[name="lang"]:checked').value;
  }

  function render() {
    const q = questions[idx];
    qnumEl.textContent = "Question " + (idx+1);
    const lang = getLang();
    codeEl.textContent = (lang === 'js') ? q.codeJS : q.codePy;
    // render choices
    choicesEl.innerHTML = '';
    q.choices.forEach((c, i) => {
      const id = 'opt' + i;
      const wrapper = document.createElement('div');
      wrapper.style.marginTop = '6px';
      wrapper.innerHTML = `<label><input type="radio" name="choice" value="${i}" id="${id}"> ${escapeHtml(c)}</label>`;
      choicesEl.appendChild(wrapper);
    });
    resultEl.textContent = '';
    explainEl.textContent = '';
    selected = null;
    document.querySelectorAll('input[name="choice"]').forEach(r => r.addEventListener('change', e=> selected = parseInt(e.target.value)));
  }

  function escapeHtml(s){ return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;'); }

  document.getElementById('submit').addEventListener('click', ()=>{
    if (selected === null) { resultEl.textContent = "Pick an answer first."; resultEl.style.color = "darkorange"; return; }
    const q = questions[idx];
    if (selected === q.answer) {
      resultEl.textContent = "Correct";
      resultEl.style.color = "green";
    } else {
      resultEl.textContent = "Incorrect";
      resultEl.style.color = "red";
    }
  });

  document.getElementById('next').addEventListener('click', ()=>{
    idx = (idx + 1) % questions.length;
    render();
  });

  document.getElementById('explain').addEventListener('click', ()=>{
    explainEl.textContent = questions[idx].explain;
  });

  document.querySelectorAll('input[name="lang"]').forEach(r=> r.addEventListener('change', render));

  // initial render
  render();
})();
</script>
