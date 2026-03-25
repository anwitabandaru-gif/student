---
layout: base
title: I'm [Your Full Name]
hide: true
show_reading_time: false
---

Hi! My name is Anwita Bandaru

### Development Environment

> Coding starts with tools, explore these tools and procedures with a click.

<div style="display: flex; flex-wrap: wrap; gap: 10px;">
    <a href="https://opencodingsociety.com" style="text-decoration: none; display: inline-flex; align-items: center; gap: 8px; padding: 10px 14px; border: 1px solid #FA8072; border-radius: 6px; font-weight: 700;">
        <img src="{{ '/favicon.ico' | relative_url }}" alt="OCS logo" style="width: 16px; height: 16px;">
        OCS
    </a>
    <a href="https://github.com/Open-Coding-Society/portfolio" style=" text-decoration: none; display: inline-flex; align-items: center; gap: 8px; padding: 10px 14px; border: 1px solid #FFF; border-radius: 6px; font-weight: 700;">
        <img src="https://github.githubassets.com/favicons/favicon.svg" alt="GitHub logo" style="width: 16px; height: 16px;">
        GitHub
    </a>
    <a href="https://vscode.dev/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 8px; padding: 10px 14px; border: 1px solid #007ACC; border-radius: 6px; font-weight: 700;">
        <img src="https://vscode.dev/favicon.ico" alt="VSCode logo" style="width: 16px; height: 16px;">
        VSCode.dev
    </a>
</div>

<br>

### Class Progress

> Here is my progress through coding, click to see these online

<div style="display: flex; flex-wrap: wrap; gap: 10px;">
    <a href="{{site.baseurl}}/snake" style="text-decoration: none;">
        <div style="background-color: #00FF00; color: black; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
            Snake Game
        </div>
    </a>
    <a href="{{site.baseurl}}/turtle" style="text-decoration: none;">
        <div style="background-color: #FF0000; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
            Turtle
        </div>
    </a>
</div>

<br>

<!-- Contact Section -->
### Get in Touch

> Feel free to reach out if you'd like to collaborate or learn more about our work.

<p style="color: #2A7DB1;">Open Coding Society: <a href="https://opencodingsociety.com" style="color: #2A7DB1; text-decoration: underline;">Socials</a></p>

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