# Marcellus-vip-signals
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Marcellus Aviator Signals VIP</title>
<style>
    @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
        font-family: 'Roboto', sans-serif;
        background: #000;
        color: #fff;
        height: 100vh;
        overflow: hidden;
        position: relative;
    }

    #matrix-canvas {
        position: fixed;
        top: 0;
        left: 0;
        z-index: 1;
    }

    .container {
        position: relative;
        z-index: 10;
        max-width: 420px;
        margin: 0 auto;
        padding: 20px;
        height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
    }

    /* Loading Screen */
    #loading {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: #000;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        text-align: center;
        padding: 20px;
        z-index: 30;
    }
    #loading h1 {
        color: #00ff00;
        font-size: 28px;
        font-weight: 700;
        font-family: 'Courier New', monospace;
        margin-bottom: 10px;
        text-shadow: 0 0 10px #00ff00;
    }
    #loading p {
        color: #b3ffb3;
        font-size: 14px;
        margin-bottom: 18px;
        font-family: 'Courier New', monospace;
    }
    .loader {
        width: 250px;
        height: 12px;
        border: 1px solid #00ff00;
        border-radius: 6px;
        overflow: hidden;
        margin-top: 10px;
    }
    .loader-inner {
        width: 0;
        height: 100%;
        background: #00ff00;
        animation: load 3s forwards;
    }
    @keyframes load {
        0% { width: 0; }
        100% { width: 100%; }
    }

    /* Welcome Screen */
    #welcome {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.88);
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        text-align: center;
        padding: 20px;
        z-index: 20;
    }
    #welcome h1 {
        color: #00ff00;
        font-size: 28px;
        font-weight: 700;
        font-family: 'Courier New', monospace;
        margin-bottom: 8px;
        text-shadow: 0 0 10px #00ff00;
    }
    #welcome p {
        color: #b3ffb3;
        font-size: 14px;
        margin-bottom: 18px;
        font-family: 'Courier New', monospace;
    }
    #startBtn {
        padding: 15px 30px;
        border-radius: 8px;
        border: 2px solid #00ff00;
        background: transparent;
        color: #00ff00;
        font-size: 18px;
        font-weight: 700;
        cursor: pointer;
        animation: pulse 1.5s infinite;
        font-family: 'Courier New', monospace;
    }

    /* Main UI */
    .header {
        text-align: center;
        margin-bottom: 20px;
    }
    .header h1 {
        color: #00ff00;
        font-size: 24px;
        font-weight: 700;
        font-family: 'Courier New', monospace;
        text-shadow: 0 0 10px #00ff00;
        margin-bottom: 6px;
    }
    .header p {
        color: #b3ffb3;
        font-size: 14px;
        font-family: 'Courier New', monospace;
    }

    .tabs {
        display: flex;
        gap: 8px;
        margin-bottom: 16px;
    }
    .tab {
        flex: 1;
        padding: 14px;
        border-radius: 8px;
        border: 1px solid #00ff00;
        background: rgba(0, 255, 0, 0.06);
        cursor: pointer;
        text-align: center;
        font-weight: 700;
        font-family: 'Courier New', monospace;
        color: #00ff00;
    }
    .tab.active {
        background: #00ff00;
        color: #000;
    }

    .plan-details {
        background: rgba(0, 255, 0, 0.06);
        padding: 15px;
        border-radius: 12px;
        margin-bottom: 15px;
        border: 1px solid rgba(0,255,0,0.3);
        font-family: 'Courier New', monospace;
    }
    .plan-details strong {
        font-size: 16px;
        font-weight: 700;
        color: #00ff00;
    }
    .plan-details p {
        margin: 8px 0;
        font-size: 14px;
        color: #b3ffb3;
    }

    .payment-box {
        background: rgba(0,0,0,0.7);
        border: 2px solid #00ff00;
        padding: 15px;
        border-radius: 12px;
        margin-bottom: 15px;
        font-family: 'Courier New', monospace;
    }
    .payment-box strong {
        font-weight: 700;
        font-size: 16px;
        color: #00ff00;
    }

    .pulseBtn {
        width: 100%;
        padding: 15px;
        border-radius: 8px;
        border: none;
        background: #00ff00;
        color: #000;
        font-size: 18px;
        font-weight: 700;
        cursor: pointer;
        animation: pulse 1.5s infinite;
        font-family: 'Courier New', monospace;
    }
    @keyframes pulse {
        0% { transform: scale(1); box-shadow: 0 0 0 0 rgba(0, 255, 0, 0.7); }
        70% { transform: scale(1.05); box-shadow: 0 0 0 15px rgba(0, 255, 0, 0); }
        100% { transform: scale(1); box-shadow: 0 0 0 0 rgba(0, 255, 0, 0); }
    }

    /* Progress bar */
    .progress {
        margin-top: 10px;
        height: 10px;
        border: 1px solid #00ff00;
        border-radius: 6px;
        background: rgba(0,0,0,0.5);
        overflow: hidden;
    }
    .progress-inner {
        height: 100%;
        width: 0;
        background: #00ff00;
        animation: loading 3s forwards;
    }
    @keyframes loading {
        0% { width: 0; }
        100% { width: 100%; }
    }

    /* Console typing */
    .console {
        margin-top: 12px;
        font-family: 'Courier New', monospace;
        font-size: 13px;
        color: #b3ffb3;
        padding: 10px;
        border: 1px solid rgba(0,255,0,0.3);
        border-radius: 10px;
        background: rgba(0,0,0,0.5);
    }
    .console .line {
        display: block;
        margin-bottom: 4px;
        opacity: 0;
    }

    /* Access granted */
    .access {
        margin-top: 10px;
        font-family: 'Courier New', monospace;
        font-size: 18px;
        color: #00ff00;
        text-align: center;
        display: none;
        animation: glow 1s infinite;
    }
    @keyframes glow {
        0% { text-shadow: 0 0 5px #00ff00; }
        50% { text-shadow: 0 0 20px #00ff00; }
        100% { text-shadow: 0 0 5px #00ff00; }
    }

    footer {
        margin-top: 18px;
        font-size: 12px;
        color: #94a3b8;
        text-align: center;
        font-family: 'Courier New', monospace;
    }
</style>
</head>
<body>
<canvas id="matrix-canvas"></canvas>

<div class="container">
    <!-- Loading Screen -->
    <div id="loading">
        <h1>LOADING</h1>
        <p>Initializing Marcellus VIP Server...</p>
        <div class="loader">
            <div class="loader-inner"></div>
        </div>
    </div>

    <!-- Welcome Screen -->
    <div id="welcome">
        <h1>WELCOME</h1>
        <p>Marcellus Aviator Signals VIP</p>
        <button id="startBtn">ENTER VIP</button>
    </div>

    <!-- Main Content -->
    <div class="header">
        <h1>Marcellus AVIATOR VIP</h1>
        <p>Choose your plan & pay via MPesa</p>
    </div>

    <div class="tabs">
        <div class="tab active" id="tab1" onclick="selectPlan(1)">Weekly</div>
        <div class="tab" id="tab2" onclick="selectPlan(2)">3 Weeks</div>
    </div>

    <div class="plan-details" id="planDetails">
        <strong>Weekly Plan</strong>
        <p>• Price: Ksh 500</p>
        <p>• Live Aviator signals daily</p>
        <p>• VIP WhatsApp access</p>
    </div>

    <div class="payment-box">
        <strong>Pay via MPesa:</strong>
        <p><strong>+254797124175</strong></p>
        <p>After payment, click JOIN VIP to send proof on WhatsApp.</p>
        <div class="progress"><div class="progress-inner"></div></div>
        <div class="console" id="console">
            <span class="line">Initializing connection...</span>
            <span class="line">Scanning signal network...</span>
            <span class="line">Accessing VIP server...</span>
        </div>
        <div class="access" id="access">ACCESS GRANTED</div>
    </div>

    <button class="pulseBtn" onclick="redirectWhatsApp()">JOIN VIP</button>

    <footer>© 2026 Marcellus</footer>
</div>

<script>
    let selectedPlan = 1;

    // Show Welcome after loading
    window.onload = function() {
        setTimeout(() => {
            document.getElementById('loading').style.display = 'none';
            document.getElementById('welcome').style.display = 'flex';
        }, 3000);
    };

    // Welcome screen
    document.getElementById('startBtn').addEventListener('click', () => {
        document.getElementById('welcome').style.display = 'none';
        startConsole();
    });

    // Plan selection
    function selectPlan(plan) {
        selectedPlan = plan;
        const tab1 = document.getElementById('tab1');
        const tab2 = document.getElementById('tab2');
        const details = document.getElementById('planDetails');

        if (plan === 1) {
            tab1.classList.add('active');
            tab2.classList.remove('active');
            details.innerHTML = `
                <strong>Weekly Plan</strong>
                <p>• Price: Ksh 500</p>
                <p>• Live Aviator signals daily</p>
                <p>• VIP WhatsApp access</p>
            `;
        } else {
            tab2.classList.add('active');
            tab1.classList.remove('active');
            details.innerHTML = `
                <strong>3 Weeks Plan</strong>
                <p>• Price: Ksh 1,500</p>
                <p>• Live Aviator signals daily</p>
                <p>• VIP WhatsApp access</p>
                <p>• Best value</p>
            `;
        }
    }

    // WhatsApp redirect
    function redirectWhatsApp() {
        const number = '251105285185';
        const message = selectedPlan === 1
            ? 'Hello, I paid Ksh 500 for the Weekly plan. Please confirm.'
            : 'Hello, I paid Ksh 1,500 for the 3 Weeks plan. Please confirm.';

        window.location.href = `https://wa.me/${number}?text=${encodeURIComponent(message)}`;
    }

    // Console typing effect
    function startConsole() {
        const lines = document.querySelectorAll('.console .line');
        let idx = 0;
        lines.forEach(line => line.style.opacity = 0);

        const interval = setInterval(() => {
            if (idx >= lines.length) {
                clearInterval(interval);
                document.getElementById('access').style.display = 'block';
                return;
            }
            lines[idx].style.opacity = 1;
            idx++;
        }, 700);
    }

    // Matrix rain
    const canvas = document.getElementById('matrix-canvas');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
    const fontSize = 14;
    const columns = canvas.width / fontSize;
    const drops = Array(Math.floor(columns)).fill(1);

    function draw() {
        ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        ctx.fillStyle = "#00ff00";
        ctx.font = fontSize + "px monospace";

        for (let i = 0; i < drops.length; i++) {
            const text = alphabet.charAt(Math.floor(Math.random() * alphabet.length));
            ctx.fillText(text, i * fontSize, drops[i] * fontSize);
            if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
                drops[i] = 0;
            }
            drops[i]++;
        }
    }
    setInterval(draw, 50);

    window.addEventListener('resize', () => {
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
    });
</script>
</body>

</html>
