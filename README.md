<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>سياسة الخصوصية - شات بوت</title>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700&display=swap" rel="stylesheet" />
    <style>
        /* Reset & base */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Tajawal', sans-serif;
            background: linear-gradient(135deg, #1a1a2e, #16213e, #0f3460);
            padding: 20px;
        }

        /* Glass card – مطابق للطلب (زجاجي حقيقي) */
        .glass-card {
            max-width: 850px;
            width: 100%;
            background: rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(20px) saturate(180%);
            -webkit-backdrop-filter: blur(20px) saturate(180%);
            border-radius: 40px;
            border: 1px solid rgba(255, 255, 255, 0.15);
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.5), inset 0 1px 0 rgba(255, 255, 255, 0.1);
            padding: 35px 30px 30px;
            color: #f0f4ff;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        /* إضافة تأثير زجاجي إضافي */
        .glass-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle at 30% 10%, rgba(255, 255, 255, 0.05) 0%, transparent 60%);
            pointer-events: none;
        }

        /* الملف الشخصي (الصورة الدائرية + العنوان + زر الصوت) */
        .profile-section {
            display: flex;
            align-items: center;
            gap: 18px;
            margin-bottom: 20px;
            position: relative;
            z-index: 1;
        }

        .profile-avatar {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            border: 2px solid rgba(255, 255, 255, 0.25);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.4);
            object-fit: cover;
            background: #2a2a4a;
            flex-shrink: 0;
        }

        .header-text {
            flex: 1;
        }

        .header-text h1 {
            font-size: 1.8rem;
            font-weight: 700;
            letter-spacing: 0.5px;
            background: linear-gradient(to left, #f0e6ff, #b8a9ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-shadow: 0 2px 10px rgba(100, 80, 255, 0.3);
            margin: 0;
        }

        .header-text .sub-date {
            font-size: 0.95rem;
            opacity: 0.7;
            font-weight: 400;
            margin-top: 4px;
        }

        /* زر قراءة النص (صغير في الأعلى) */
        .read-btn {
            background: rgba(255, 255, 255, 0.08);
            border: 1px solid rgba(255, 255, 255, 0.2);
            color: #fff;
            width: 44px;
            height: 44px;
            border-radius: 50%;
            font-size: 1.3rem;
            cursor: pointer;
            backdrop-filter: blur(4px);
            transition: 0.25s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
            margin-right: auto;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        }
        .read-btn:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: scale(1.05);
            border-color: rgba(255, 255, 255, 0.4);
        }
        .read-btn:active {
            transform: scale(0.95);
        }
        .read-btn svg {
            width: 24px;
            height: 24px;
            fill: currentColor;
        }

        /* محتوى السياسة – النص الأصلي بدون تغيير */
        .policy-content {
            position: relative;
            z-index: 1;
            margin: 10px 0 18px;
            line-height: 1.8;
            font-size: 1rem;
            max-height: 70vh;
            overflow-y: auto;
            padding-left: 6px;
            padding-right: 6px;
            scrollbar-width: thin;
            scrollbar-color: rgba(255,255,255,0.15) transparent;
        }
        .policy-content::-webkit-scrollbar {
            width: 5px;
        }
        .policy-content::-webkit-scrollbar-track {
            background: transparent;
        }
        .policy-content::-webkit-scrollbar-thumb {
            background: rgba(255,255,255,0.2);
            border-radius: 10px;
        }

        /* الحفاظ على تنسيق العناوين كما هي */
        .policy-content h1,
        .policy-content h6,
        .policy-content h3 {
            color: #f0f4ff;
            margin: 0.8em 0 0.4em;
            font-weight: 600;
        }
        .policy-content h1 {
            font-size: 1.6rem;
            background: linear-gradient(to left, #f0e6ff, #b8a9ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        .policy-content h6 {
            font-size: 1rem;
            font-weight: 400;
            line-height: 1.8;
            color: #e0e8ff;
        }
        .policy-content h3 {
            font-size: 1.1rem;
            opacity: 0.85;
        }
        .policy-content p {
            margin: 0.5em 0;
        }

        /* زر البريد الإلكتروني في الأسفل */
        .footer-actions {
            display: flex;
            justify-content: center;
            margin-top: 12px;
            position: relative;
            z-index: 1;
        }

        .email-btn {
            display: inline-flex;
            align-items: center;
            gap: 12px;
            background: rgba(255, 255, 255, 0.06);
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
            border: 1px solid rgba(255, 255, 255, 0.15);
            padding: 14px 32px;
            border-radius: 60px;
            color: #fff;
            font-size: 1.1rem;
            font-weight: 500;
            text-decoration: none;
            transition: 0.25s ease;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
            letter-spacing: 0.3px;
        }
        .email-btn:hover {
            background: rgba(255, 255, 255, 0.14);
            transform: translateY(-2px);
            border-color: rgba(255, 255, 255, 0.3);
            box-shadow: 0 12px 35px rgba(0, 0, 0, 0.5);
        }
        .email-btn:active {
            transform: translateY(1px);
        }
        .email-btn svg {
            width: 24px;
            height: 24px;
            fill: currentColor;
            opacity: 0.8;
        }
        .email-btn .email-text {
            direction: ltr;
            unicode-bidi: embed;
        }

        /* استجابة للشاشات الصغيرة */
        @media (max-width: 600px) {
            .glass-card {
                padding: 20px 18px;
            }
            .profile-section {
                flex-wrap: wrap;
            }
            .header-text h1 {
                font-size: 1.4rem;
            }
            .profile-avatar {
                width: 60px;
                height: 60px;
            }
            .read-btn {
                width: 38px;
                height: 38px;
                font-size: 1.1rem;
            }
            .email-btn {
                padding: 12px 22px;
                font-size: 1rem;
            }
        }
    </style>
</head>
<body>
    <div class="glass-card">

        <!-- الملف الشخصي: الصورة الدائرية + العنوان + زر الصوت -->
        <div class="profile-section">
            <img 
                class="profile-avatar" 
                src="bfd8c880-8807-11f1-8108-b3a8e4e1fe89.png" 
                alt="شعار البوت" 
                loading="lazy"
                onerror="this.style.display='none'"
            />
            <div class="header-text">
                <h1>سياسات والخصوصية شات بوت</h1>
                <div class="sub-date">الإثنين 10 اغسطس 2026</div>
            </div>
            <button class="read-btn" id="readAloudBtn" type="button" aria-label="قراءة النص بصوت">
                <svg viewBox="0 0 24 24"><path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/></svg>
            </button>
        </div>

        <!-- محتوى السياسة – النص الأصلي كما هو (بدون تغيير) -->
        <div class="policy-content" id="policyText">
            <h6>سياسة الخصوصية لبوت [Chatbot]

آخر تحديث: [الثلاثاء 28 يوليوز 2026]

مرحباً بك في بوت [Chatbot]. نحن نلتزم بحماية خصوصيتك وشفافية التعامل مع بياناتك. توضح هذه السياسة كيفية جمع معلوماتك واستخدامها وحمايتها عند تفاعلك مع بوتنا عبر فيسبوك ماسنجر.

1. المعلومات التي نجمعها

عند استخدامك للبوت، قد نقوم بجمع:

· المعلومات الأساسية: معرف المستخدم الخاص بالصفحة (PSID)،والاسم العام لملفك الشخصي على فيسبوك.
· محتويات المحادثة: الرسائل التي ترسلها للبوت، والأسئلة التي تطرحها، والتعليمات التي تقدمها.
· بيانات التفاعل: سجل نقاطك، وتاريخ ووقت المحادثات، وعدد المرات التي تستخدم فيها البوت.

2. كيف نستخدم معلوماتك

نستخدم البيانات التي نجمعها للأغراض التالية:

· تشغيل البوت وتحسينه: لتقديم ردود دقيقة، وتحليل أنماط المحادثة لتطوير أداء البوت.
· تخصيص التجربة: لتذكر تفضيلاتك وسجل محادثاتك السابقة، وجعل التفاعل أكثر سلاسة.
· إدارة نظام النقاط: لتتبع نقاطك وتحديث رصيدك، ومنحك المكافآت التي تزيد من فرصك في التحدث.
· مراقبة الجودة والامتثال: لضمان الالتزام بسياسة الاستخدام، واكتشاف أي إساءة أو انتهاك للقوانين.

3. محاكاة السلوك البشري

يعمل بوت [Chatbot] بتقنيات الذكاء الاصطناعي المصممة لمحاكاة المحادثة البشرية. هذا يعني:

· البوت ليس إنساناً، بل برنامج يهدف لجعل تفاعلك طبيعياً وسلساً.
· يتم تحليل مدخلاتك لتوليد ردود تشبه ردود البشر، لكن جميع الردود يتم إنشاؤها آلياً.
· رغم محاولتنا تقديم تجربة شبيهة بالبشر، لا يمكن اعتبار البوت بديلاً عن الاستشارات البشرية في الأمور الحساسة (كالصحية أو القانونية).

4. نظام النقاط وزيادة فرص التحدث

لبوتنا نظام نقاط يحفز التفاعل:

· كسب النقاط: يمكنك ربح نقاط عبر التفاعل مع البوت، أو إنجاز مهام محددة، أو المشاركة في أنشطة يعلن عنها البوت.
· استخدام النقاط: تمنحك النقاط مزايا إضافية، مثل زيادة أولوية الردود، أو الحصول على محتوى حصري، أو فترات محادثة أطول.
· ملاحظة: النقاط ليس لها قيمة نقدية، ولا يمكن استبدالها بأموال حقيقية، وهي خاصة بحسابك ولا تُنقل للآخرين.

5. الحظر (الBan) وإنهاء الخدمة

لضمان بيئة آمنة ومحترمة، نحتفظ بالحق في حظر أي مستخدم بشكل مؤقت أو دائم في الحالات التالية:

· إساءة الاستخدام: استخدام ألفاظ بذيئة، أو مضايقة، أو محاولة اختراق البوت.
· انتهاك الشروط: محاولة التلاعب بنظام النقاط، أو استخدام البوت لأغراض غير قانونية.
· الطلبات المتكررة: إرسال كم هائل من الرسائل بهدف تعطيل الخدمة (ما يعرف بهجمات الإغراق).
في حال حظر حسابك، قد تفقد نقاطك وإمكانية الوصول للبوت. يمكنك التواصل معنا للاعتراض على قرار الحظر.

6. مشاركة البيانات مع أطراف ثالثة

· لا نبيع معلوماتك الشخصية أو محادثاتك لأي طرف ثالث.
· قد نشارك بيانات مجمعة وغير قابلة للتعريف (مثل إحصاءات الاستخدام) مع شركاء تقنيين لتحسين البوت.
· نظراً لأن البوت يعمل على منصة فيسبوك ماسنجر، فإن سياسة خصوصية ميتا تنطبق أيضاً على تفاعلك، وقد تستخدم ميتا بيانات التفاعل لأغراضها (كتحسين الإعلانات) وفقاً لسياساتها.

7. حماية بياناتك وتخزينها

· نتخذ إجراءات أمنية معقولة لحماية بياناتك من الوصول غير المصرح به.
· قد نحتفظ بسجل المحادثات لفترة محدودة لتحسين البوت، ثم نقوم بحذفها أو إخفاء هويتها بشكل دائم.
· رغم جهودنا، لا يمكن ضمان أمن البيانات بنسبة 100% عند نقلها عبر الإنترنت.

8. حقوقك

لديك الحق في:

· طلب حذف بياناتك: يمكنك التواصل معنا لطلب حذف معلوماتك المخزنة.
· الانسحاب من نظام النقاط: يمكنك إلغاء المشاركة في نظام النقاط في أي وقت.
· الوصول إلى بياناتك: يمكنك طلب نسخة من البيانات التي لدينا عنك.

9. التواصل معنا

للاستفسارات حول هذه السياسة، أو لحذف بياناتك، أو للاعتراض على قرار حظر، يرجى التواصل معنا 

10. التعديل على السياسة

قد نقوم بتحديث هذه السياسة من وقت لآخر. سنخطرك بأي تغييرات جوهرية عبر البوت أو صفحتنا على فيسبوك. استمرارك باستخدام البوت بعد التعديل يعني موافقتك على السياسة المحدثة.

إشعار حقوق الملكية
جميع المحتويات المنشورة على صفحة Chatbot من صور، فيديوهات، نصوص، وتصاميم مولدة بواسطة أدوات الذكاء الاصطناعي المملوكة للصفحة هي ملك فكري حصري لصفحة Chatbot.
يُحظر إعادة نشرها أو استخدامها تجارياً بدون إذن خطي مسبق من إدارة الصفحة. © 2026</h6>

<h3>الإثنين 10 اغسطس 2026</h3>

<h3>جميع الحقوق محفوظه لهذا البوت</h3>
        </div>

        <!-- زر البريد الإلكتروني في الأسفل (قابل للنقر) -->
        <div class="footer-actions">
            <a href="mailto:contactchatbot1@gmail.com" class="email-btn">
                <svg viewBox="0 0 24 24"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg>
                <span class="email-text">contactchatbot1@gmail.com</span>
            </a>
        </div>

    </div>

    <script>
        (function() {
            const readBtn = document.getElementById('readAloudBtn');
            const policyDiv = document.getElementById('policyText');
            let isReading = false;
            let utterance = null;

            function getPolicyText() {
                return policyDiv.innerText;
            }

            function speakText() {
                if (isReading) {
                    window.speechSynthesis.cancel();
                    isReading = false;
                    readBtn.innerHTML = `<svg viewBox="0 0 24 24"><path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/></svg>`;
                    return;
                }

                const text = getPolicyText().trim();
                if (!text) return;

                utterance = new SpeechSynthesisUtterance(text);
                utterance.lang = 'ar-SA';
                utterance.rate = 0.9;
                utterance.pitch = 1;
                utterance.volume = 1;

                utterance.onstart = function() {
                    isReading = true;
                    readBtn.innerHTML = `<svg viewBox="0 0 24 24"><path d="M6 19h4V5H6v14zm8-14v14h4V5h-4z"/></svg>`;
                };

                utterance.onend = function() {
                    isReading = false;
                    readBtn.innerHTML = `<svg viewBox="0 0 24 24"><path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/></svg>`;
                };

                utterance.onerror = function() {
                    isReading = false;
                    readBtn.innerHTML = `<svg viewBox="0 0 24 24"><path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/></svg>`;
                };

                window.speechSynthesis.speak(utterance);
            }

            readBtn.addEventListener('click', speakText);
        })();
    </script>
</body>
</html>
