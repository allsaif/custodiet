<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Custodiet – قيد الإطلاق</title>
  <meta name="description" content="Custodiet – Who Watches the Threats? منصة رصد التهديدات العالمية في الوقت الفعلي – قيد التطوير"/>
  
  <style>
    :root {
      --bg: #0a0e17;
      --text: #f1f5f9;
      --accent: #60a5fa;
      --success: #34d399;
      --card: #1e293b;
    }
    body {
      margin: 0;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
      background: linear-gradient(to bottom, var(--bg), #111827);
      color: var(--text);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 20px;
      box-sizing: border-box;
    }
    .lang-switch {
      position: absolute;
      top: 20px;
      right: 20px;
      display: flex;
      gap: 10px;
      z-index: 10;
    }
    .lang-btn {
      background: rgba(255,255,255,0.1);
      border: 1px solid rgba(255,255,255,0.2);
      color: var(--text);
      padding: 8px 14px;
      border-radius: 6px;
      cursor: pointer;
      font-size: 0.95rem;
      transition: all 0.2s;
    }
    .lang-btn:hover,
    .lang-btn.active {
      background: var(--accent);
      border-color: var(--accent);
      color: #000;
    }
    h1 {
      font-size: clamp(2.8rem, 8vw, 5.5rem);
      margin: 0.5rem 0;
      color: var(--accent);
      font-weight: 800;
      letter-spacing: -1px;
    }
    .tagline {
      font-size: clamp(1.4rem, 5vw, 2.2rem);
      color: var(--success);
      margin: 1rem 0 2rem;
      font-weight: 500;
    }
    .desc {
      font-size: clamp(1.1rem, 4vw, 1.4rem);
      max-width: 720px;
      line-height: 1.6;
      margin: 0 auto 2.5rem;
      opacity: 0.92;
    }
    .coming-soon {
      font-size: 1.5rem;
      color: #fbbf24;
      margin: 2rem 0;
      padding: 12px 28px;
      border: 2px dashed #fbbf24;
      border-radius: 12px;
      display: inline-block;
    }
    .footer {
      position: absolute;
      bottom: 2rem;
      font-size: 0.95rem;
      opacity: 0.6;
    }

    /* التبديل إلى اليسار للغات غير العربية */
    [lang="en"] body,
    [lang="de"] body {
      direction: ltr;
      text-align: center;
    }

    @media (max-width: 640px) {
      h1 { font-size: 3.2rem; }
      .tagline { font-size: 1.6rem; }
      .desc { font-size: 1.15rem; }
    }
  </style>
</head>
<body>

  <!-- أزرار تغيير اللغة -->
  <div class="lang-switch">
    <button class="lang-btn active" data-lang="ar">العربية</button>
    <button class="lang-btn" data-lang="en">English</button>
    <button class="lang-btn" data-lang="de">Deutsch</button>
  </div>

  <h1 data-key="title">Custodiet</h1>
  
  <div class="tagline" data-key="tagline">
    Who Watches the Threats?
  </div>

  <p class="desc" data-key="description">
    منصة رصد التهديدات العالمية في الوقت الفعلي<br>
    ذكاء مفتوح المصدر – شفافية كاملة – يقظة مستمرة
  </p>

  <div class="coming-soon" data-key="coming">
    قيد التطوير – Coming Soon – In Entwicklung
  </div>

  <div class="footer">
    © 2026 Custodiet • custodiet.io & custodiet.app
  </div>

  <script>
    const translations = {
      ar: {
        title: "Custodiet",
        tagline: "من يراقب التهديدات؟",
        description: "منصة رصد التهديدات العالمية في الوقت الفعلي\nذكاء مفتوح المصدر – شفافية كاملة – يقظة مستمرة",
        coming: "قيد التطوير – Coming Soon – In Entwicklung"
      },
      en: {
        title: "Custodiet",
        tagline: "Who Watches the Threats?",
        description: "Real-time global threat monitoring platform\nOpen-source intelligence – Full transparency – Continuous vigilance",
        coming: "Under Development – Coming Soon – In Entwicklung"
      },
      de: {
        title: "Custodiet",
        tagline: "Wer überwacht die Bedrohungen?",
        description: "Plattform zur Echtzeit-Überwachung globaler Bedrohungen\nOpen-Source-Intelligence – Volle Transparenz – Kontinuierliche Wachsamkeit",
        coming: "In Entwicklung – Coming Soon – In Entwicklung"
      }
    };

    const langButtons = document.querySelectorAll('.lang-btn');
    const html = document.documentElement;

    function setLanguage(lang) {
      html.lang = lang;
      html.dir = lang === 'ar' ? 'rtl' : 'ltr';

      document.querySelectorAll('[data-key]').forEach(el => {
        const key = el.dataset.key;
        if (translations[lang][key]) {
          el.textContent = translations[lang][key];
        }
      });

      langButtons.forEach(btn => {
        btn.classList.toggle('active', btn.dataset.lang === lang);
      });
    }

    // تحميل اللغة المحفوظة أو الافتراضية (العربية)
    const savedLang = localStorage.getItem('custodiet-lang') || 'ar';
    setLanguage(savedLang);

    // تغيير اللغة عند الضغط
    langButtons.forEach(btn => {
      btn.addEventListener('click', () => {
        const lang = btn.dataset.lang;
        setLanguage(lang);
        localStorage.setItem('custodiet-lang', lang);
      });
    });
  </script>
</body>
</html>
