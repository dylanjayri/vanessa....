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
        width: 320px;
        margin: 0 auto;
    }

    #gameArea {
        position: relative;
        width: 320px;
        height: 200px;
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
        transition: left 1.2s ease, top 1.2s ease; /* slower movement */
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

// Create heart
const heart = document.createElement("div");
heart.clas
