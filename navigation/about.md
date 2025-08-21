---
layout: post
title: About
permalink: /about/
comments: true
---

## As a conversation Starter

Here are some places I have lived.

<comment>
Flags are made using Wikipedia images
</comment>

<style>
    /* Style looks pretty compact, 
       - grid-container and grid-item are referenced the code 
    */
    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); /* Dynamic columns */
        gap: 10px;
    }
    .grid-item {
        text-align: center;
    }
    .grid-item img {
        width: 100%;
        height: 100px; /* Fixed height for uniformity */
        object-fit: contain; /* Ensure the image fits within the fixed height */
    }
    .grid-item p {
        margin: 5px 0; /* Add some margin for spacing */
    }

    .image-gallery {
        display: flex;
        flex-wrap: nowrap;
        overflow-x: auto;
        gap: 10px;
        }

    .image-gallery img {
        max-height: 150px;
        object-fit: cover;
        border-radius: 5px;
    }
</style>

<!-- This grid_container class is used by CSS styling and the id is used by JavaScript connection -->
<div class="grid-container" id="grid_container">
    <!-- content will be added here by JavaScript -->
</div>

<script>
    // 1. Make a connection to the HTML container defined in the HTML div
    var container = document.getElementById("grid_container"); // This container connects to the HTML div

    // 2. Define a JavaScript object for our http source and our data rows for the Living in the World grid
    var living_in_the_world = [
        {"img": "https://upload.wikimedia.org/wikipedia/commons/0/01/Flag_of_California.svg", "greeting": "Hey, like-", "description": "California - SUNNY DAYS"},
        {"img": "https://upload.wikimedia.org/wikipedia/commons/4/41/Flag_of_India.svg", "greeting": "Namaste", "description": "India - family roots"}
    ];

    // 3a. Consider how to update style count for size of container
    // The grid-template-columns has been defined as dynamic with auto-fill and minmax

    // 3b. Build grid items inside of our container for each row of data
    for (const location of living_in_the_world) {
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";
        var img = document.createElement("img");
        img.src = location.img;
        img.alt = location.description;
        var description = document.createElement("p");
        description.textContent = location.description;
        var greeting = document.createElement("p");
        greeting.textContent = location.greeting;
        gridItem.appendChild(img);
        gridItem.appendChild(description);
        gridItem.appendChild(greeting);
        container.appendChild(gridItem);
    }
</script>

### Journey through Life

Here is what I did at those places

- 🏫 I lived in San Diego since birth, going to Monterey Elementary School in 4S Ranch
- 🏫 Middle and High School in 4S Ranch (CA), Current Junior at Del Norte Highschool
- 💃I completed my Dance Arangetram in the summer of 2025 after 9 years of dance
- 🎓 Part of the Del Norte Varsity Golf Team 
- 🧫 Part of the DNHS iGEM team and work with the Yeo Lab at UCSD
- 🍵My dream job is to join own a matcha cafe and have a pet samoyed.

<style>
  .receipt-container {
    position: relative;
    margin: 20px 0;
  }

  .receipt-btn {
    background-color: #576e35ff; /* matcha green */
    color: white;
    padding: 10px 20px;
    border-radius: 8px;
    font-weight: bold;
    cursor: pointer;
    border: none;
    transition: background 0.2s ease;
  }

  .receipt-btn:hover {
    background-color: #576e35ff;
  }

  .receipt {
    max-height: 0;
    overflow: hidden;
    background: #fff;
    color: #333;
    font-family: monospace;
    border: 2px dashed #ccc;
    border-radius: 6px;
    margin-top: 10px;
    padding: 0 15px;
    width: 220px;
    transition: max-height 0.6s ease;
  }

  .receipt.open {
    max-height: 500px; /* enough room to expand */
    padding: 15px;
  }

  .receipt h4 {
    margin: 0 0 10px 0;
    text-align: center;
    border-bottom: 1px dashed #aaa;
    padding-bottom: 5px;
  }

  .receipt p {
    margin: 4px 0;
  }

  .receipt .total {
    margin-top: 10px;
    border-top: 1px dashed #aaa;
    padding-top: 5px;
    text-align: right;
    font-weight: bold;
  }
</style>

<div class="receipt-container">
  <button class="receipt-btn" onclick="toggleReceipt()">🍵 Reveal My Matcha Order</button>
  <div class="receipt" id="receipt">
    <h4>Matcha Order</h4>
    <p>Drink: Iced Matcha Latte</p>
    <p>Sweetness: 50% Sugar</p>
    <p>Ice: Light Ice</p>
    <p>Size: Grande</p>
    <div class="total">Total: $4.50</div>
  </div>
</div>

<script>
  function toggleReceipt() {
    const receipt = document.getElementById("receipt");
    receipt.classList.toggle("open");
  }
</script>

### Culture, Family, and Fun

Everything for me, revolves around my friends and family. 

- I am 100% Indian but my dad is from North India and my mom is from South India
- I have an older sister named Aditi. People say we look alike, but no one in my family thinks so. 
- I have 6 cousins and I'm the youngest in my extended family. I'm also the only left handed person in my whole family. 
- My favorite show is Money Heist, but I don't watch a lot of TV. My favorite character is Tigger from Winnie the Pooh
- In my free time, I enjoy listening to music and going to local cafes with my friends!🧋☕ 

<h3>Here's some of my Favorite Music</h3>
<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/4QhWbupniDd44EDtnh2bFJ?utm_source=generator" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
<iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/track/0QyJXG36Q3Kta662XS8GhY?utm_source=generator" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>

<comment>
Gallery of Pics, scroll to the right for more ...
</comment>
<div class="image-gallery">
  <img src="{{site.baseurl}}/images/about/missionary.jpg" alt="Image 1">
  <img src="{{site.baseurl}}/images/about/john_tamara.jpg" alt="Image 2">
  <img src="{{site.baseurl}}/images/about/tamara_fam.jpg" alt="Image 3">
  <img src="{{site.baseurl}}/images/about/surf.jpg" alt="Image 4">
  <img src="{{site.baseurl}}/images/about/john_lora.jpg" alt="Image 5">
  <img src="{{site.baseurl}}/images/about/lora_fam.jpg" alt="Image 6">
  <img src="{{site.baseurl}}/images/about/lora_fam2.jpg" alt="Image 7">
  <img src="{{site.baseurl}}/images/about/pj_party.jpg" alt="Image 8">
  <img src="{{site.baseurl}}/images/about/trent_family.png" alt="Image 9">
  <img src="{{site.baseurl}}/images/about/claire.jpg" alt="Image 10">
  <img src="{{site.baseurl}}/images/about/grandkids.jpg" alt="Image 11">
  <img src="{{site.baseurl}}/images/about/farm.jpg" alt="Image 12">
</div>
