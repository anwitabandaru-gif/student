---
permalink: /write-up/
---
# AP Computer Science Principles
## Create Performance Task: Media Bias Sorting Game
### Component C: Personalized Project Reference

---

## Program Overview

### Program Purpose
An educational game that teaches users to identify media bias by sorting news outlets into Left, Center, or Right political categories, helping students develop critical thinking skills for evaluating news sources.

### Key Program Components

#### Input
- **User drag-and-drop actions**: Moving media outlet logo images between Left, Center, and Right bins
- **Button clicks**: Reset game, submit score, autofill (testing mode)
- **Stored data**: Previously saved image placements from localStorage

#### Output
- **Visual feedback modal**: Displays incorrectly placed outlets with names, current bin location, and thumbnails
- **Timer display**: Shows elapsed time in MM:SS format during gameplay
- **Leaderboard**: Top 5 players with usernames and completion times
- **Success modal**: Congratulatory message upon correct completion

#### List (Data Collection)
```javascript
const imageFiles = [
    { src: "atlanticL.png", company: "Atlantic", bin: "Left" },
    { src: "cnnL.png", company: "CNN", bin: "Left" },
    { src: "foxR.png", company: "Fox News", bin: "Right" },
    { src: "bbcC.png", company: "BBC", bin: "Center" },
    // ... 26 more media outlets (30 total)
];
```
**Purpose**: Stores all media outlet data (image filename, company name, correct bias category) in a single array structure instead of 90 separate variables.

#### Student-Developed Procedure
```javascript
function autofillImageGame(showAlert) { 
    // Automatically places all images in their correct bins
    // and optionally shows feedback based on the parameter
}
```
**Parameter:** `showAlert` (boolean) - Controls whether to display alert feedback  
**Return Type:** None (void)  
**Contains:** Sequencing, selection, and iteration

---

## Procedure

### i. Student-Developed Procedure

```javascript
// Student-developed procedure: autofillImageGame(showAlert)
// Location: Mediachat.md, line 582
// This procedure automatically places all images in their correct bins
// and optionally displays feedback to the user

function autofillImageGame(showAlert = false) {
    // SEQUENCING: Clear all bins first
    document.querySelectorAll('.bin-content').forEach(el => el.innerHTML = '');
    
    // Get all image elements and initialize counter
    const imgs = Array.from(document.querySelectorAll('img.image'));
    let correctCount = 0;
    const data = loadData();
    data.gameState = data.gameState || {};

    // ITERATION: Process each image
    imgs.forEach(img => {
        // Get the correct bin for this image
        const target = img.dataset.bin;
        const id = img.dataset.id;
        
        // SELECTION: Find the matching bin element
        const bin = Array.from(document.querySelectorAll('.bin'))
            .find(b => b.dataset.bin === target);
        
        if (bin) {
            // Place image in correct bin
            bin.querySelector('.bin-content').appendChild(img);
            img.style.opacity = '1';
            img.style.cursor = 'grab';
            placedImages.add(id);
            data.gameState[id] = target; // Persist to storage
            correctCount++;
        }
    });

    saveData(data);
    
    // SELECTION: Show alert based on parameter
    if (showAlert) {
        alert(`Autofill placed ${correctCount} images into their correct bins.`);
    }
}
```

### ii. Procedure Calls

```javascript
// Called when user clicks autofill button (Mediachat.md, line 690)
// Passes TRUE to show alert feedback to the user
const autofillBtn = document.getElementById('autofill-images');
if (autofillBtn) {
    autofillBtn.addEventListener('click', () => {
        console.log("✨ Autofill clicked");
        autofillImageGame(true);  // Parameter: showAlert = true
    });
}
```

**How the parameter affects functionality:**
- When `showAlert = true`: Displays an alert message showing how many images were placed
- When `showAlert = false`: Silently places images without any user notification
- The parameter directly controls the `if (showAlert)` conditional at the end of the procedure

---

## List

### i. Data Storage in List

```javascript
// Master list of all media outlets (Mediachat.md, line 178)
const imageFiles = [
    { src: "atlanticL.png", company: "Atlantic", bin: "Left" },
    { src: "buzzfeedL.png", company: "Buzzfeed", bin: "Left" },
    { src: "cnnL.png", company: "CNN", bin: "Left" },
    { src: "epochR.png", company: "Epoch Times", bin: "Right" },
    { src: "forbesC.png", company: "Forbes", bin: "Center" },
    { src: "hillC.png", company: "The Hill", bin: "Center" },
    { src: "nbcL.png", company: "NBC", bin: "Left" },
    { src: "newsweekC.png", company: "Newsweek", bin: "Center" },
    { src: "nytL.png", company: "NY Times", bin: "Left" },
    { src: "voxL.png", company: "Vox", bin: "Left" },
    { src: "wtR.png", company: "Washington Times", bin: "Right" },
    { src: "bbcC.png", company: "BBC", bin: "Center" },
    { src: "callerR.png", company: "The Daily Caller", bin: "Right" },
    { src: "dailywireR.png", company: "Daily Wire", bin: "Right" },
    { src: "federalistR.png", company: "Federalist", bin: "Right" },
    { src: "foxR.png", company: "Fox News", bin: "Right" },
    { src: "marketwatchC.png", company: "MarketWatch", bin: "Center" },
    { src: "newsmaxR.png", company: "Newsmax", bin: "Right" },
    { src: "nprL.png", company: "NPR", bin: "Left" },
    { src: "reutersC.png", company: "Reuters", bin: "Center" },
    { src: "wsjC.png", company: "Wall Street Journal", bin: "Center" },
    { src: "abcL.png", company: "ABC", bin: "Left" },
    { src: "timeL.png", company: "Time", bin: "Left" },
    { src: "yahooL.png", company: "Yahoo News", bin: "Left" },
    { src: "newsnationC.png", company: "News Nation", bin: "Center" },
    { src: "reasonC.png", company: "Reason News", bin: "Center" },
    { src: "sanC.png", company: "SAN News", bin: "Center" },
    { src: "nypR.png", company: "New York Post", bin: "Right" },
    { src: "upwardR.png", company: "Upward News", bin: "Right" },
    { src: "cbnR.png", company: "CBN", bin: "Right" }
];
```

### ii. Using the List Data

```javascript
// Creating randomly selected subset (Mediachat.md, line 330)
const leftImages = imageFiles.filter(img => img.bin === "Left");
const centerImages = imageFiles.filter(img => img.bin === "Center");
const rightImages = imageFiles.filter(img => img.bin === "Right");

selectedImages = [
    ...getRandomSubset(leftImages, 7),
    ...getRandomSubset(centerImages, 7),
    ...getRandomSubset(rightImages, 7)
].sort(() => 0.5 - Math.random());

// Validating placements using the list (Mediachat.md, line 630)
let incorrectImages = [];
document.querySelectorAll('.bin').forEach(bin => {
    bin.querySelectorAll('.image').forEach(img => {
        if (img.dataset.bin !== bin.dataset.bin) {
            incorrectImages.push({
                name: img.dataset.company,
                currentBin: bin.dataset.bin,
                src: img.src
            });
        }
    });
});
```

---

## End-of-Course Exam Written Responses

### Written Response 1: Program Design, Function, and Purpose

**Learning Objectives:** CRD-2.A, CRD-2.B, CRD-2.C, CRD-2.D, CRD-2.E, CRD-2.F, CRD-2.G

#### a) Describe the purpose of your computing innovation.

The program teaches users to identify media bias by categorizing news outlets into Left, Center, or Right bins, helping students develop critical thinking skills for evaluating news sources.

#### b) Describe the functionality of the `initGame()` procedure.

`initGame()` resets the game state, randomly selects 21 media outlets (7 from each political category), displays them as draggable images, and restores any previously saved placements from localStorage.

#### c) Identify one input to your program.

User drag-and-drop actions when moving media outlet images into Left, Center, or Right bins.

#### d) Identify one output produced by your program.

A modal feedback display showing incorrectly placed outlets with their names, current bin location, and thumbnails when the user submits an incorrect answer.

```javascript
// Output example: showIncorrectFeedback modal
const imageGrid = incorrectImages.map(img => 
    `
        
        
            ${img.name}
            Currently in: ${img.currentBin}
        
    `
).join('');
```

#### e) Describe one aspect of the user interface design.

The interface uses a collapsible "Spectrum of Bias" slider that lets users explore different bias levels (Far Left to Far Right) with visual colors, emojis, and descriptions before attempting the sorting task.

#### f) Describe the purpose of the drag-and-drop event handlers in your code.

```javascript
// Enables image movement between bins and starts timer on first interaction
img.addEventListener('dragstart', (e) => {
    if (!gameStarted) {
        gameStarted = true;
        timerHandle = startTimer();  // Start timing on first drag
    }
    e.target.classList.add('dragging');
    e.dataTransfer.setData('text/plain', e.target.dataset.id);
});
```

---

### Written Response 2(a): Algorithm Development

**Learning Objectives:** CRD-2.B, AAP-2.E.b, AAP-2.F.b, AAP-2.H.b, AAP-2.J, AAP-2.K.b, AAP-2.L, AAP-2.M.a, AAP-2.M.b

#### a) Explain how the random selection algorithm in `initGame()` functions.

The algorithm filters `imageFiles` by bias category, uses `getRandomSubset()` to select 7 outlets from each category, combines them into a 21-item array, and randomizes the final order.

```javascript
const leftImages = imageFiles.filter(img => img.bin === "Left");
const centerImages = imageFiles.filter(img => img.bin === "Center");
const rightImages = imageFiles.filter(img => img.bin === "Right");

selectedImages = [
    ...getRandomSubset(leftImages, 7),
    ...getRandomSubset(centerImages, 7),
    ...getRandomSubset(rightImages, 7)
].sort(() => 0.5 - Math.random());
```

#### b) Evaluate this relational operator: What does `data.meta.roundImages.length === 21` check?

It checks whether the saved round contains exactly 21 images to determine if the previous game state is valid for reuse.

#### c) Determine the result of this conditional statement:

```javascript
if (!selectedImages) {
    selectedImages = [ /* create new array */ ];
}
```

If `selectedImages` is `null`, `undefined`, or `false`, the condition evaluates to `true` and creates a new random selection. Otherwise, it uses the existing selection.

#### d) How many times does this iteration execute?

```javascript
selectedImages.forEach((file) => {
    const card = createImageCard(file);
    imagesArea.appendChild(card);
});
```

Executes exactly **21 times** (the length of `selectedImages`).

#### e) Compare these two algorithms - do they produce the same result?

**Algorithm 1 (Current):**
```javascript
const leftImages = imageFiles.filter(img => img.bin === "Left");
const centerImages = imageFiles.filter(img => img.bin === "Center");
const rightImages = imageFiles.filter(img => img.bin === "Right");
```

**Algorithm 2 (Alternative):**
```javascript
let leftImages = [], centerImages = [], rightImages = [];
for (let i = 0; i < imageFiles.length; i++) {
    if (imageFiles[i].bin === "Left") leftImages.push(imageFiles[i]);
    else if (imageFiles[i].bin === "Center") centerImages.push(imageFiles[i]);
    else if (imageFiles[i].bin === "Right") rightImages.push(imageFiles[i]);
}
```

**Yes**, both produce the same result - three arrays categorized by bias.

#### f) Describe an algorithm modification you made.

I combined the existing `getRandomSubset()` helper function with array spread operators to create a more concise random selection algorithm.

---

### Written Response 2(b): Errors and Testing

**Learning Objectives:** CRD-2.I.a, CRD-2.I.b, CRD-2.J

#### a) Identify an error in this code:

```javascript
selectedImages = null;
selectedImages.forEach((file) => {
    const card = createImageCard(file);
    imagesArea.appendChild(card);
});
```

**Error:** `TypeError: Cannot read property 'forEach' of null`

#### b) Correct the error:

```javascript
// Add null check before forEach
if (selectedImages && Array.isArray(selectedImages)) {
    selectedImages.forEach((file) => {
        const card = createImageCard(file);
        imagesArea.appendChild(card);
    });
}
```

#### c) Identify test inputs and expected outputs:

| **Input** | **Expected Output** |
|-----------|---------------------|
| User drags CNN logo to "Left" bin | Image stays in bin, saved to localStorage with `gameState[id] = "Left"` |
| User drags Fox News to "Left" bin then submits | Modal appears showing "Fox News - Currently in: Left" as incorrect |
| User places all 21 images correctly then submits | Timer stops, success modal appears, score saved with username and time |

---

### Written Response 2(c): Data and Procedural Abstraction

**Learning Objectives:** AAP-1.D.a, AAP-1.D.b, AAP-2.O.a, AAP-2.O.b, AAP-3.B

#### a) How does the `imageFiles` list manage complexity?

The list stores all 30 media outlets with their properties in one structure instead of requiring 30 separate variables (e.g., `cnn_src`, `cnn_company`, `cnn_bin`, `fox_src`, `fox_company`, `fox_bin`, etc.).

**Without list (high complexity):**
```javascript
const cnn_src = "cnnL.png";
const cnn_company = "CNN";
const cnn_bin = "Left";
const fox_src = "foxR.png";
const fox_company = "Fox News";
const fox_bin = "Right";
// ... 28 more outlets × 3 variables = 90 variables total!
```

**With list (low complexity):**
```javascript
const imageFiles = [
    { src: "cnnL.png", company: "CNN", bin: "Left" },
    { src: "foxR.png", company: "Fox News", bin: "Right" },
    // ... 28 more objects
];
```

#### b) Write an iteration to traverse the `incorrectImages` list:

```javascript
let incorrectImages = [];
document.querySelectorAll('.bin').forEach(bin => {
    bin.querySelectorAll('.image').forEach(img => {
        if (img.dataset.bin !== bin.dataset.bin) {
            incorrectImages.push({
                name: img.dataset.company,
                currentBin: bin.dataset.bin,
                src: img.src
            });
        }
    });
});
```

#### c) Determine the result of this list traversal algorithm:

```javascript
const leftImages = imageFiles.filter(img => img.bin === "Left");
```

**Result:** A new array containing only the media outlets where `bin === "Left"` (CNN, NBC, NPR, NY Times, Vox, Atlantic, Buzzfeed, ABC, Time, Yahoo News) - 10 elements.

#### d) How does the `initGame()` procedure manage complexity?

`initGame()` encapsulates 9 separate tasks (clearing state, stopping timer, filtering categories, loading saved data, creating random selection, creating cards, restoring placements, saving state, updating display) into one reusable procedure that can be called from multiple places (page load, reset button, game completion) instead of duplicating all that code.

**Without procedure abstraction:**
```javascript
// Reset button - duplicate all code
resetBtn.addEventListener('click', () => {
    imagesArea.innerHTML = '';
    document.querySelectorAll('.bin-content').forEach(el => el.innerHTML = '');
    placedImages.clear();
    // ... 50+ more lines
});

// Page load - duplicate all code again
window.onload = () => {
    imagesArea.innerHTML = '';
    document.querySelectorAll('.bin-content').forEach(el => el.innerHTML = '');
    placedImages.clear();
    // ... 50+ more lines duplicated
};
```

**With procedure abstraction:**
```javascript
resetBtn.addEventListener('click', () => { initGame(); });
window.onload = () => { initGame(); };
```