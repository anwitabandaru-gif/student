## Before Refactoring
```javascript
    window.addEventListener('DOMContentLoaded', () => {
        console.log("DOM fully loaded — initializing game & buttons");

        initGame();
        console.log("Game initialized automatically");

        const resetBtn = document.getElementById('reset-btn');
        if (resetBtn) {
            resetBtn.addEventListener('click', () => {
                console.log("🔁 Reset clicked");
                const ids = Array.from(document.querySelectorAll('img.image')).map(i => i.dataset.id);
                clearGameStateForIds(ids);

                const data = loadData();
                if (data.meta && data.meta.roundImages) {
                    delete data.meta.roundImages;
                    saveData(data);
                }

                initGame();
            });
        }

        const autofillBtn = document.getElementById('autofill-images');
        if (autofillBtn) {
            autofillBtn.addEventListener('click', () => {
                console.log("✨ Autofill clicked");
                autofillImageGame(true);
            });
        }

        const submitBtn = document.getElementById('submit-btn');
        if (submitBtn) {
            submitBtn.addEventListener('click', () => {
                console.log("Submit clicked");

                const totalImages = document.querySelectorAll('.image').length;
                const placedCount = placedImages.size;

                if (placedCount < totalImages) {
                    alert(`You haven't placed all the images yet! You've placed ${placedCount} out of ${totalImages}.`);
                    return;
                }

                // Check for correct placement and collect incorrect ones
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

                if (incorrectImages.length > 0) {
                    showIncorrectFeedback(incorrectImages);
                    return;
                }

                // NEW: Check if autofill was used
                if (autofillUsed) {
                    showAutofillWarning();
                    initGame(); // Reset game
                    return;
                }

                // Stop timer and get final time (only if autofill wasn't used)
                if (timerHandle) {
                    const elapsed = timerHandle.stop();
                    const username = window.currentPlayerUid || 'Guest';

                    try {
                        const d = loadData();
                        d.attempts = d.attempts || [];
                        const prompts = (d.meta && d.meta.currentChatPrompts) ? d.meta.currentChatPrompts.slice() : [];
                        d.attempts.push({ 
                            username: username,
                            time: Number(elapsed) || 0, 
                            at: Date.now(), 
                            prompts 
                        });
                        if (d.meta) delete d.meta.currentChatPrompts;
                        saveData(d);
                    } catch (err) {
                        console.warn('save attempt with prompts failed', err);
                    }

                    submitFinalTime(username, elapsed);
                    
                    showCongrats(elapsed);
                    initGame();
                } else {
                    alert("Timer not started. Please play the game first!");
                }
            });
        }
    });

    // Initialize
    window.onload = () => {
        console.log("Window fully loaded — starting game");
        fetchUser();
        initGame();
        fetchLeaderboard();
        setInterval(fetchLeaderboard, 30000);
    };
```
## After Refactoring

```javascript
//SRP CHANGES
// WORKER: Validate all images are placed
function validateAllPlaced(placedImages) {
    const total = document.querySelectorAll('.image').length;
    if (placedImages.size < total) {
        alert(`Place all images first! (${placedImages.size}/${total})`);
        return false;
    }
    return true;
}

// WORKER: Find incorrect placements
function getIncorrectPlacements() {
    const incorrect = [];
    document.querySelectorAll('.bin').forEach(bin => {
        bin.querySelectorAll('.image').forEach(img => {
            if (img.dataset.bin !== bin.dataset.bin) {
                incorrect.push({
                    name: img.dataset.company,
                    currentBin: bin.dataset.bin,
                    src: img.src
                });
            }
        });
    });
    return incorrect;
}

// WORKER: Save attempt data to localStorage
function saveAttemptLocally(username, elapsed) {
    const d = loadData();
    d.attempts = d.attempts || [];
    const prompts = d.meta?.currentChatPrompts?.slice() ?? [];
    d.attempts.push({ username, time: Number(elapsed) || 0, at: Date.now(), prompts });
    if (d.meta) delete d.meta.currentChatPrompts;
    saveData(d);
}

    window.addEventListener('DOMContentLoaded', () => {
        console.log("DOM fully loaded — initializing game & buttons");

        initGame();
        console.log("Game initialized automatically");

        const resetBtn = document.getElementById('reset-btn');
        if (resetBtn) {
            resetBtn.addEventListener('click', () => {
                console.log("🔁 Reset clicked");
                const ids = Array.from(document.querySelectorAll('img.image')).map(i => i.dataset.id);
                clearGameStateForIds(ids);

                const data = loadData();
                if (data.meta && data.meta.roundImages) {
                    delete data.meta.roundImages;
                    saveData(data);
                }

                initGame();
            });
        }

        const autofillBtn = document.getElementById('autofill-images');
        if (autofillBtn) {
            autofillBtn.addEventListener('click', () => {
                console.log("✨ Autofill clicked");
                autofillImageGame(true);
            });
        }

        const submitBtn = document.getElementById('submit-btn');
        if (submitBtn) {
            submitBtn.addEventListener('click', () => {
                if (!validateAllPlaced(placedImages)) return;

                const incorrect = getIncorrectPlacements();
                if (incorrect.length > 0) {
                    showIncorrectFeedback(incorrect);
                    return;
                }

                if (autofillUsed) {
                    showAutofillWarning();
                    initGame();
                    return;
                }

                if (!timerHandle) {
                    alert("Timer not started. Please play the game first!");
                    return;
                }

                const elapsed = timerHandle.stop();
                const username = window.currentPlayerUid || 'Guest';

                saveAttemptLocally(username, elapsed);
                submitFinalTime(username, elapsed);
                showCongrats(elapsed);
                initGame();
            });
        }       
        
    });
```