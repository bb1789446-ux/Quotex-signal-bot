# Quotex-signal-bot
Trading bot 
<!DOCTYPE html><html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Quotex Signal App</title>
<style>
    body {
        margin: 0;
        padding: 0;
        background: #000;
        font-family: Arial, sans-serif;
        color: #fff;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
        overflow: hidden;
    }h1 {
    font-size: 28px;
    text-shadow: 0 0 15px #0ff;
    margin-bottom: 20px;
}

.signal-box {
    width: 90%;
    max-width: 380px;
    padding: 20px;
    background: rgba(0, 0, 0, 0.7);
    border: 2px solid #0ff;
    border-radius: 15px;
    box-shadow: 0 0 25px #0ff;
    text-align: center;
    margin-bottom: 20px;
}

.signal-type {
    font-size: 22px;
    margin-bottom: 10px;
    text-shadow: 0 0 10px #0ff;
}

.btn {
    width: 90%;
    max-width: 300px;
    padding: 15px;
    margin: 10px;
    border: 2px solid #0ff;
    border-radius: 12px;
    font-size: 20px;
    background: transparent;
    color: #0ff;
    text-shadow: 0 0 10px #0ff;
    cursor: pointer;
    transition: 0.2s;
    box-shadow: 0 0 15px #0ff;
}

.btn:active {
    transform: scale(0.9);
    box-shadow: 0 0 30px #0ff;
}

.buy { border-color: #0f0; color: #0f0; box-shadow: 0 0 15px #0f0; }
.sell { border-color: #f00; color: #f00; box-shadow: 0 0 15px #f00; }

</style>
<link rel="manifest" href="data:application/json,{\"name\":\"Quotex Neon App\",\"short_name\":\"QSignals\",\"start_url\":\"./\",\"display\":\"standalone\",\"background_color\":\"#000000\",\"theme_color\":\"#000000\",\"icons\":[{\"src\":\"https://cdn-icons-png.flaticon.com/512/833/833472.png\",\"sizes\":\"512x512\",\"type\":\"image/png\"}]}" />
<script>
// Dynamic Service Worker
const swCode = `self.addEventListener('install',e=>self.skipWaiting());self.addEventListener('activate',e=>clients.claim());`;
const blob = new Blob([swCode], { type: 'text/javascript' });
navigator.serviceWorker.register(URL.createObjectURL(blob));
</script>
</head>
<body><h1>Neon Quotex Signals</h1><div class="signal-box">
    <div id="signal" class="signal-type">Waiting for signal...</div>
    <div id="confidence">Confidence: --%</div>
</div><button class="btn buy" onclick="openQuotex('buy')">BUY</button> <button class="btn sell" onclick="openQuotex('sell')">SELL</button>

<script>
    function randomSignal() {
        const signals = ["BUY", "SELL"];
        let pick = signals[Math.floor(Math.random() * signals.length)];
        let confidence = Math.floor(Math.random() * (95 - 70 + 1)) + 70;

        document.getElementById("signal").innerText = pick;
        document.getElementById("confidence").innerText = "Confidence: " + confidence + "%";
    }

    setInterval(randomSignal, 5000);

    function openQuotex(type) {
        window.open("https://quotex.com", "_blank");
    }
</script><script>
// Fullscreen Android mode
if (window.navigator.standalone || window.matchMedia('(display-mode: standalone)').matches) {
    document.body.style.height = '100vh';
}
</script></body>
</html>
