<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My Baby ❤️</title>
    <style>
        body {
            background-color: #ffdeeb;
            background-image: url('https://www.transparenttextures.com/patterns/heart.png'); /* Tiny hearts pattern */
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            overflow: hidden;
        }

        #container {
            background: white;
            padding: 30px;
            border-radius: 40px;
            box-shadow: 0 15px 35px rgba(255, 105, 180, 0.3);
            text-align: center;
            width: 350px;
            border: 5px solid #ffb3c1;
        }

        .bunny-gif {
            width: 200px;
            height: 200px;
            object-fit: contain;
            margin-bottom: 10px;
        }

        h2 { color: #ff4d6d; font-size: 20px; line-height: 1.4; }

        .buttons {
            margin-top: 20px;
            display: flex;
            justify-content: center;
            gap: 15px;
        }

        button {
            padding: 12px 25px;
            font-size: 16px;
            border-radius: 50px;
            border: none;
            cursor: pointer;
            font-weight: bold;
            transition: 0.3s;
        }

        .yes-btn { background-color: #ff4d6d; color: white; }
        .no-btn { background-color: #ffb3c1; color: white; position: absolute; }
        
        /* This keeps the No button relative to the box initially */
        #no-wrap { position: relative; width: 80px; height: 45px; }

        .heart-pop {
            position: absolute;
            font-size: 20px;
            animation: floatUp 2s forwards;
        }

        @keyframes floatUp {
            to { transform: translateY(-100px); opacity: 0; }
        }
    </style>
</head>
<body>

<div id="container">
    <img id="main-gif" class="bunny-gif" src="https://media.tenor.com/S99S8_z8Y_IAAAAi/milk-and-mocha-bear-hearts.gif" alt="Cute Bunny">
    <h2 id="text">Do you love me?</h2>
    
    <div class="buttons">
        <button class="yes-btn" onclick="handleYes()">Yes</button>
        <div id="no-wrap">
            <button id="no-btn" class="no-btn" onclick="handleNo()">No</button>
        </div>
    </div>
</div>

<script>
    let step = 1;
    const mainGif = document.getElementById('main-gif');
    const text = document.getElementById('text');
    const noBtn = document.getElementById('no-btn');

    // GIF LINKS
    const kissGif = "https://media.tenor.com/T_7_fB_9E38AAAAi/milk-and-mocha-kiss.gif";
    const angryGif = "https://media.tenor.com/vHqV-16V6mUAAAAi/milk-and-mocha-bear-angry.gif";
    const hugGif = "https://media.tenor.com/Y8_0_AAnl_0AAAAi/milk-and-mocha-hug.gif";
    const thinkingGif = "https://media.tenor.com/9nFfT0Xun-kAAAAi/milk-and-mocha-bear.gif";

    function handleNo() {
        if (step === 1) {
            alert("You have to say yes! 🙄");
        } else if (step === 2) {
            mainGif.src = angryGif;
            text.innerHTML = "INVALID ANSWER! 💢 <br> Try again...";
        }
    }

    // This makes the No button run away for the last question
    noBtn.onmouseover = () => {
        if (step === 3) {
            const x = Math.random() * (window.innerWidth - 100);
            const y = Math.random() * (window.innerHeight - 50);
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
            noBtn.style.position = 'fixed';
        }
    };

    function handleYes() {
        if (step === 1) {
            mainGif.src = kissGif;
            text.innerHTML = "Right answer! 😘 <br><br> Will you promise to talk to her when it hurts?";
            step = 2;
        } else if (step === 2) {
            mainGif.src = thinkingGif;
            text.innerHTML = "I love you baby ure correct! 🥰 <br><br> Will you promise to listen to ur gf?";
            step = 3;
        } else if (step === 3) {
            mainGif.src = hugGif;
            text.innerHTML = "Good job babyy u re love of my life! I love you very much babyy! 💋";
            noBtn.style.display = 'none';
            spawnHearts();
        }
    }

    function spawnHearts() {
        for(let i=0; i<15; i++) {
            setTimeout(() => {
                const heart = document.createElement('div');
                heart.className = 'heart-pop';
                heart.innerHTML = '❤️';
                heart.style.left = Math.random() * 100 + '%';
                heart.style.top = '60%';
                document.body.appendChild(heart);
                setTimeout(() => heart.remove(), 2000);
            }, i * 200);
        }
    }
</script>

</body>
</html>

