<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
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

#gameArea {
    position: relative;
    width: 280px;
    height: 180px;
    margin: 20px auto;
    background: #fff0f3;
    border-radius: 15px;
    border: 2px solid #ffc2d1;
    overflow: hidden;
}

.heart {
    position: absolute;
    font-size: 48px;
    cursor: pointer;
    transition: left 1.2s ease, top 1.2s ease;
    user-select: none;
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
</style>
</head>

<body>

<h1>💘 Catch My Heart 💘</h1>
<p id="counter">Vanessa 💕 Catch 5 hearts!</p>

<div id="gameArea"></div>

<div id="proposal" style="display:none; position:relative; height:200px;">
    <h2>Vanessa ❤️</h2>
    <p>You caught my heart...</p>
    <p><strong>Will you be my girlfriend?</strong></p>
    <button id="yesBtn">YES 💕</button>
    <button id="noBtn">No 😢</button>
</div>

<script>
window.onload = function() {

let heartsCaught = 0;
const totalHearts = 5;

const gameArea = document.getElementById("gameArea");
const counter = document.getElementById("counter");
const proposal = document.getElementById("proposal");

const heart = document.createElement("div");
heart.className = "heart";
heart.textContent = "❤️";
gameArea.appendChild(heart);

function moveHeart() {
    const areaWidth = gameArea.clientWidth;
    const areaHeight = gameArea.clientHeight;

    const heartSize = 48;

    const maxX = areaWidth - heartSize;
    const maxY = areaHeight - heartSize;

    const x = Math.random() * maxX;
    const y = Math.random() * maxY;

    heart.style.left = x + "px";
    heart.style.top = y + "px";
}

// Tap or click works on mobile
heart.addEventListener("click", function() {
    heartsCaught++;
    counter.innerText = "Hearts: " + heartsCaught + " / " + totalHearts;

    if (heartsCaught < totalHearts) {
        moveHeart();
    } else {
        gameArea.style.display = "none";
        counter.style.display = "none";
        proposal.style.display = "block";
    }
});

// YES button
document.getElementById("yesBtn").addEventListener("click", function() {
    document.body.innerHTML = `
        <h1 style="margin-top:120px;color:#c9184a;">
            She said YES!!! 💖
        </h1>
        <p style="font-size:20px;">
            Vanessa 💕 You just made me the happiest person alive ❤️
        </p>
    `;
});

// NO button runs and shrinks
const noBtn = document.getElementById("noBtn");
let noSize = 16;
noBtn.style.fontSize = noSize + "px";

function moveNo() {
    const x = Math.random() * 200;
    const y = Math.random() * 120;

    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";

    if (noSize > 8) {
        noSize -= 1;
        noBtn.style.fontSize = noSize + "px";
    }
}

noBtn.addEventListener("click", moveNo);
noBtn.addEventListener("touchstart", function(e){
    e.preventDefault();
    moveNo();
});

// Initial spawn AFTER everything loads
setTimeout(moveHeart, 200);

};
</script>

</body>
</html>
