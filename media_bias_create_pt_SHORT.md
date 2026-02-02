# Create PT Writeup

## 1. INPUT

### Drag-and-Drop (Mediachat.md, line 350)
```javascript
img.addEventListener('dragstart', (e) => {
    if (!gameStarted) {
        gameStarted = true;
        timerHandle = startTimer();
    }
    e.dataTransfer.setData('text/plain', e.target.dataset.id);
});
```
**Captures:** Image ID, drag event, starts timer on first interaction

### Submit Button (Mediachat.md, line 623)
```javascript
submitBtn.addEventListener('click', () => {
    const totalImages = document.querySelectorAll('.image').length;
    const placedCount = placedImages.size;
    // Validates completion and correctness
});
```
**Captures:** User completion signal, triggers validation

---

## 2. OUTPUT

### Incorrect Feedback Modal (Mediachat.md, line 505)
```javascript
function showIncorrectFeedback(incorrectImages) {
    const imageGrid = incorrectImages.map(img => 
        `<div>
            <img src="${img.src}">
            <div>${img.name}</div>
            <div>Currently in: ${img.currentBin}</div>
        </div>`
    ).join('');
}
```
**Displays:** Which outlets are wrong, their current location, visual feedback

### Leaderboard (Mediachat.md, line 475)
```javascript
async function fetchLeaderboard() {
    const response = await fetch(pythonURI + '/api/media/leaderboard?limit=5');
    const data = await response.json();
    data.forEach((entry, index) => {
        // Display rank, username, time
    });
}
```
**Displays:** Rankings, usernames, completion times

---

## 3. LIST (Row 2 - Data Abstraction)

### Master List (Mediachat.md, line 178)
```javascript
const imageFiles = [
    { src: "atlanticL.png", company: "Atlantic", bin: "Left" },
    { src: "buzzfeedL.png", company: "Buzzfeed", bin: "Left" },
    { src: "cnnL.png", company: "CNN", bin: "Left" },
    // ... 27 more entries (30 total)
];
```

### Selected Images List (Mediachat.md, line 330)
```javascript
const getRandomSubset = (arr, count) => {
    return [...arr].sort(() => 0.5 - Math.random()).slice(0, count);
};

selectedImages = [
    ...getRandomSubset(leftImages, 7),
    ...getRandomSubset(centerImages, 7),
    ...getRandomSubset(rightImages, 7)
].sort(() => 0.5 - Math.random());
```
**Purpose:** Stores 21 randomly selected images for current game
**Operations:** Filter by category, random selection, concatenation, shuffle

### Incorrect Images List (Mediachat.md, line 630)
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
**Purpose:** Collects misplaced items for feedback display

**Why Lists Are Necessary:**
- Can't use 30 individual variables
- Need to iterate, filter, and randomly select
- Dynamic size based on validation results

---

## 4. PROCEDURE (Row 3 - Procedural Abstraction)

### initGame() (Mediachat.md, line 318)
```javascript
function initGame() {
    // Clear existing game
    imagesArea.innerHTML = '';
    placedImages.clear();
    gameStarted = false;
    
    // Load or create random selection
    const data = loadData();
    let selectedImages = null;
    
    if (data.meta.roundImages && data.meta.roundImages.length === 21) {
        // Reuse previous round selection
        selectedImages = mapIdsToFiles(data.meta.roundImages);
    }
    
    if (!selectedImages) {
        // Create new random selection (7 from each category)
        selectedImages = [
            ...getRandomSubset(leftImages, 7),
            ...getRandomSubset(centerImages, 7),
            ...getRandomSubset(rightImages, 7)
        ].sort(() => 0.5 - Math.random());
        
        data.meta.roundImages = selectedImages.map(f => slugify(f.company));
        saveData(data);
    }
    
    // Create image cards
    selectedImages.forEach(file => {
        const card = createImageCard(file);
        imagesArea.appendChild(card);
    });
    
    // Restore saved placements
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

**Called By:**
- `window.onload` - Initial page load
- Reset button - User clicks reset
- Submit handler - After successful completion

**Purpose:** Centralizes complex initialization logic (60+ lines) that would otherwise be duplicated in 3 places

**Parameters:** None (uses global state)

---

## 5. ALGORITHM (Row 4 - Algorithm Implementation)

### Validation Algorithm (Mediachat.md, line 623)
```javascript
submitBtn.addEventListener('click', () => {
    // STEP 1: Check completion
    const totalImages = document.querySelectorAll('.image').length;
    const placedCount = placedImages.size;
    
    if (placedCount < totalImages) {
        alert(`Haven't placed all images!`);
        return;  // SELECTION: early exit
    }

    // STEP 2: Validate correctness
    let incorrectImages = [];
    document.querySelectorAll('.bin').forEach(bin => {  // ITERATION
        bin.querySelectorAll('.image').forEach(img => {  // NESTED ITERATION
            if (img.dataset.bin !== bin.dataset.bin) {  // SELECTION
                incorrectImages.push({
                    name: img.dataset.company,
                    currentBin: bin.dataset.bin,
                    src: img.src
                });
            }
        });
    });

    // STEP 3: Handle incorrect placements
    if (incorrectImages.length > 0) {  // SELECTION
        showIncorrectFeedback(incorrectImages);
        return;
    }

    // STEP 4: Success - record score
    if (timerHandle) {  // SELECTION
        const elapsed = timerHandle.stop();
        const username = window.currentPlayerUid || 'Guest';
        
        // Save locally
        const d = loadData();
        d.attempts = d.attempts || [];
        d.attempts.push({ username, time: elapsed, at: Date.now() });
        saveData(d);
        
        // Submit to server
        submitFinalTime(username, elapsed);
        showCongrats();
        initGame();
    }
});
```

**Includes:**
- **Sequencing:** Steps 1→2→3→4 executed in order
- **Selection:** 4 if-statements determine path
- **Iteration:** 2 nested forEach loops

---

## 6. BACKEND API

### Score Submission (media_api.py, line 91)
```python
class MediaScoreAPI(Resource):
    def post(self, username=None, time=None):
        # Accept path params OR JSON body
        if username and time:
            time = int(time)
        else:
            body = request.get_json()
            username = body.get('username')
            time = int(body.get('time'))
        
        # Save to database
        score = MediaScore(username=username, time=time)
        created_score = score.create()
        
        return created_score.read(), 201
```

### Leaderboard (media_api.py, line 140)
```python
class MediaLeaderboardAPI(Resource):
    def get(self):
        # Get best time per user using SQL
        subquery = db.session.query(
            MediaScore.username,
            func.min(MediaScore.time).label('best_time')
        ).group_by(MediaScore.username).subquery()
        
        scores = db.session.query(MediaScore).join(
            subquery,
            db.and_(
                MediaScore.username == subquery.c.username,
                MediaScore.time == subquery.c.best_time
            )
        ).order_by(MediaScore.time.asc()).limit(limit).all()
        
        # Add ranks
        leaderboard = []
        for rank, score in enumerate(scores, start=1):
            entry = score.read()
            entry['rank'] = rank
            leaderboard.append(entry)
        
        return leaderboard, 200
```

### Database Model (media_api.py, line 17)
```python
class MediaScore(db.Model):
    __tablename__ = 'media_scores'
    
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(100), nullable=False)
    time = db.Column(db.Integer, nullable=False)
    created_at = db.Column(db.DateTime, default=datetime.utcnow)
    
    def create(self):
        db.session.add(self)
        db.session.commit()
        return self
```

---

## 7. ADMIN UI (Postman Alternative)

### Testing Interface (u2table.html, line 465)
```javascript
// Edit score
async function editMediaScore(scoreId, currentUsername, currentTime) {
    const newUsername = prompt(`Enter new username:`, currentUsername);
    const newTime = prompt(`Enter new time (seconds):`, currentTime);
    
    fetch(`/media/update/${scoreId}`, {
        method: 'PUT',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ username: newUsername, time: parseInt(newTime) })
    });
}

// Delete score
async function deleteMediaScore(scoreId) {
    if (!confirm('Delete this score?')) return;
    fetch(`/media/delete/${scoreId}`, { method: 'DELETE' });
}
```

**Features:** View all scores, edit entries, delete entries, view stats

---

## 8. COLLEGE BOARD ALIGNMENT

### Row 1: Program Purpose and Function
**Purpose:** Teach media bias identification  
**Input:** Drag-and-drop, authentication  
**Output:** Feedback modals, leaderboard, timer  
**Functionality:** Sort 21 outlets, get validation, compete on timed leaderboard

### Row 2: Data Abstraction
**List Name:** `selectedImages`  
**Stores:** 21 randomly selected media outlet objects  
**Used For:** Game initialization, display, validation  
**Why Necessary:** Can't use 21+ variables; needs iteration, filtering, random selection

### Row 3: Procedural Abstraction
**Procedure:** `initGame()`  
**Parameters:** None  
**Called:** Page load, reset, after completion  
**Advantage:** Prevents duplicating 60+ lines in 3 places

### Row 4: Algorithm
**Algorithm:** Submit validation  
**Includes:** Sequencing (4 steps), selection (4 if-statements), iteration (2 nested loops)  
**Purpose:** Verify completion and correctness before recording score

---

## 9. NO HARD-CODED DATA

✅ Image list could load from JSON/API  
✅ Game state in localStorage (dynamic)  
✅ Leaderboard from database (no preset winners)  
✅ Users from database (no hard-coded accounts)

---

## VIDEO CHECKLIST

- [ ] Show drag-and-drop input
- [ ] Show incorrect feedback output (trigger error)
- [ ] Show successful completion output (leaderboard update)
- [ ] Mention `selectedImages` list usage
- [ ] Call `initGame()` via reset button
- [ ] Demonstrate validation algorithm (show both paths)

---

## QUICK REFERENCE

**Input:** Lines 350 (drag), 623 (submit)  
**Output:** Lines 505 (feedback), 475 (leaderboard)  
**List:** Lines 178 (master), 330 (selected), 630 (incorrect)  
**Procedure:** Line 318 (`initGame`)  
**Algorithm:** Line 623 (validation)  
**Backend:** media_api.py lines 17, 91, 140  
**Admin UI:** u2table.html line 465
