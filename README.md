<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes" />
    <title>سياسة الخصوصية - شات بوت</title>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700&display=swap" rel="stylesheet" />
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Tajawal', 'Segoe UI', system-ui, sans-serif;
            background: #f5f7fa;
            padding: 16px;
            /* تحسين للشاشات الصغيرة */
            margin: 0;
        }

        /* البطاقة الزجاجية – خلفية شفافة مع blur */
        .glass-card {
            max-width: 850px;
            width: 100%;
            background: rgba(255, 255, 255, 0.6);
            /* دعم أفضل لأندرويد */
            backdrop-filter: blur(24px) saturate(200%);
            -webkit-backdrop-filter: blur(24px) saturate(200%);
            border-radius: 40px;
            border: 1px solid rgba(255, 255, 255, 0.7);
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.10), inset 0 1px 0 rgba(255, 255, 255, 0.8);
            padding: 28px 24px 24px;
            color: #0f172a;
            transition: all 0.2s ease;
            position: relative;
            overflow: hidden;
        }

        /* تأثير إضافي */
        .glass-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle at 30% 10%, rgba(255, 255, 255, 0.35) 0%, transparent 60%);
            pointer-events: none;
        }

        /* الملف الشخصي */
        .profile-section {
            display: flex;
            align-items: center;
            gap: 14px;
            margin-bottom: 18px;
            position: relative;
            z-index: 1;
            flex-wrap: wrap;
        }

        .profile-avatar {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            border: 2px solid rgba(255, 255, 255, 0.6);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.08);
            object-fit: cover;
            background: #e2e8f0;
            flex-shrink: 0;
            /* منع التمدد */
            max-width: 70px;
        }

        .header-text {
            flex: 1;
            min-width: 120px;
        }

        .header-text h1 {
            font-size: clamp(1.3rem, 5vw, 1.8rem);
            font-weight: 700;
            letter-spacing: 0.3px;
            color: #0f172a;
            margin: 0;
            line-height: 1.2;
        }

        .header-text .sub-date {
            font-size: clamp(0.75rem, 2vw, 0.95rem);
            opacity: 0.6;
            font-weight: 400;
            margin-top: 2px;
            color: #334155;
        }

        /* زر الصوت – حجم مناسب للأندرويد */
        .read-btn {
            background: rgba(255, 255, 255, 0.5);
            border: 1px solid rgba(255, 255, 255, 0.8);
            color: #1e293b;
            width: 48px;
            height: 48px;
            border-radius: 50%;
            font-size: 1.2rem;
            cursor: pointer;
            backdrop-filter: blur(4px);
            -webkit-backdrop-filter: blur(4px);
            transition: 0.2s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
            margin-right: auto;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
            /* تحسين اللمس */
            touch-action: manipulation;
            user-select: none;
            -webkit-user-select: none;
        }
        .read-btn:active {
            transform: scale(0.92);
            background: rgba(255, 255, 255, 0.8);
        }
        .read-btn svg {
            width: 26px;
            height: 26px;
            fill: currentColor;
            pointer-events: none;
        }

        /* محتوى السياسة */
        .policy-content {
            position: relative;
            z-index: 1;
            margin: 8px 0 16px;
            line-height: 1.8;
            font-size: clamp(0.9rem, 2.2vw, 1rem);
            max-height: 65vh;
            overflow-y: auto;
            padding-left: 4px;
            padding-right: 4px;
            /* تحسين التمرير للأندرويد */
            -webkit-overflow-scrolling: touch;
            scroll-behavior: smooth;
            color: #0f172a;
        }
        .policy-content::-webkit-scrollbar {
            width: 4px;
        }
        .policy-content::-webkit-scrollbar-track {
            background: transparent;
        }
        .policy-content::-webkit-scrollbar-thumb {
            background: rgba(0, 0, 0, 0.15);
            border-radius: 10px;
        }

        .policy-content h1,
        .policy-content h6,
        .policy-content h3 {
            color: #0f172a;
            margin: 0.6em 0 0.3em;
            font-weight: 600;
        }
        .policy-content h1 {
            font-size: clamp(1.3rem, 4vw, 1.6rem);
        }
        .policy-content h6 {
            font-size: clamp(0.85rem, 2vw, 1rem);
            font-weight: 400;
            line-height: 1.8;
            color: #1e293b;
        }
        .policy-content h3 {
            font-size: clamp(0.95rem, 2.2vw, 1.1rem);
            opacity: 0.75;
        }
        .policy-content p {
            margin: 0.4em 0;
        }

        /* زر البريد الإلكتروني – مناسب للأندرويد */
        .footer-actions {
            display: flex;
            justify-content: center;
            margin-top: 8px;
            position: relative;
            z-index: 1;
        }

        .email-btn {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            background: rgba(255, 255, 255, 0.5);
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
            border: 1px solid rgba(255, 255, 255, 0.8);
            padding: 14px 24px;
            border-radius: 60px;
            color: #0f172a;
            font-size: clamp(0.9rem, 2.2vw, 1.05rem);
            font-weight: 500;
            text-decoration: none;
            transition: 0.2s ease;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.06);
            letter-spacing: 0.2px;
            text-align: center;
            touch-action: manipulation;
            user-select: none;
            -webkit-user-select: none;
            width: 100%;
            justify-content: center;
            max-width: 400px;
        }
        .email-btn:active {
            transform: scale(0.97);
            background: rgba(255, 255, 255, 0.85);
        }
        .email-btn svg {
            width: 22px;
            height: 22px;
            fill: currentColor;
            opacity: 0.7;
            flex-shrink: 0;
        }
        .email-btn span {
            direction: ltr;
            unicode-bidi: embed;
            font-weight: 400;
        }

        /* تحسين للشاشات الصغيرة جداً */
        @media (max-width: 480px) {
            body {
                padding: 10px;
            }
            .glass-card {
                padding: 20px 16px 18px;
                border-radius: 28px;
            }
            .profile-avatar {
                width: 56px;
                height: 56px;
                max-width: 56px;
            }
            .read-btn {
                width: 42px;
                height: 42px;
            }
            .read-btn svg {
                width: 22px;
                height: 22px;
            }
            .email-btn {
                padding: 12px 18px;
                font-size: 0.85rem;
                gap: 8px;
            }
            .policy-content {
                max-height: 60vh;
                font-size: 0.85rem;
            }
        }

        @media (max-width: 380px) {
            .profile-section {
                gap: 10px;
            }
            .header-text h1 {
                font-size: 1.1rem;
            }
            .read-btn {
                width: 38px;
                height: 38px;
            }
        }
    </style>
</head>
<body>
    <div class="glass-card">

        <!-- الملف الشخصي -->
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

        <!-- محتوى السياسة – النص الأصلي بدون تغيير -->
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

        <!-- زر البريد الإلكتروني – النص الجديد -->
        <div class="footer-actions">
            <a href="mailto:contactchatbot1@gmail.com" class="email-btn">
                <svg viewBox="0 0 24 24"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg>
                <span>للتواصل مع المطور اضغط لتواصل عبر بريد الكتروني</span>
            </a>
        </div>

    </div>

    <script>
        (function() {
            const readBtn = document.getElementById('readAloudBtn');
            const policyDiv = document.getElementById('policyText');
            let isReading = false;
            let utterance = null;

            // التحقق من دعم Speech Synthesis
            const supportsSpeech = 'speechSynthesis' in window;

            function getPolicyText() {
                return policyDiv.innerText;
            }

            function speakText() {
                if (!supportsSpeech) {
                    // تنبيه للمستخدم في حال عدم الدعم
                    alert('متصفحك لا يدعم خاصية قراءة النص صوتياً.');
                    return;
                }

                // إذا كان يقرأ حالياً، إيقاف
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

                utterance.onerror = function(event) {
                    // في حالة خطأ (مثل عدم وجود أصوات)
                    isReading = false;
                    readBtn.innerHTML = `<svg viewBox="0 0 24 24"><path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/></svg>`;
                    // تجاهل الخطأ إذا كان بسبب الإلغاء
                    if (event.error !== 'canceled') {
                        console.warn('Speech error:', event.error);
                    }
                };

                window.speechSynthesis.speak(utterance);
            }

            // إضافة حدث النقر مع منع الازدواجية
            readBtn.addEventListener('click', speakText);
            // دعم اللمس للأندرويد (نفس الحدث)
            readBtn.addEventListener('touchstart', function(e) {
                // منع التكرار عند اللمس
                e.preventDefault();
                speakText();
            }, { passive: false });

            // تحسين: إلغاء القراءة عند مغادرة الصفحة
            window.addEventListener('beforeunload', function() {
                if (isReading) {
                    window.speechSynthesis.cancel();
                }
            });

        })();
    </script>
</body>
</html>
