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

## Code Requirements Overview

Your code satisfies all requirements. Here's a breakdown:

---

### FUNCTION Requirement
**Location:** `autofillImageGame(showAlert)` function (Mediachat.md, line 582)

```javascript
function autofillImageGame(showAlert = false) {
    // Clear all bins
    document.querySelectorAll('.bin-content').forEach(el => el.innerHTML = '');
    
    const imgs = Array.from(document.querySelectorAll('img.image'));
    let correctCount = 0;
    const data = loadData();
    data.gameState = data.gameState || {};

    // Loop through each image
    imgs.forEach(img => {
        const target = img.dataset.bin;
        const id = img.dataset.id;
        
        // Find matching bin
        const bin = Array.from(document.querySelectorAll('.bin'))
            .find(b => b.dataset.bin === target);
        
        // If statement inside loop
        if (bin) {
            bin.querySelector('.bin-content').appendChild(img);
            img.style.opacity = '1';
            img.style.cursor = 'grab';
            placedImages.add(id);
            data.gameState[id] = target;
            correctCount++;
        }
    });

    saveData(data);
    
    // Parameter controls this conditional
    if (showAlert) {
        alert(`Autofill placed ${correctCount} images into their correct bins.`);
    }
}
```

**What this function does:**
- Clears all current image placements from the three bins (Left, Center, Right)
- Retrieves all media outlet images currently displayed on the page
- Loops through each image and determines its correct bin based on stored data
- Places each image into its correct category bin automatically
- Updates visual styling to show images are properly placed
- Saves all placements to localStorage for persistence
- Counts how many images were successfully placed
- **Parameter behavior:** When `showAlert` is true, displays a confirmation message with the count; when false, performs placement silently

**Function calls:**
```javascript
// Call with showAlert = true (shows alert)
autofillBtn.addEventListener('click', () => {
    autofillImageGame(true);
});

// Could also call with showAlert = false (no alert)
autofillImageGame(false);
```

---

### LOOP Requirement
**Location:** Inside `autofillImageGame()` function (Mediachat.md, line 591)

```javascript
// LOOP: Iterate through all images
imgs.forEach(img => {
    const target = img.dataset.bin;
    const id = img.dataset.id;
    
    // Find the correct bin for this image
    const bin = Array.from(document.querySelectorAll('.bin'))
        .find(b => b.dataset.bin === target);
    
    // IF STATEMENT INSIDE LOOP
    if (bin) {
        // Place image in correct bin
        bin.querySelector('.bin-content').appendChild(img);
        img.style.opacity = '1';
        img.style.cursor = 'grab';
        placedImages.add(id);
        data.gameState[id] = target;
        correctCount++;
    }
});
```

**What this loop does:**
- Processes each media outlet image one at a time
- Extracts the correct bin category from the image's data attribute (e.g., "Left", "Center", or "Right")
- Searches through all three bins on the page to find the one matching the target category
- **Conditional logic:** If a matching bin is found, moves the image element into that bin's container
- Updates the image's visual appearance (opacity and cursor) to indicate it's interactive
- Tracks the image ID in the `placedImages` set to mark it as placed
- Stores the placement in the game state object for saving to localStorage
- Increments the counter to track how many images were successfully placed
- **Safety check:** If no matching bin exists, skips that image without crashing

 Both the parameter-controlled conditional (`if (showAlert)`) AND the loop with if statement (`imgs.forEach` with `if (bin)`) are inside the same function: `autofillImageGame(showAlert)`
---

Here's the LIST section updated to use the actual `fetchLeaderboard()` function from `Mediachat.md`:

---

### LIST/GROUP Requirement
**Location:** `fetchLeaderboard()` function in `Mediachat.md`

```javascript
// BACKEND:
leaderboard = []
for rank, score in enumerate(scores, start=1):
    entry = score.read()   # Returns { id, username, time, created_at }
    entry['rank'] = rank   # Adds rank to each object
    leaderboard.append(entry)

return leaderboard, 200

```

```javascript
// FRONTEND:
async function fetchLeaderboard() {
    const tbody = document.getElementById('leaderboard-body');
    try {
        const response = await fetch(pythonURI + '/api/media/leaderboard?limit=5');
        if (!response.ok) throw new Error('Failed to fetch leaderboard');
        
        const data = await response.json();
        
        tbody.innerHTML = '';

        // ITERATION with SELECTION: Loop through every entry in the list
        data.forEach((entry, index) => {
            const row = tbody.insertRow();

            row.insertCell().textContent = entry.rank || (index + 1);

            row.insertCell().textContent = entry.username || 'Unknown';

            const timeInSeconds = entry.time || 0;
            const minutes = Math.floor(timeInSeconds / 60);
            const seconds = timeInSeconds % 60;
            row.insertCell().textContent = `${minutes}:${seconds.toString().padStart(2, '0')}`;
        });

    } catch (err) {
        console.error('Error fetching leaderboard:', err);
        tbody.innerHTML = '<tr><td colspan="3">Unable to load leaderboard</td></tr>';
    }
}

setInterval(fetchLeaderboard, 30000);
```

**What this list does:**
- Stores the top 5 leaderboard entries returned by the backend API, where each object contains a player's rank, username, completion time in seconds, score ID, and submission date
- Built on the backend by looping through database query results and appending each entry to the list with its rank
- Sent to the frontend via the API and used to drive the entire leaderboard table display

---

# End-of-Course Exam Written Responses

## Written Response 1: Program Design, Function, and Purpose

### a) Purpose/Function

**Program Purpose:**
The program teaches users to identify media bias by categorizing news outlets into Left, Center, or Right political bins, helping students develop critical thinking skills for evaluating news sources.

**Input(s):**
- User drag-and-drop actions moving media outlet logo images between bins
- Button clicks (Reset, Submit Score, Autofill)
- Previously saved image placements from localStorage

**Output(s):**
- Visual feedback modal showing incorrectly placed outlets with names, current bin, and thumbnails
- Timer display showing elapsed time in MM:SS format
- Leaderboard displaying top 5 players with usernames and completion times
- Success modal with congratulatory message upon correct completion

**How the code functions:**
1. Randomly selects 21 media outlets (7 from each political category)
2. Displays outlets as draggable images that users sort into bins
3. Tracks user placements and saves them to localStorage
4. Validates placements against correct answers when user submits
5. Provides feedback and records completion time to leaderboard

```javascript
// Main game initialization
function initGame() {
    // Select 21 random outlets (7 Left, 7 Center, 7 Right)
    const leftImages = imageFiles.filter(img => img.bin === "Left");
    const centerImages = imageFiles.filter(img => img.bin === "Center");
    const rightImages = imageFiles.filter(img => img.bin === "Right");
    
    selectedImages = [
        ...getRandomSubset(leftImages, 7),
        ...getRandomSubset(centerImages, 7),
        ...getRandomSubset(rightImages, 7)
    ].sort(() => 0.5 - Math.random());
    
    // Create draggable cards for each outlet
    selectedImages.forEach((file) => {
        const card = createImageCard(file);
        imagesArea.appendChild(card);
    });
}
```

---

### b) Development Process: Challenge and Solution

**Problem:**
Players were losing their progress when accidentally refreshing the page or navigating away, which was frustrating because they had to restart the entire sorting process from scratch.

**How I addressed it:**
I implemented localStorage persistence that automatically saves each image placement as the user drags it. When the page reloads, the game restores all previous placements.

```javascript
// Save placement immediately when image is dropped
bin.addEventListener('drop', e => {
    e.preventDefault();
    const id = e.dataTransfer.getData('text/plain');
    const img = document.querySelector(`[data-id="${id}"]`);
    
    // Place image in bin
    bin.querySelector('.bin-content').appendChild(img);
    placedImages.add(id);
    
    // SOLUTION: Persist placement to localStorage
    const data = loadData();
    data.gameState = data.gameState || {};
    data.gameState[id] = bin.dataset.bin;  // Save which bin this image is in
    saveData(data);
});

// Restore placements on page load
function initGame() {
    
    // SOLUTION: Restore saved placements
    const data = loadData();
    document.querySelectorAll('img.image').forEach(img => {
        const id = img.dataset.id;
        const zone = data.gameState && data.gameState[id];
        if (zone) {
            const bin = document.querySelector(`.bin[data-bin="${zone}"]`);
            if (bin) {
                bin.querySelector('.bin-content').appendChild(img);
                placedImages.add(id);
            }
        }
    });
}
```

**Result:** Players can now close the browser, refresh, or navigate away without losing their progress.

---

## Written Response 2(a): Algorithm - Procedure with List

### Student-Developed Procedure

**Procedure Name:** `autofillImageGame(showAlert)`  
**Location:** Mediachat.md, line 582

```javascript
function autofillImageGame(showAlert = false) {
    // Clear all bins
    document.querySelectorAll('.bin-content').forEach(el => el.innerHTML = '');
    
    const imgs = Array.from(document.querySelectorAll('img.image'));
    let correctCount = 0;
    const data = loadData();
    data.gameState = data.gameState || {};

    // ITERATION: Loop through each image
    imgs.forEach(img => {
        const target = img.dataset.bin;  // Get correct bin from list data
        const id = img.dataset.id;
        
        // Find matching bin
        const bin = Array.from(document.querySelectorAll('.bin'))
            .find(b => b.dataset.bin === target);
        
        // SELECTION: If statement inside loop
        if (bin) {
            bin.querySelector('.bin-content').appendChild(img);
            img.style.opacity = '1';
            img.style.cursor = 'grab';
            placedImages.add(id);
            data.gameState[id] = target;
            correctCount++;
        }
    });

    saveData(data);
    
    // SELECTION: Parameter controls conditional
    if (showAlert) {
        alert(`Autofill placed ${correctCount} images into their correct bins.`);
    }
}
```

### How it works:
1. **Clears current state:** Removes all images from bins to start fresh
2. **Retrieves all images:** Gets array of all media outlet image elements on page
3. **Iterates through images:** Loops through each outlet image one by one
4. **Finds correct bin:** For each image, reads its correct category from the `imageFiles` list
5. **Places image:** Moves the image element into the matching bin container
6. **Updates tracking:** Saves placement to localStorage and increments counter
7. **Conditional feedback:** Shows alert message only if `showAlert` parameter is true

### Purpose for Complexity:

**The `imageFiles` list:**
```javascript
const imageFiles = [
    { src: "atlanticL.png", company: "Atlantic", bin: "Left" },
    { src: "cnnL.png", company: "CNN", bin: "Left" },
    { src: "foxR.png", company: "Fox News", bin: "Right" },
    // ... 27 more outlets
];
```

**Without the list:**
```javascript
// Would need 90 separate variables (30 outlets × 3 properties)
const atlantic_src = "atlanticL.png";
const atlantic_company = "Atlantic";
const atlantic_bin = "Left";
const cnn_src = "cnnL.png";
const cnn_company = "CNN";
const cnn_bin = "Left";
// ... 84 more variables!

// And autofill would need 30 if-else statements:
if (id === "atlantic") target = "Left";
else if (id === "cnn") target = "Left";
else if (id === "fox") target = "Right";
// ... 27 more conditions!
```

**With the list:**
```javascript
// Single line retrieves correct bin from stored data
const target = img.dataset.bin;  // Data originally from imageFiles list
```

**Complexity reduction:**
- **Before:** 90 variables + 30 if-else statements = 120 lines of code
- **After:** 1 array + 1 line to access data = minimal complexity
- The list enables loop-based processing instead of hardcoding each outlet

---

## Written Response 2(b): Iteration and Selection

### Selection (If-Statements)

**Selection 1: Check if matching bin exists**
```javascript
if (bin) {
    bin.querySelector('.bin-content').appendChild(img);
    img.style.opacity = '1';
    img.style.cursor = 'grab';
    placedImages.add(id);
    data.gameState[id] = target;
    correctCount++;
}
```

**Purpose:**
- **Condition:** Checks if a bin matching the target category was found
- **True path:** Places image in bin, updates styling, saves placement, increments counter
- **False path:** Skips image without crashing (safety check)

---

**Selection 2: Parameter controls alert display**
```javascript
if (showAlert) {
    alert(`Autofill placed ${correctCount} images into their correct bins.`);
}
```

**What it does:**
- **Condition:** Checks if `showAlert` parameter is true
- **True path:** Displays confirmation alert with placement count
- **False path:** Performs autofill silently without user notification
- **Purpose:** This is how the parameter controls the procedure's behavior

---

### Iteration (Loops)

**Loop: Process each image**
```javascript
imgs.forEach(img => {
    const target = img.dataset.bin;
    const id = img.dataset.id;
    
    const bin = Array.from(document.querySelectorAll('.bin'))
        .find(b => b.dataset.bin === target);
    
    if (bin) {
        bin.querySelector('.bin-content').appendChild(img);
        img.style.opacity = '1';
        img.style.cursor = 'grab';
        placedImages.add(id);
        data.gameState[id] = target;
        correctCount++;
    }
});
```

**What it does:**
- **Iterates:** Processes each media outlet image one at a time
- **Extracts data:** Gets correct bin category from image's dataset
- **Searches:** Finds the bin element matching the target category
- **Conditional:** Only places image if matching bin exists (nested selection)
- **Updates state:** Tracks placement in set, saves to storage, counts successful placements

**Purpose:**
- Without the loop, would need to write this code 21 times (once per image)
- Loop enables processing variable number of images regardless of selection

---

## Written Response 2(c): Testing

### Two Different Procedure Calls with Different Results

**Test Call 1: With alert (showAlert = true)**
```javascript
// User clicks autofill button
autofillBtn.addEventListener('click', () => {
    autofillImageGame(true);
});
```

**Result:**
- All 21 images are placed in their correct bins
- Visual styling is updated (opacity set to 1, cursor set to grab)
- Placements are saved to localStorage
- Counter increments to 21
- **Alert is displayed:** "Autofill placed 21 images into their correct bins."
- User receives immediate visual confirmation


**Test Call 2: Without alert (showAlert = false)**
```javascript
// Silent autofill for automated testing
function runAutomatedTest() {
    initGame();
    autofillImageGame(false);  // No alert
    validatePlacements();
}
```

**Result:**
- All 21 images are placed in their correct bins
- Visual styling is updated (opacity set to 1, cursor set to grab)
- Placements are saved to localStorage
- Counter increments to 21
- **No alert is displayed** - function completes silently
- Automated testing can proceed without user interaction

---

### Comparison Table

| **Aspect** | **Call 1: `autofillImageGame(true)`** | **Call 2: `autofillImageGame(false)`** |
|------------|---------------------------------------|----------------------------------------|
| Images placed | 21 images → correct bins | 21 images → correct bins |
| Visual updates | Opacity & cursor updated | Opacity & cursor updated |
| localStorage | Placements saved | Placements saved |
| Counter | Incremented to 21 | Incremented to 21 |
| **Alert display** | **Shows alert message** | **No alert shown** |
| Use case | Manual user testing | Automated testing |

**Key Difference:**
The parameter directly controls the `if (showAlert)` conditional:
- When `true` → executes alert statement
- When `false` → skips alert statement

---