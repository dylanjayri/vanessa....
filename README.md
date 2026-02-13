<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Catch My Heart 💖</title>

<style>
    body {
        margin: 0;
        background: #ffe6ea;
        font-family: Arial, sans-serif;
        text-align: center;
    }

    h1 {
        color: #c9184a;
        margin-top: 20px;
    }

    #gameContainer {
        width: 400px;
        margin: 0 auto;
    }

    #gameArea {
        position: relative;
        width: 400px;
        height: 250px;
        background: #fff0f3;
        border-radius: 15px;
        margin-top: 20px;
        overflow: hidden;
        border: 2px solid #ffc2d1;
    }

    .heart {
        position: absolute;
        font-size: 40px;
        cursor: pointer;
        transition: left 0.6s ease, top 0.6s ease; /* slower movement */
    }

    button {
        padding: 10px 20px;
        font-size: 16px;
        border: none;
        cursor: pointer;
        margin: 10px;
        border-radius: 8px;
    }

    #yesBtn {
        background-color: #ff8fab;
    }

    #noBtn {
        background-color: #ffc2d1;
        position: absolute;
    }

    #proposal {
        display: none;
        margin-top: 30px;
        position: relative;
        height: 200px;
    }
</style>
</head>

<body>

<h1>💘 Catch My Heart 💘</h1>
<p id="counter">Vanessa 💕 Catch 5 hearts if you can 😏</p>

<div id="gameContainer">
    <div id="gameArea"></div>
</div>

<div id="proposal">
    <h2>Vanessa ❤️</h2>
    <p>You caught my heart…</p>
    <p><strong>Will you be my girlfriend?</strong></p>
    <button id="yesBtn">YES 💕</button>
    <button id="noBtn">No 😢</button>
</div>

<script>
let heartsCaught = 0;
const totalHearts = 5;

const gameArea = document.getElementById("gameArea");
const counter = document.getElementById("counter");
const proposal = document.getElementById("proposal");
const noBtn = document.getElementById("noBtn");

// Create heart element
const heart = document.createElement("div");
heart.classList.add("heart");
heart.innerHTML = "❤️";
gameArea.appendChild(heart);

// Smaller movement boundaries
function moveHeart() {
    const maxX = 340;  // 400 width - heart space
    const maxY = 190;  // 250 height - heart space

    const x = Math.random() * maxX;
    const y = Math.random() * maxY;

    heart.style.left = x + "px";
    heart.style.top = y + "px";
}

// Move heart slowly when hovered
heart.addEventListener("mouseenter", () => {
    moveHeart();
});

// Click heart
heart.addEventListener("click", () => {
    heartsCaught++;
    counter.innerText = `Hearts: ${heartsCaught} / ${totalHearts}`;

    if (heartsCaught < totalHearts) {
        moveHeart();
    } else {
        gameArea.style.display = "none";
        counter.style.display = "none";
        proposal.style.display = "block";
    }
});

// YES button celebration
document.getElementById("yesBtn").addEventListener("click", () => {
    document.body.innerHTML = `
        <h1 style="margin-top:120px;color:#c9184a;">
            She said YES!!! 💖
        </h1>
        <p style="font-size:20px;">
            Vanessa 💕 You just made me the happiest person alive ❤️
        </p>
    `;
});

// NO button runs & shrinks
let noSize = 16;
noBtn.style.fontSize = noSize + "px";

noBtn.addEventListener("mouseenter", () => {
    const x = Math.random() * 300;
    const y = Math.random() * 150;

    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";

    if (noSize > 8) {
        noSize -= 1;
        noBtn.style.fontSize = noSize + "px";
    }
});

// Initial heart position
moveHeart();
</script>

</body>
</html>
