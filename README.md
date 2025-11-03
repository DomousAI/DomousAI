body {
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
    height: 100vh;
}

.gradient-background {
    background: linear-gradient(135deg, #74ebd5, #acb6e5);
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
}

.chatbot {
    background: white;
    border-radius: 10px;
    box-shadow: 0 4px 20px rgba(0,0,0,0.1);
    width: 300px;
    max-width: 90%;
    display: flex;
    flex-direction: column;
}

.chatbot-header {
    background: #007BFF;
    color: white;
    padding: 10px;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    text-align: center;
}

.chatbot-messages {
    flex-grow: 1;
    padding: 10px;
    overflow-y: auto;
    max-height: 300px;
    border: 1px solid #ddd;
}
// script.js
document.addEventListener('DOMContentLoaded', () => {
    // Make the studio window draggable
    const studio = document.getElementById('studio');
    let isDragging = false;
    let offsetX, offsetY;

    studio.addEventListener('mousedown', (e) => {
        isDragging = true;
        offsetX = e.clientX - studio.getBoundingClientRect().left;
        offsetY = e.clientY - studio.getBoundingClientRect().top;
        studio.style.cursor = 'grabbing';
    });

    document.addEventListener('mousemove', (e) => {
        if (isDragging) {
            studio.style.left = `${e.clientX - offsetX}px`;
            studio.style.top = `${e.clientY - offsetY}px`;
        }
    });

    document.addEventListener('mouseup', () => {
        isDragging = false;
        studio.style.cursor = 'move';
    });

    // Load sounds from JSON
    fetch('sounds.json')
        .then(response => response.json())
        .then(sounds => {
            // Attach event listeners to buttons
            document.getElementById('kick').addEventListener('click', () => new Audio(sounds.kick).play());
            document.getElementById('snare').addEventListener('click', () => new Audio(sounds.snare).play());
            document.getElementById('hihat').addEventListener('click', () => new Audio(sounds.hihat).play());
            document.getElementById('crash').addEventListener('click', () => new Audio(sounds.crash).play());
            document.getElementById('violin').addEventListener('click', () => new Audio(sounds.violin).play());
        })
        .catch(error => console.error('Error loading sounds:', error));
});


// sounds.json
{
    "kick": "https://actions.google.com/sounds/v1/ambient/beat_drop.wav",
    "snare": "https://actions.google.com/sounds/v1/ambient/snare_drum.wav",
    "hihat": "https://actions.google.com/sounds/v1/ambient/hi_hat.wav",
    "crash": "https://actions.google.com/sounds/v1/ambient/crash_cymbal.wav",
    "violin": "https://actions.google.com/sounds/v1/instruments/violin.wav"
}

/* styles.css */
body {
    background: black;
    color: lime;
    font-family: courier, monospace;
    margin: 0;
    padding: 0;
    overflow: hidden;
}

.draggable {
    position: absolute;
    top: 10px;
    left: 10px;
    width: 300px;
    height: auto;
    background: #111;
    z-index: 999;
    border: 2px solid lime;
    resize: both;
    overflow: auto;
    padding: 10px;
    cursor: move;
}

h1 {
    margin-top: 0;
    text-align: center;
}

button {
    display: block;
    width: 100%;
    margin: 5px 0;
    background: #222;
    color: lime;
    border: 1px solid lime;
    padding: 10px;
    cursor: pointer;
}

button:hover {
    background: #333;
}
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Music Load</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div id="studio" class="draggable">
        <h1>Music Load</h1>
        <button id="kick">Kick</button>
        <button id="snare">Snare</button>
        <button id="hihat">Hi-hat</button>
        <button id="crash">Crash</button>
        <button id="violin">Violin</button>
    </div>
    <script src="script.js"></script>
</body>
</html>
