---
permalink: /write-up/
---
# AP Computer Science Principles
## Create Performance Task: Media Bias Sorting Game
### Component C: Personalized Project Reference

---

## Procedure

### i. Student-Developed Procedure

```javascript
// Student-developed procedure: initGame()
// Location: mainmodule.md, line 1023
// This procedure initializes the game state and displays randomly selected images

function initGame() {
    // SEQUENCING: Clear existing game state
    imagesArea.innerHTML = '';
    document.querySelectorAll('.bin-content').forEach(el => el.innerHTML = '');
    placedImages.clear();
    gameStarted = false;
    
    if (timerHandle) {
        timerHandle.stop();
        timerHandle = null;
    }
    
    if (timerDisplay) {
        timerDisplay.textContent = 'Time: 0:00';
    }

    const getRandomSubset = (arr, count) => {
        return [...arr]
            .sort(() => 0.5 - Math.random())
            .slice(0, count);
    };

    const leftImages = imageFiles.filter(img => img.bin === "Left");
    const centerImages = imageFiles.filter(img => img.bin === "Center");
    const rightImages = imageFiles.filter(img => img.bin === "Right");

    // ITERATION & SELECTION: Load or create selection
    const data = loadData();
    data.meta = data.meta || {};
    let selectedImages = null;
    
    if (Array.isArray(data.meta.roundImages) && 
        data.meta.roundImages.length === 21) {
        const idMap = new Map(imageFiles.map(f => 
            [slugify(f.company), f]));
        const files = data.meta.roundImages
            .map(id => idMap.get(id))
            .filter(Boolean);
        if (files.length === 21) {
            selectedImages = files;
        }
    }

    // SELECTION: Create new selection if needed
    if (!selectedImages) {
        selectedImages = [
            ...getRandomSubset(leftImages, 7),
            ...getRandomSubset(centerImages, 7),
            ...getRandomSubset(rightImages, 7)
        ].sort(() => 0.5 - Math.random());
        
        data.meta.roundImages = selectedImages.map(f => 
            slugify(f.company));
        saveData(data);
    }

    // ITERATION: Create and display image cards
    selectedImages.forEach((file) => {
        const card = createImageCard(file);
        imagesArea.appendChild(card);
    });

    // ITERATION: Restore saved placements
    document.querySelectorAll('img.image').forEach(img => {
        const id = img.dataset.id;
        const zone = data.gameState && data.gameState[id];
        if (zone) {
            const bin = document.querySelector(
                `.bin[data-bin="${zone}"]`);
            if (bin) {
                bin.querySelector('.bin-content')
                    .appendChild(img);
                placedImages.add(id);
            }
        }
    });
}
```

### ii. Procedure Calls

```javascript
// Called on page load (Mediachat.md, line 800)
window.onload = () => {
    console.log("Window fully loaded — starting game");
    fetchUser();
    initGame();
    fetchLeaderboard();
    setInterval(fetchLeaderboard, 30000);
};

// Called when user clicks reset button (Mediachat.md, line 680)
const resetBtn = document.getElementById('reset-btn');
if (resetBtn) {
    resetBtn.addEventListener('click', () => {
        console.log("Reset clicked");
        const ids = Array.from(
            document.querySelectorAll('img.image')
        ).map(i => i.dataset.id);
        clearGameStateForIds(ids);
        
        const data = loadData();
        if (data.meta && data.meta.roundImages) {
            delete data.meta.roundImages;
            saveData(data);
        }
        
        initGame();
    });
}

// Called after successful completion (Mediachat.md, line 735)
if (incorrectImages.length === 0) {
    const elapsed = timerHandle.stop();
    const username = window.currentPlayerUid || 'Guest';
    submitFinalTime(username, elapsed);
    showCongrats();
    initGame();
}
```

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

### Prompt 1: Program Design, Function, and Purpose

**Prompt:** *Identify an expected user of your program. Describe one way your program's design meets the needs of this user.*

**Expected user:** High school/college student learning media bias for research.

**Design feature:** Educational game with immediate feedback showing which outlets are incorrectly placed with modal displays, plus a visual spectrum slider explaining bias characteristics.

```javascript
// Feedback system that meets user needs
if (incorrectImages.length > 0) {
    showIncorrectFeedback(incorrectImages);  // Shows specific errors
    return;
}
```

---

### Prompt 2: Algorithm Development

**Prompt:** *Consider the first iteration statement included in the Procedure section of your Personalized Project Reference. Identify the number of times the body of your iteration statement will execute. Describe a condition or error that would cause your iteration statement to not terminate and cause an infinite loop. If no such condition or error exists, explain how the loop could be modified to cause an infinite loop.*

**Iteration count:** The loop executes exactly 21 times (length of selectedImages array).

**Infinite loop scenario:** If modified to use `while (i < selectedImages.length)` without incrementing `i++`, the condition would always be true.

```javascript
// CURRENT (terminates correctly):
selectedImages.forEach((file) => {
    const card = createImageCard(file);
    imagesArea.appendChild(card);
});

// MODIFIED (infinite loop):
let i = 0;
while (i < selectedImages.length) {
    imagesArea.appendChild(createImageCard(selectedImages[i]));
    // Missing i++ causes infinite loop
}
```

---

### Prompt 3: Errors and Testing

**Prompt:** *Consider the procedure included in part (i) of the Procedure section of your Personalized Project Reference. Describe a change to your procedure that will result in a run-time error. Explain why this change will result in a run-time error.*

**Error scenario:** Setting `selectedImages = null` then calling `selectedImages.forEach()` would crash with `TypeError: Cannot read property 'forEach' of null` because null has no methods.

| **Before (Works Correctly)** | **After (Runtime Error)** | **What Changed** |
|------------------------------|---------------------------|------------------|
| ```javascript<br>if (!selectedImages) {<br>    selectedImages = [<br>        ...getRandomSubset(leftImages, 7),<br>        ...getRandomSubset(centerImages, 7),<br>        ...getRandomSubset(rightImages, 7)<br>    ].sort(() => 0.5 - Math.random());<br>}<br><br>selectedImages.forEach((file) => {<br>    const card = createImageCard(file);<br>    imagesArea.appendChild(card);<br>});<br>``` | ```javascript<br>// Force null assignment<br>selectedImages = null;<br><br><br><br><br><br><br><br>selectedImages.forEach((file) => {<br>    const card = createImageCard(file);<br>    imagesArea.appendChild(card);<br>});<br>// CRASH: Cannot read 'forEach' of null<br>``` | Removed the safety check that creates a valid array when `selectedImages` is falsy, and instead directly assigned `null`. This causes `.forEach()` to fail because you cannot call array methods on `null`. |

---

### Prompt 4: Data and Procedural Abstraction

**Prompt:** *Suppose you are provided with a procedure called isEqual(value1, value2). The procedure returns true if the two parameters value1 and value2 are equal in value and returns false otherwise. Using the list you identified in the List section of your Personalized Project Reference, explain in detailed steps an algorithm that uses isEqual to count the number of times a certain value appears in your list. Your explanation must be detailed enough for someone else to write the program code.*

To count the number of times a certain value appears in my `imageFiles` list using the `isEqual` procedure, you would follow these detailed steps:

**Step 1:** Initialize a counter variable called `count` and set it to 0. This variable will keep track of how many matches we find.

**Step 2:** Define the target value you want to search for. Since my `imageFiles` list contains objects with properties (`src`, `company`, `bin`), I need to specify which property to compare and what value to look for. For example, if I want to count how many outlets are categorized as `"Left"`, my target would be the string `"Left"`.

**Step 3:** Create a loop that iterates through every element in the `imageFiles` array. Use a `for` loop or `forEach` loop to access each element one at a time, starting from index 0 and continuing until you reach the last element.

**Step 4:** For each element in the loop, extract the specific property value you want to compare. For example, if you're counting `"Left"` outlets, extract the `bin` property from the current object using `imageFiles[i].bin` or `element.bin`.

**Step 5:** Call the `isEqual` procedure with two parameters: the extracted property value from the current element and your target value. For example: `isEqual(element.bin, "Left")`.

**Step 6:** Check the return value from `isEqual`. If it returns `true` (meaning the values match), increment the `count` variable by 1 using `count = count + 1` or `count++`. If `isEqual` returns `false`, do nothing and continue to the next element.

**Step 7:** Continue the loop until you have examined every element in the `imageFiles` array.

**Step 8:** After the loop completes, the `count` variable will contain the total number of occurrences of your target value in the list. Return or display this `count` value.

For example, if `imageFiles` contains 30 media outlets and 10 of them have `bin` equal to `"Left"`, this algorithm would result in `count` being 10 after all iterations complete.

```javascript
// Example implementation of the algorithm
function countOccurrences(targetBin) {
    let count = 0;
    
    for (let i = 0; i < imageFiles.length; i++) {
        if (isEqual(imageFiles[i].bin, targetBin)) {
            count++;
        }
    }
    
    return count;
}

// Example usage:
let leftCount = countOccurrences("Left");     // Returns 10
let centerCount = countOccurrences("Center"); // Returns 10
let rightCount = countOccurrences("Right");   // Returns 10
```