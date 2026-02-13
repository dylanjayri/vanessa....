# vanessa....
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
        overflow: hidden;
    }

    h1 {
        color: #c9184a;
    }

    #gameArea {
        position: relative;
        width: 100vw;
        height: 60vh;
        background: #fff0f3;
        margin-top: 20px;
        overflow: hidden;
    }

    .heart {
        position: absolute;
        font-size: 40px;
        cursor: pointer;
        transition: all 0.2s ease;
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
    }
</style>
</head>

<body>

<h1>💘 Catch My Heart 💘</h1>
<p id="counter">Vanessa 💕 Catch 5 hearts if you can 😏</p>

<div id="gameArea"></div>

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

// Create moving heart
const heart = document.createElement("div");
heart.classList.add("heart");
heart.innerHTML = "❤️";
gameArea.appendChild(heart);

function moveHeart() {
    const x = Math.random() * (window.innerWidth - 60);
    const y = Math.random() * (gameArea.offsetHeight - 60);
    heart.style.left = x + "px";
    heart.style.top = y + "px";
}

// Slow move effect
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

// YES button
document.getElementById("yesBtn").addEventListener("click", () => {
    alert("Vanessa 💕 You just made me the happiest person alive ❤️");
    document.body.innerHTML = "<h1 style='margin-top:100px;color:#c9184a;'>She said YES!!! 💖</h1>";
});

// NO button runs & shrinks
let noSize = 16;
noBtn.style.fontSize = noSize + "px";

noBtn.addEventListener("mouseenter", () => {
    const x = Math.random() * (window.innerWidth - 120);
    const y = Math.random() * (window.innerHeight - 120);
    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";

    if (noSize > 8) {
        noSize -= 1;
        noBtn.style.fontSize = noSize + "px";
    }
});

moveHeart();
</script>

</body>
</html>
