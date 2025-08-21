---
layout: base
title: I'm Anwita Bandaru
hide: true
---

Hi! My name is Anwita Bandaru

### Development Environment

> Coding starts with tools, explore these tools and procedures with a click.

<div style="display: flex; flex-wrap: wrap; gap: 10px;">
    <a href="https://github.com/Open-Coding-Society/student">
        <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
    </a>
    <a href="https://open-coding-society.github.io/student">
        <img src="https://img.shields.io/badge/GitHub%20Pages-327FC7?style=for-the-badge&logo=github&logoColor=white" alt="GitHub Pages">
    </a>
    <a href="https://kasm.nighthawkcodingsociety.com/">
        <img src="https://img.shields.io/badge/KASM-0078D4?style=for-the-badge&logo=kasm&logoColor=white" alt="KASM">
    </a>
    <a href="https://vscode.dev/">
        <img src="https://img.shields.io/badge/VSCode-007ACC?style=for-the-badge&logo=visual-studio-code&logoColor=white" alt="VSCode">
    </a>
</div>

<br>

### Class Progress

> Here is my progress through coding, click to see these online

<div style="display: flex; flex-wrap: wrap; gap: 10px;">
    <a href="{{site.baseurl}}/snake" style="text-decoration: none;">
        <div style="background-color: #a26360; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
            Snake Game
        </div>
    </a>
    <a href="{{site.baseurl}}/turtle" style="text-decoration: none;">
        <div style="background-color: #a26360; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
            Turtle
        </div>
    </a>
</div>

<br>

<!-- Contact Section -->
### Get in Touch

> Feel free to reach out if you'd like to collaborate or learn more about our work.

<p style="color: #a26360;">Open Coding Society: <a href="https://opencodingsociety.com" style="color: #a26360; text-decoration: underline;">Socials</a></p>

Click the button below for confetti:

{% include confetti.html %}
<br>

<!-- Cat Walk Animation Section -->
<button id="cat-walk-btn" style="background-color: #a26360; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold; margin-top: 20px;">Make Cat Walk!</button>
<div id="cat-container" style="position: relative; height: 200px; width: 100%; overflow: hidden; border: 2px dashed #a26360;">
    <img id="cat-img" src="https://battlecats.club/en/series/battlecats/img/game_chara01.png" alt="Cat" style="position: absolute; left: -200px; top: 10px; height: 180px; transition: left 4s linear; background: #fffbe6;" />
</div>
<script>
document.getElementById('cat-walk-btn').onclick = function() {
    var cat = document.getElementById('cat-img');
    cat.style.left = '-200px'; // Reset position
    setTimeout(function() {
        cat.style.left = (window.innerWidth - 200) + 'px';
    }, 100);
    setTimeout(function() {
        cat.style.left = '-200px'; // Hide after walk
    }, 4100);
};
</script>