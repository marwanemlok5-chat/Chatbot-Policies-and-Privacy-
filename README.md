
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
    <!-- Font Awesome 6 -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" />
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
            margin: 0;
        }

        /* البطاقة الزجاجية – خلفية شفافة مع blur */
        .glass-card {
            max-width: 850px;
            width: 100%;
            background: rgba(255, 255, 255, 0.6);
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

        /* حاوية الصورة الرمزية مع شبكة عصبية ثلاثية الأبعاد */
        .avatar-wrapper {
            position: relative;
            width: 80px;
            height: 80px;
            flex-shrink: 0;
            border-radius: 50%;
            overflow: visible;
            /* لإظهار الشبكة خارج الإطار */
        }

        .avatar-wrapper canvas {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 120px;
            height: 120px;
            pointer-events: none;
            z-index: 0;
            border-radius: 50%;
            opacity: 0.85;
        }

        .profile-avatar {
            position: relative;
            z-index: 1;
            width: 70px;
            height: 70px;
            border-radius: 50%;
            border: 2px solid rgba(255, 255, 255, 0.7);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.12), 0 0 0 1px rgba(255, 255, 255, 0.3) inset;
            object-fit: cover;
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(4px);
            -webkit-backdrop-filter: blur(4px);
            display: block;
            margin: 5px;
        }

        .profile-section {
            display: flex;
            align-items: center;
            gap: 14px;
            margin-bottom: 8px;
            position: relative;
            z-index: 1;
            flex-wrap: wrap;
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

        /* شارة ✦ AI بالزجاج */
        .ai-badge {
            display: flex;
            align-items: center;
            gap: 6px;
            background: rgba(255, 255, 255, 0.35);
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
            border: 1px solid rgba(255, 255, 255, 0.6);
            border-radius: 40px;
            padding: 4px 14px 4px 10px;
            font-size: 0.85rem;
            font-weight: 600;
            color: #1e40af;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.04);
            white-space: nowrap;
            margin-right: auto;
            margin-left: 8px;
        }
        .ai-badge i {
            font-size: 0.8rem;
            color: #2563eb;
            filter: drop-shadow(0 0 4px rgba(37, 99, 235, 0.2));
        }

        /* أزرار الصوت والترجمة */
        .action-buttons {
            display: flex;
            gap: 8px;
            align-items: center;
            flex-shrink: 0;
        }

        .read-btn,
        .translate-btn {
            background: rgba(255, 255, 255, 0.45);
            backdrop-filter: blur(4px);
            -webkit-backdrop-filter: blur(4px);
            border: 1px solid rgba(255, 255, 255, 0.7);
            color: #1e293b;
            width: 48px;
            height: 48px;
            border-radius: 50%;
            font-size: 1.2rem;
            cursor: pointer;
            transition: 0.2s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.04);
            touch-action: manipulation;
            user-select: none;
            -webkit-user-select: none;
        }
        .read-btn:active,
        .translate-btn:active {
            transform: scale(0.92);
            background: rgba(255, 255, 255, 0.8);
        }
        .read-btn svg,
        .translate-btn i {
            pointer-events: none;
            font-size: 1.4rem;
        }
        .translate-btn i {
            color: #2563eb;
        }

        /* محتوى السياسة */
        .policy-content {
            position: relative;
            z-index: 1;
            margin: 12px 0 16px;
            line-height: 1.8;
            font-size: clamp(0.9rem, 2.2vw, 1rem);
            max-height: 65vh;
            overflow-y: auto;
            padding-left: 4px;
            padding-right: 4px;
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

        .policy-content .lang-arabic,
        .policy-content .lang-english {
            transition: opacity 0.3s ease;
        }
        .policy-content .lang-english {
            display: none;
        }
        .policy-content.show-english .lang-arabic {
            display: none;
        }
        .policy-content.show-english .lang-english {
            display: block;
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

        /* زر البريد الإلكتروني */
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
            background: rgba(255, 255, 255, 0.45);
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
            border: 1px solid rgba(255, 255, 255, 0.7);
            padding: 14px 24px;
            border-radius: 60px;
            color: #0f172a;
            font-size: clamp(0.9rem, 2.2vw, 1.05rem);
            font-weight: 500;
            text-decoration: none;
            transition: 0.2s ease;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.04);
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
            background: rgba(255, 255, 255, 0.8);
        }
        .email-btn i {
            font-size: 1.2rem;
            opacity: 0.7;
        }
        .email-btn span {
            direction: ltr;
            unicode-bidi: embed;
            font-weight: 400;
        }

        /* responsive */
        @media (max-width: 480px) {
            body {
                padding: 10px;
            }
            .glass-card {
                padding: 20px 16px 18px;
                border-radius: 28px;
            }
            .avatar-wrapper {
                width: 64px;
                height: 64px;
            }
            .avatar-wrapper canvas {
                width: 100px;
                height: 100px;
            }
            .profile-avatar {
                width: 56px;
                height: 56px;
            }
            .read-btn,
            .translate-btn {
                width: 42px;
                height: 42px;
            }
            .read-btn svg {
                width: 22px;
                height: 22px;
            }
            .ai-badge {
                font-size: 0.7rem;
                padding: 2px 10px 2px 8px;
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
            .read-btn,
            .translate-btn {
                width: 38px;
                height: 38px;
            }
        }
    </style>
</head>
<body>
    <div class="glass-card">

        <!-- الملف الشخصي مع شارة ✦ AI وزر الترجمة -->
        <div class="profile-section">
            <!-- حاوية الصورة الرمزية مع شبكة عصبية -->
            <div class="avatar-wrapper" id="avatarWrapper">
                <img class="profile-avatar" src="bfd8c880-8807-11f1-8108-b3a8e4e1fe89.png" alt="شعار البوت" loading="lazy" onerror="this.style.display='none'" />
            </div>

            <div class="header-text">
                <h1>سياسات والخصوصية شات بوت</h1>
                <div class="sub-date">الإثنين 10 اغسطس 2026</div>
            </div>

            <!-- شارة ✦ AI بالزجاج -->
            <div class="ai-badge">
                <i class="fas fa-star"></i> ✦ AI
            </div>

            <!-- أزرار الصوت والترجمة -->
            <div class="action-buttons">
                <button class="read-btn" id="readAloudBtn" type="button" aria-label="قراءة النص بصوت">
                    <svg viewBox="0 0 24 24" width="26" height="26"><path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/></svg>
                </button>
                <button class="translate-btn" id="translateBtn" type="button" aria-label="ترجمة إلى الإنجليزية">
                    <i class="fas fa-language"></i>
                </button>
            </div>
        </div>

        <!-- محتوى السياسة (عربي + إنجليزي) -->
        <div class="policy-content" id="policyText">
            <div class="lang-arabic">
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

            <div class="lang-english">
                <h6>Privacy Policy for [Chatbot] Bot

Last updated: [Tuesday, July 28, 2026]

Welcome to [Chatbot] Bot. We are committed to protecting your privacy and ensuring transparency in handling your data. This policy explains how we collect, use, and protect your information when you interact with our bot via Facebook Messenger.

1. Information We Collect

When using the bot, we may collect:

· Basic information: Page-scoped user ID (PSID), and your public Facebook profile name.
· Conversation content: Messages you send to the bot, questions you ask, and instructions you provide.
· Interaction data: Your points history, conversation timestamps, and usage frequency.

2. How We Use Your Information

We use the data we collect for the following purposes:

· Operating and improving the bot: To provide accurate responses and analyze conversation patterns to enhance performance.
· Personalizing experience: To remember your preferences and past conversations for smoother interaction.
· Managing the points system: To track your points, update your balance, and grant rewards that increase your speaking opportunities.
· Quality monitoring and compliance: To ensure adherence to our usage policy and detect any misuse or violations.

3. Human-like Behavior Simulation

[Chatbot] Bot uses AI technologies designed to simulate human conversation. This means:

· The bot is not human; it is a program aimed at making your interaction natural and smooth.
· Your inputs are analyzed to generate human-like replies, but all responses are generated automatically.
· Although we strive to provide a human-like experience, the bot should not be considered a substitute for professional advice in sensitive matters (e.g., health or legal).

4. Points System and Increased Speaking Chances

Our bot has a points system to encourage interaction:

· Earning points: You can earn points by interacting with the bot, completing specific tasks, or participating in activities announced by the bot.
· Using points: Points give you additional benefits, such as higher reply priority, exclusive content, or longer conversation sessions.
· Note: Points have no monetary value and cannot be exchanged for real money. They are tied to your account and are non-transferable.

5. Ban and Service Termination

To ensure a safe and respectful environment, we reserve the right to temporarily or permanently ban any user in the following cases:

· Misuse: Using offensive language, harassment, or attempting to hack the bot.
· Violation of terms: Attempting to manipulate the points system or using the bot for illegal purposes.
· Excessive requests: Sending a large volume of messages to disrupt the service (known as flooding attacks).
If your account is banned, you may lose your points and access to the bot. You may contact us to appeal the ban decision.

6. Data Sharing with Third Parties

· We do not sell your personal information or conversations to any third party.
· We may share aggregated and non-identifiable data (e.g., usage statistics) with technical partners to improve the bot.
· Since the bot operates on Facebook Messenger, Meta's privacy policy also applies to your interaction, and Meta may use interaction data for its purposes (e.g., improving ads) in accordance with its policies.

7. Data Protection and Storage

· We implement reasonable security measures to protect your data from unauthorized access.
· We may retain conversation logs for a limited period to improve the bot, then delete or permanently anonymize them.
· Despite our efforts, we cannot guarantee 100% data security during tr
