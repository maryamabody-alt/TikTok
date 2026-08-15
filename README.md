<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>🎉 عيد ميلاد حبيبتي 🎉</title>
    <style>
        /* إعادة تعيين كامل */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html, body {
            width: 100%;
            height: 100%;
            overflow: hidden;
            background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
            font-family: 'Arial', cursive, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            touch-action: none;
        }

        /* البطاقة */
        .card {
            width: 100%;
            height: 100vh;
            padding: 30px 20px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(5px);
            position: relative;
            z-index: 10;
            animation: fadeIn 2s ease;
            overflow-y: auto;
        }

        @keyframes fadeIn {
            0% { opacity: 0; transform: scale(0.9); }
            100% { opacity: 1; transform: scale(1); }
        }

        .emoji-big {
            font-size: 70px;
            display: block;
            margin-bottom: 5px;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        h1 {
            color: #fff;
            font-size: 28px;
            font-weight: 900;
            background: linear-gradient(45deg, #f7971e, #ffd200);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            display: inline-block;
        }

        .subtitle {
            color: #ff6b9d;
            font-size: 22px;
            font-weight: bold;
            margin: 5px 0 10px;
            text-shadow: 0 0 30px #ff6b9d;
        }

        .message {
            color: #e0e0e0;
            font-size: 18px;
            line-height: 2.2;
            max-width: 550px;
            margin: 10px 0 20px;
            direction: rtl;
            padding: 0 10px;
        }

        .message i {
            color: #ff6b9d;
        }

        /* القلوب المتساقطة */
        .heart-rain {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 999;
            overflow: hidden;
        }

        .heart {
            position: absolute;
            font-size: 22px;
            animation: fall linear infinite;
            opacity: 0.6;
            user-select: none;
        }

        @keyframes fall {
            0% { transform: translateY(-10vh) rotate(0deg) scale(1); opacity: 0.8; }
            100% { transform: translateY(110vh) rotate(720deg) scale(0.2); opacity: 0; }
        }

        .balloon {
            font-size: 50px;
            display: inline-block;
            animation: float 3s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-12px); }
        }

        .btn-music {
            background: rgba(255, 255, 255, 0.08);
            border: 1px solid rgba(255, 255, 255, 0.15);
            color: #fff;
            padding: 12px 30px;
            border-radius: 50px;
            font-size: 16px;
            cursor: pointer;
            transition: 0.3s;
            margin: 10px 0 5px;
            touch-action: manipulation;
        }

        .btn-music:active {
            transform: scale(0.95);
        }

        .footer {
            color: #888;
            font-size: 14px;
            margin-top: 10px;
            opacity: 0.5;
            direction: rtl;
        }

        /* تنسيق للجوال فقط */
        @media (max-width: 480px) {
            h1 { font-size: 22px; }
            .subtitle { font-size: 18px; }
            .message { font-size: 16px; line-height: 2; padding: 0 5px; }
            .emoji-big { font-size: 55px; }
            .balloon { font-size: 40px; }
            .btn-music { padding: 10px 20px; font-size: 14px; }
            .heart { font-size: 18px; }
        }

        @media (max-width: 380px) {
            h1 { font-size: 18px; }
            .message { font-size: 14px; line-height: 1.9; }
            .emoji-big { font-size: 45px; }
        }
    </style>
</head>
<body>

<!-- قلوب متساقطة -->
<div class="heart-rain" id="heartRain"></div>

<!-- البطاقة -->
<div class="card">
    <span class="emoji-big">🎂</span>
    <h1>🎉 عيد ميلاد حبيبتي 🎉</h1>
    <div class="subtitle">💖 يا روحي 💖</div>

    <div class="message">
        <i>❤️ كل عام وأنتي نور عيوني ❤️</i><br><br>
        اليوم يومج .. يوم الفرحة اللي ما تفارق وجهج 🌸<br>
        كل سنة وأنتي طيبة .. وكل سنة وأجمالج تزيد 😍<br>
        أنتي مثل الورد .. كل ما أشوفج تفتح النفسية 💫<br>
        وعيونج .. يا عيونج .. لو تغيب الدنيا كلها، تبقين أنتي الدنيا بحق ❤️<br><br>
        اليوم الك .. والقلب الك .. وكل الحب الك 💞<br>
        ما أريد غير فرحتج .. ولو أطلب من الله سنة وحدة، أطلبها تكون معاج 🙏<br><br>
        يا روحي .. يا نبض قلبي .. يا أجمل شي صار بحياتي ❤️<br>
        كل سنة وأنتي ملكتي .. وكل سنة وأنتي حبيبتي 🌹<br>
        كل سنة وأنتي عمري الجاي .. وكل سنة وأنا أحبج أكثر 💖<br><br>
        ما عندي هدية أغلى من دعائي الك .. ربنا يحفظج ويخليج لي 🤲<br>
        وكل عام وأنتي بخير يا أحلى بنت بالدنيا 💕
    </div>

    <div>
        <span class="balloon">🎈</span>
        <span class="balloon" style="animation-delay:0.5s;">🎈</span>
        <span class="balloon" style="animation-delay:1s;">🎈</span>
        <span class="balloon" style="animation-delay:1.5s;">🎈</span>
        <span class="balloon" style="animation-delay:2s;">🎈</span>
    </div>

    <button class="btn-music" id="musicBtn">🎵 شغّل الموسيقى 🎵</button>

    <div class="footer">
        ❤️ من قلب يحبك .. إلى أغلى إنسانة بحياتي ❤️
    </div>
</div>

<script>
// ==========================================
// 1. القلوب المتساقطة
// ==========================================
function createHearts() {
    const container = document.getElementById('heartRain');
    const emojis = ['❤️', '💖', '💗', '💓', '💕', '💘', '💝', '♥️', '💛', '🧡'];
    const colors = ['#ff6b9d', '#ff3366', '#ff1493', '#ff4d6d', '#ff8c9e', '#ffb3c6', '#ff69b4'];

    for (let i = 0; i < 120; i++) {
        const heart = document.createElement('div');
        heart.className = 'heart';
        heart.textContent = emojis[Math.floor(Math.random() * emojis.length)];
        heart.style.left = Math.random() * 100 + '%';
        heart.style.fontSize = (Math.random() * 18 + 14) + 'px';
        heart.style.animationDuration = (Math.random() * 5 + 6) + 's';
        heart.style.animationDelay = (Math.random() * 15) + 's';
        heart.style.color = colors[Math.floor(Math.random() * colors.length)];
        container.appendChild(heart);
    }
}

// ==========================================
// 2. الموسيقى
// ==========================================
let audioCtx = null;
let isPlaying = false;

function playHappyBirthday() {
    if (audioCtx === null) {
        audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    }

    if (isPlaying) {
        isPlaying = false;
        document.getElementById('musicBtn').textContent = '🎵 شغّل الموسيقى 🎵';
        return;
    }

    isPlaying = true;
    document.getElementById('musicBtn').textContent = '⏹️ أوقف الموسيقى';

    const notes = [
        { freq: 262, dur: 0.3 }, { freq: 262, dur: 0.3 },
        { freq: 294, dur: 0.5 }, { freq: 262, dur: 0.5 },
        { freq: 349, dur: 0.5 }, { freq: 330, dur: 0.6 },
        { freq: 262, dur: 0.3 }, { freq: 262, dur: 0.3 },
        { freq: 294, dur: 0.5 }, { freq: 262, dur: 0.5 },
        { freq: 392, dur: 0.5 }, { freq: 349, dur: 0.6 },
        { freq: 262, dur: 0.3 }, { freq: 262, dur: 0.3 },
        { freq: 523, dur: 0.5 }, { freq: 440, dur: 0.5 },
        { freq: 349, dur: 0.5 }, { freq: 330, dur: 0.5 },
        { freq: 294, dur: 0.6 }
    ];

    let time = 0;
    for (let note of notes) {
        setTimeout(() => {
            if (!isPlaying) return;
            const osc = audioCtx.createOscillator();
            const gain = audioCtx.createGain();
            osc.type = 'sine';
            osc.frequency.value = note.freq;
            gain.gain.setValueAtTime(0.12, audioCtx.currentTime);
            gain.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + note.dur);
            osc.connect(gain);
            gain.connect(audioCtx.destination);
            osc.start();
            osc.stop(audioCtx.currentTime + note.dur);
        }, time * 1000);
        time += note.dur + 0.05;
    }
}

// ==========================================
// 3. تشغيل Fullscreen عند النقر
// ==========================================
function goFullscreen() {
    const el = document.documentElement;
    if (el.requestFullscreen) {
        el.requestFullscreen();
    } else if (el.webkitRequestFullscreen) {
        el.webkitRequestFullscreen();
    } else if (el.msRequestFullscreen) {
        el.msRequestFullscreen();
    }
}

// طلب Fullscreen عند أي تفاعل
document.addEventListener('click', goFullscreen);
document.addEventListener('touchstart', goFullscreen);

// ==========================================
// 4. تحميل الصفحة
// ==========================================
window.onload = function() {
    createHearts();
    document.getElementById('musicBtn').addEventListener('click', playHappyBirthday);
};
</script>
</body>
</html>
