<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Pongal</title>
    <style>
        body, html {
            height: 100%;
            margin: 0;
            overflow: hidden;
        }
        .container {
            position: relative;
            height: 100%;
            width: 100%;
        }
        .colorful-text, .name-text, .celebrate-text, .click-text {
            font-size: 2em;
            font-weight: bold;
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            z-index: 2;
            animation: colors 5s infinite;
        }
        .colorful-text {
            top: 20px;
        }
        .name-text {
            top: 80px;
        }
        .celebrate-text {
            top: 10px;
            display: none;
            color: #fff;
        }
        .click-text {
            top: 75%;
            display: none;
            cursor: pointer;
            color: #fff;
            font-size: 1.5em;
        }
        @keyframes colors {
            0% { color: #ff4500; }
            25% { color: #ffa500; }
            50% { color: #32cd32; }
            75% { color: #1e90ff; }
            100% { color: #ff4500; }
        }
        video, #blackScreen {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            object-fit: cover;
            z-index: 1;
        }
        #blackScreen, #nextVideo {
            display: none;
        }
        #nextVideo {
            position: absolute;
            z-index: 3;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        #potImage {
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            top: 50px;
            z-index: 2;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="colorful-text" id="happyPongalText">Happy Pongal</div>
        <div class="name-text" id="nameText"></div>
        <div class="celebrate-text" id="celebrateText"></div>
        <div id="blackScreen"></div>
        <img id="potImage" src="img/pot.png" alt="Pongal Pot">
        <div class="click-text" id="clickText" onclick="playNextVideo()">Click Here</div>
        <video id="pongalVideo" autoplay muted>
            <source src="vid0.mp4" type="video/mp4">
            Your browser does not support the video tag.
        </video>
        <video id="nextVideo" controls>
            <source src="vid1.mp4" type="video/mp4">
            Your browser does not support the video tag.
        </video>
        <audio id="pongalAudio" autoplay loop>
            <source src="Your_Pongal_Audio.mp3" type="audio/mpeg">
            Your browser does not support the audio element.
        </audio>
    </div>
    <script>
        window.onload = function() {
            let name = prompt("Please enter your name:");
            let nameText = document.getElementById('nameText');
            let celebrateText = document.getElementById('celebrateText');
            if (name != null && name != "") {
                nameText.innerText = "To dear " + name;
                celebrateText.innerText = `Come on ${name},\nlet's celebrate \nPongal together!`;
            } else {
                nameText.innerText = "";
                celebrateText.innerText = "Let's celebrate Pongal together!";
            }
            let pongalVideo = document.getElementById('pongalVideo');
            pongalVideo.style.display = 'block';
            pongalVideo.play();
            pongalVideo.onended = function() {
                let blackScreen = document.getElementById('blackScreen');
                blackScreen.style.backgroundColor = 'black';
                blackScreen.style.display = 'block';
                document.getElementById('happyPongalText').style.display = 'none';
                nameText.style.display = 'none';
                celebrateText.style.display = 'block';
                let clickText = document.getElementById('clickText');
                clickText.style.display = 'block';
            };
        };

        function playNextVideo() {
            let pongalVideo = document.getElementById('pongalVideo');
            pongalVideo.style.display = 'none';
            let blackScreen = document.getElementById('blackScreen');
            blackScreen.style.display = 'none';
            let clickText = document.getElementById('clickText');
            clickText.style.display = 'none';
            let nextVideo = document.getElementById('nextVideo');
            nextVideo.style.display = 'block';
            nextVideo.play();
        }
    </script>
</body>
</html>
