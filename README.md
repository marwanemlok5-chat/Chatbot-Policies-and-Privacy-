<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes" />
    <title>سياسة الخصوصية - شات بوت</title>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700&display=swap" rel="stylesheet" />
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

        .avatar-wrapper {
            position: relative;
            width: 90px;
            height: 90px;
            flex-shrink: 0;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .star-ring {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 2;
        }
        .star-ring .star {
            position: absolute;
            font-size: 1.5rem;
            color: #2563eb;
            text-shadow: 0 0 12px rgba(37, 99, 235, 0.6);
            animation: twinkle 2.5s infinite alternate ease-in-out;
            transform-origin: center;
            line-height: 1;
        }
        .star-ring .star:nth-child(1) { top: -8px; left: 50%; transform: translateX(-50%); }
        .star-ring .star:nth-child(2) { top: 18%; right: -8px; transform: translateY(-50%); }
        .star-ring .star:nth-child(3) { bottom: -8px; left: 50%; transform: translateX(-50%); }
        .star-ring .star:nth-child(4) { bottom: 18%; left: -8px; transform: translateY(50%); }
        .star-ring .star:nth-child(5) { top: 50%; left: 50%; transform: translate(-50%, -50%) scale(1.3); opacity: 0.3; }

        @keyframes twinkle {
            0% { opacity: 0.6; transform: scale(0.9); }
            100% { opacity: 1; transform: scale(1.2); }
        }

        .avatar-wrapper canvas {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 130px;
            height: 130px;
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
            display: block;
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
            color: #0f172a;
            margin: 0;
            line-height: 1.2;
        }

        .header-text .sub-date {
            font-size: clamp(0.75rem, 2vw, 0.95rem);
            opacity: 0.6;
            margin-top: 2px;
            color: #334155;
        }

        .ai-badge {
            display: flex;
            align-items: center;
            gap: 6px;
            background: rgba(255, 255, 255, 0.35);
            backdrop-filter: blur(8px);
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
        }

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
            border: 1px solid rgba(255, 255, 255, 0.7);
            color: #1e293b;
            width: 48px;
            height: 48px;
            border-radius: 50%;
            cursor: pointer;
            transition: 0.2s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.04);
            touch-action: manipulation;
            user-select: none;
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

        .policy-content {
            position: relative;
            z-index: 1;
            margin: 12px 0 16px;
            line-height: 1.9;
            font-size: clamp(0.95rem, 2.2vw, 1.05rem);
            max-height: 65vh;
            overflow-y: auto;
            padding: 0 4px;
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

        /* تنسيق النص المنظم باستخدام فقرات وقوائم */
        .policy-content p {
            margin: 0.6em 0;
            line-height: 1.9;
        }
        .policy-content .section-title {
            display: block;
            font-weight: 700;
            color: #0f172a;
            font-size: 1.1em;
            margin-top: 1.2em;
            margin-bottom: 0.3em;
        }
        .policy-content ul {
            padding-right: 1.8em;
            margin: 0.3em 0;
            list-style: none;
        }
        .policy-content ul li {
            position: relative;
            padding-right: 1.2em;
            margin: 0.2em 0;
        }
        .policy-content ul li::before {
            content: "•";
            position: absolute;
            right: 0;
            color: #2563eb;
            font-weight: bold;
        }
        .policy-content h3 {
            font-size: clamp(0.95rem, 2.2vw, 1.1rem);
            opacity: 0.8;
            margin: 0.8em 0 0.2em;
            font-weight: 500;
        }
        .policy-content strong {
            font-weight: 700;
            color: #0f172a;
        }

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
            border: 1px solid rgba(255, 255, 255, 0.7);
            padding: 14px 24px;
            border-radius: 60px;
            color: #0f172a;
            font-size: clamp(0.9rem, 2.2vw, 1.05rem);
            font-weight: 500;
            text-decoration: none;
            transition: 0.2s ease;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.04);
            text-align: center;
            touch-action: manipulation;
            user-select: none;
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

        @media (max-width: 480px) {
            body { padding: 10px; }
            .glass-card { padding: 20px 16px 18px; border-radius: 28px; }
            .avatar-wrapper { width: 76px; height: 76px; }
            .avatar-wrapper canvas { width: 110px; height: 110px; }
            .profile-avatar { width: 56px; height: 56px; }
            .star-ring .star { font-size: 1.2rem; }
            .read-btn, .translate-btn { width: 42px; height: 42px; }
            .read-btn svg { width: 22px; height: 22px; }
            .ai-badge { font-size: 0.7rem; padding: 2px 10px 2px 8px; }
            .email-btn { padding: 12px 18px; font-size: 0.85rem; gap: 8px; }
            .policy-content { max-height: 60vh; font-size: 0.9rem; }
        }

        @media (max-width: 380px) {
            .profile-section { gap: 10px; }
            .header-text h1 { font-size: 1.1rem; }
            .read-btn, .translate-btn { width: 38px; height: 38px; }
            .star-ring .star { font-size: 1rem; }
        }
    </style>
</head>
<body>
    <div class="glass-card">

        <!-- الملف الشخصي مع شارة ✦ AI ونجوم -->
        <div class="profile-section">
            <div class="avatar-wrapper" id="avatarWrapper">
                <div class="star-ring">
                    <span class="star">✦</span>
                    <span class="star">✦</span>
                    <span class="star">✦</span>
                    <span class="star">✦</span>
                    <span class="star">✦</span>
                </div>
                <img class="profile-avatar" src="bfd8c880-8807-11f1-8108-b3a8e4e1fe89.png" alt="شعار البوت" loading="lazy" onerror="this.style.display='none'" />
            </div>

            <div class="header-text">
                <h1>سياسات والخصوصية شات بوت</h1>
                <div class="sub-date">الإثنين 10 اغسطس 2026</div>
            </div>

            <div class="ai-badge">
                <i class="fas fa-star"></i> ✦ AI
            </div>

            <div class="action-buttons">
                <button class="read-btn" id="readAloudBtn" type="button" aria-label="قراءة النص بصوت">
                    <svg viewBox="0 0 24 24" width="26" height="26"><path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/></svg>
                </button>
                <button class="translate-btn" id="translateBtn" type="button" aria-label="ترجمة إلى الإنجليزية مع القراءة الصوتية">
                    <i class="fas fa-language"></i>
                </button>
            </div>
        </div>

        <!-- محتوى السياسة – منظم باستخدام فقرات وقوائم مع الحفاظ الكامل على النص -->
        <div class="policy-content" id="policyText">
            <div class="lang-arabic">
                <p><strong>سياسة الخصوصية لبوت [Chatbot]</strong></p>
                <p><span class="section-title">آخر تحديث: [الثلاثاء 28 يوليوز 2026]</span></p>
                <p>مرحباً بك في بوت [Chatbot]. نحن نلتزم بحماية خصوصيتك وشفافية التعامل مع بياناتك. توضح هذه السياسة كيفية جمع معلوماتك واستخدامها وحمايتها عند تفاعلك مع بوتنا عبر فيسبوك ماسنجر.</p>

                <span class="section-title">1. المعلومات التي نجمعها</span>
                <p>عند استخدامك للبوت، قد نقوم بجمع:</p>
                <ul>
                    <li>المعلومات الأساسية: معرف المستخدم الخاص بالصفحة (PSID)، والاسم العام لملفك الشخصي على فيسبوك.</li>
                    <li>محتويات المحادثة: الرسائل التي ترسلها للبوت، والأسئلة التي تطرحها، والتعليمات التي تقدمها.</li>
                    <li>بيانات التفاعل: سجل نقاطك، وتاريخ ووقت المحادثات، وعدد المرات التي تستخدم فيها البوت.</li>
                </ul>

                <span class="section-title">2. كيف نستخدم معلوماتك</span>
                <p>نستخدم البيانات التي نجمعها للأغراض التالية:</p>
                <ul>
                    <li>تشغيل البوت وتحسينه: لتقديم ردود دقيقة، وتحليل أنماط المحادثة لتطوير أداء البوت.</li>
                    <li>تخصيص التجربة: لتذكر تفضيلاتك وسجل محادثاتك السابقة، وجعل التفاعل أكثر سلاسة.</li>
                    <li>إدارة نظام النقاط: لتتبع نقاطك وتحديث رصيدك، ومنحك المكافآت التي تزيد من فرصك في التحدث.</li>
                    <li>مراقبة الجودة والامتثال: لضمان الالتزام بسياسة الاستخدام، واكتشاف أي إساءة أو انتهاك للقوانين.</li>
                </ul>

                <span class="section-title">3. محاكاة السلوك البشري</span>
                <p>يعمل بوت [Chatbot] بتقنيات الذكاء الاصطناعي المصممة لمحاكاة المحادثة البشرية. هذا يعني:</p>
                <ul>
                    <li>البوت ليس إنساناً، بل برنامج يهدف لجعل تفاعلك طبيعياً وسلساً.</li>
                    <li>يتم تحليل مدخلاتك لتوليد ردود تشبه ردود البشر، لكن جميع الردود يتم إنشاؤها آلياً.</li>
                    <li>رغم محاولتنا تقديم تجربة شبيهة بالبشر، لا يمكن اعتبار البوت بديلاً عن الاستشارات البشرية في الأمور الحساسة (كالصحية أو القانونية).</li>
                </ul>

                <span class="section-title">4. نظام النقاط وزيادة فرص التحدث</span>
                <p>لبوتنا نظام نقاط يحفز التفاعل:</p>
                <ul>
                    <li>كسب النقاط: يمكنك ربح نقاط عبر التفاعل مع البوت، أو إنجاز مهام محددة، أو المشاركة في أنشطة يعلن عنها البوت.</li>
                    <li>استخدام النقاط: تمنحك النقاط مزايا إضافية، مثل زيادة أولوية الردود، أو الحصول على محتوى حصري، أو فترات محادثة أطول.</li>
                    <li>ملاحظة: النقاط ليس لها قيمة نقدية، ولا يمكن استبدالها بأموال حقيقية، وهي خاصة بحسابك ولا تُنقل للآخرين.</li>
                </ul>

                <span class="section-title">5. الحظر (الBan) وإنهاء الخدمة</span>
                <p>لضمان بيئة آمنة ومحترمة، نحتفظ بالحق في حظر أي مستخدم بشكل مؤقت أو دائم في الحالات التالية:</p>
                <ul>
                    <li>إساءة الاستخدام: استخدام ألفاظ بذيئة، أو مضايقة، أو محاولة اختراق البوت.</li>
                    <li>انتهاك الشروط: محاولة التلاعب بنظام النقاط، أو استخدام البوت لأغراض غير قانونية.</li>
                    <li>الطلبات المتكررة: إرسال كم هائل من الرسائل بهدف تعطيل الخدمة (ما يعرف بهجمات الإغراق).</li>
                </ul>
                <p>في حال حظر حسابك، قد تفقد نقاطك وإمكانية الوصول للبوت. يمكنك التواصل معنا للاعتراض على قرار الحظر.</p>

                <span class="section-title">6. مشاركة البيانات مع أطراف ثالثة</span>
                <ul>
                    <li>لا نبيع معلوماتك الشخصية أو محادثاتك لأي طرف ثالث.</li>
                    <li>قد نشارك بيانات مجمعة وغير قابلة للتعريف (مثل إحصاءات الاستخدام) مع شركاء تقنيين لتحسين البوت.</li>
                    <li>نظراً لأن البوت يعمل على منصة فيسبوك ماسنجر، فإن سياسة خصوصية ميتا تنطبق أيضاً على تفاعلك، وقد تستخدم ميتا بيانات التفاعل لأغراضها (كتحسين الإعلانات) وفقاً لسياساتها.</li>
                </ul>

                <span class="section-title">7. حماية بياناتك وتخزينها</span>
                <ul>
                    <li>نتخذ إجراءات أمنية معقولة لحماية بياناتك من الوصول غير المصرح به.</li>
                    <li>قد نحتفظ بسجل المحادثات لفترة محدودة لتحسين البوت، ثم نقوم بحذفها أو إخفاء هويتها بشكل دائم.</li>
                    <li>رغم جهودنا، لا يمكن ضمان أمن البيانات بنسبة 100% عند نقلها عبر الإنترنت.</li>
                </ul>

                <span class="section-title">8. حقوقك</span>
                <p>لديك الحق في:</p>
                <ul>
                    <li>طلب حذف بياناتك: يمكنك التواصل معنا لطلب حذف معلوماتك المخزنة.</li>
                    <li>الانسحاب من نظام النقاط: يمكنك إلغاء المشاركة في نظام النقاط في أي وقت.</li>
                    <li>الوصول إلى بياناتك: يمكنك طلب نسخة من البيانات التي لدينا عنك.</li>
                </ul>

                <span class="section-title">9. التواصل معنا</span>
                <p>للاستفسارات حول هذه السياسة، أو لحذف بياناتك، أو للاعتراض على قرار حظر، يرجى التواصل معنا.</p>

                <span class="section-title">10. التعديل على السياسة</span>
                <p>قد نقوم بتحديث هذه السياسة من وقت لآخر. سنخطرك بأي تغييرات جوهرية عبر البوت أو صفحتنا على فيسبوك. استمرارك باستخدام البوت بعد التعديل يعني موافقتك على السياسة المحدثة.</p>

                <span class="section-title">إشعار حقوق الملكية</span>
                <p>جميع المحتويات المنشورة على صفحة Chatbot من صور، فيديوهات، نصوص، وتصاميم مولدة بواسطة أدوات الذكاء الاصطناعي المملوكة للصفحة هي ملك فكري حصري لصفحة Chatbot.</p>
                <p>يُحظر إعادة نشرها أو استخدامها تجارياً بدون إذن خطي مسبق من إدارة الصفحة. © 2026</p>

                <h3>الإثنين 10 اغسطس 2026</h3>
                <h3>جميع الحقوق محفوظه لهذا البوت</h3>
            </div>

            <div class="lang-english">
                <p><strong>Privacy Policy for [Chatbot] Bot</strong></p>
                <p><span class="section-title">Last updated: [Tuesday, July 28, 2026]</span></p>
                <p>Welcome to [Chatbot] Bot. We are committed to protecting your privacy and ensuring transparency in handling your data. This policy explains how we collect, use, and protect your information when you interact with our bot via Facebook Messenger.</p>

                <span class="section-title">1. Information We Collect</span>
                <p>When using the bot, we may collect:</p>
                <ul>
                    <li>Basic information: Page-scoped user ID (PSID), and your public Facebook profile name.</li>
                    <li>Conversation content: Messages you send to the bot, questions you ask, and instructions you provide.</li>
                    <li>Interaction data: Your points history, conversation timestamps, and usage frequency.</li>
                </ul>

                <span class="section-title">2. How We Use Your Information</span>
                <p>We use the data we collect for the following purposes:</p>
                <ul>
                    <li>Operating and improving the bot: To provide accurate responses and analyze conversation patterns to enhance performance.</li>
                    <li>Personalizing experience: To remember your preferences and past conversations for smoother interaction.</li>
                    <li>Managing the points system: To track your points, update your balance, and grant rewards that increase your speaking opportunities.</li>
                    <li>Quality monitoring and compliance: To ensure adherence to our usage policy and detect any misuse or violations.</li>
                </ul>

                <span class="section-title">3. Human-like Behavior Simulation</span>
                <p>[Chatbot] Bot uses AI technologies designed to simulate human conversation. This means:</p>
                <ul>
                    <li>The bot is not human; it is a program aimed at making your interaction natural and smooth.</li>
                    <li>Your inputs are analyzed to generate human-like replies, but all responses are generated automatically.</li>
                    <li>Although we strive to provide a human-like experience, the bot should not be considered a substitute for professional advice in sensitive matters (e.g., health or legal).</li>
                </ul>

                <span class="section-title">4. Points System and Increased Speaking Chances</span>
                <p>Our bot has a points system to encourage interaction:</p>
                <ul>
                    <li>Earning points: You can earn points by interacting with the bot, completing specific tasks, or participating in activities announced by the bot.</li>
                    <li>Using points: Points give you additional benefits, such as higher reply priority, exclusive content, or longer conversation sessions.</li>
                    <li>Note: Points have no monetary value and cannot be exchanged for real money. They are tied to your account and are non-transferable.</li>
                </ul>

                <span class="section-title">5. Ban and Service Termination</span>
                <p>To ensure a safe and respectful environment, we reserve the right to temporarily or permanently ban any user in the following cases:</p>
                <ul>
                    <li>Misuse: Using offensive language, harassment, or attempting to hack the bot.</li>
                    <li>Violation of terms: Attempting to manipulate the points system or using the bot for illegal purposes.</li>
                    <li>Excessive requests: Sending a large volume of messages to disrupt the service (known as flooding attacks).</li>
                </ul>
                <p>If your account is banned, you may lose your points and access to the bot. You may contact us to appeal the ban decision.</p>

                <span class="section-title">6. Data Sharing with Third Parties</span>
                <ul>
                    <li>We do not sell your personal information or conversations to any third party.</li>
                    <li>We may share aggregated and non-identifiable data (e.g., usage statistics) with technical partners to improve the bot.</li>
                    <li>Since the bot operates on Facebook Messenger, Meta's privacy policy also applies to your interaction, and Meta may use interaction data for its purposes (e.g., improving ads) in accordance with its policies.</li>
                </ul>

                <span class="section-title">7. Data Protection and Storage</span>
                <ul>
                    <li>We implement reasonable security measures to protect your data from unauthorized access.</li>
                    <li>We may retain conversation logs for a limited period to improve the bot, then delete or permanently anonymize them.</li>
                    <li>Despite our efforts, we cannot guarantee 100% data security during transmission over the internet.</li>
                </ul>

                <span class="section-title">8. Your Rights</span>
                <p>You have the right to:</p>
                <ul>
                    <li>Request deletion of your data: Contact us to request deletion of your stored information.</li>
                    <li>Opt out of the points system: You can withdraw from the points system at any time.</li>
                    <li>Access your data: Request a copy of the data we hold about you.</li>
                </ul>

                <span class="section-title">9. Contact Us</span>
                <p>For inquiries about this policy, to delete your data, or to appeal a ban, please contact us.</p>

                <span class="section-title">10. Policy Amendments</span>
                <p>We may update this policy from time to time. We will notify you of any material changes via the bot or our Facebook page. Continued use of the bot after the amendment constitutes your acceptance of the updated policy.</p>

                <span class="section-title">Copyright Notice</span>
                <p>All content published on the Chatbot page – including images, videos, texts, and designs generated by AI tools owned by the page – is the exclusive intellectual property of the Chatbot page.</p>
                <p>Commercial republication or use without prior written permission from the page administration is prohibited. © 2026</p>

                <h3>Monday, August 10, 2026</h3>
                <h3>All rights reserved for this bot</h3>
            </div>
        </div>

        <!-- زر البريد الإلكتروني -->
        <div class="footer-actions">
            <a href="mailto:contactchatbot1@gmail.com" class="email-btn">
                <i class="fas fa-envelope"></i>
                <span>للتواصل مع المطور اضغط لتواصل عبر بريد الكتروني</span>
            </a>
        </div>

    </div>

    <!-- Three.js للشبكة العصبية -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js">
    </script>
    <script>
        (function() {
            try {
                const wrapper = document.getElementById('avatarWrapper');
                if (!wrapper) return;

                const canvas = document.createElement('canvas');
                canvas.width = 160;
                canvas.height = 160;
                canvas.style.width = '130px';
                canvas.style.height = '130px';
                canvas.style.position = 'absolute';
                canvas.style.top = '50%';
                canvas.style.left = '50%';
                canvas.style.transform = 'translate(-50%, -50%)';
                canvas.style.borderRadius = '50%';
                canvas.style.pointerEvents = 'none';
                canvas.style.zIndex = '0';
                canvas.style.opacity = '0.85';
                wrapper.appendChild(canvas);

                const scene = new THREE.Scene();
                const camera = new THREE.PerspectiveCamera(45, 1, 0.1, 1000);
                camera.position.z = 4;

                const renderer = new THREE.WebGLRenderer({ canvas, alpha: true, antialias: true });
                renderer.setSize(160, 160);
                renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

                const pointsCount = 80;
                const radius = 1.6;
                const positions = [];
                const colors = [];

                for (let i = 0; i < pointsCount; i++) {
                    const theta = Math.random() * Math.PI * 2;
                    const phi = Math.acos(2 * Math.random() - 1);
                    const r = radius * (0.6 + Math.random() * 0.4);
                    positions.push(r * Math.sin(phi) * Math.cos(theta),
                        r * Math.sin(phi) * Math.sin(theta),
                        r * Math.cos(phi));
                    colors.push(0.2 + Math.random() * 0.3, 0.4 + Math.random() * 0.4, 0.8 + Math.random() * 0.2);
                }

                const geometry = new THREE.BufferGeometry();
                geometry.setAttribute('position', new THREE.Float32BufferAttribute(positions, 3));
                geometry.setAttribute('color', new THREE.Float32BufferAttribute(colors, 3));

                const pointsMaterial = new THREE.PointsMaterial({
                    size: 0.12,
                    vertexColors: true,
                    transparent: true,
                    opacity: 0.8,
                    blending: THREE.AdditiveBlending,
                    depthWrite: false
                });
                const points = new THREE.Points(geometry, pointsMaterial);
                scene.add(points);

                const linePositions = [];
                const posArray = positions;
                const threshold = 1.2;
                for (let i = 0; i < pointsCount; i++) {
                    for (let j = i + 1; j < pointsCount; j++) {
                        const dx = posArray[i * 3] - posArray[j * 3];
                        const dy = posArray[i * 3 + 1] - posArray[j * 3 + 1];
                        const dz = posArray[i * 3 + 2] - posArray[j * 3 + 2];
                        const dist = Math.sqrt(dx * dx + dy * dy + dz * dz);
                        if (dist < threshold && Math.random() < 0.15) {
                            linePositions.push(
                                posArray[i * 3], posArray[i * 3 + 1], posArray[i * 3 + 2],
                                posArray[j * 3], posArray[j * 3 + 1], posArray[j * 3 + 2]
                            );
                        }
                    }
                }
                const lineGeo = new THREE.BufferGeometry();
                lineGeo.setAttribute('position', new THREE.Float32BufferAttribute(linePositions, 3));
                const lineMat = new THREE.LineBasicMaterial({
                    color: 0x4f8cf7,
                    transparent: true,
                    opacity: 0.3,
                    blending: THREE.AdditiveBlending
                });
                const lines = new THREE.LineSegments(lineGeo, lineMat);
                scene.add(lines);

                const centerGlow = new THREE.Mesh(
                    new THREE.SphereGeometry(0.25, 16, 16),
                    new THREE.MeshBasicMaterial({ color: 0x4f8cf7, transparent: true, opacity: 0.6 })
                );
                scene.add(centerGlow);

                let time = 0;

                function animate() {
                    requestAnimationFrame(animate);
                    time += 0.005;
                    points.rotation.x = Math.sin(time * 0.3) * 0.2;
                    points.rotation.y += 0.003;
                    points.rotation.z = Math.cos(time * 0.2) * 0.1;
                    lines.rotation.x = points.rotation.x;
                    lines.rotation.y = points.rotation.y;
                    lines.rotation.z = points.rotation.z;
                    centerGlow.rotation.x = points.rotation.x;
                    centerGlow.rotation.y = points.rotation.y;
                    renderer.render(scene, camera);
                }
                animate();
            } catch (e) {
                console.warn('Three.js error (ignored):', e);
            }
        })();
    </script>

    <script>
        (function() {
            'use strict';

            const readBtn = document.getElementById('readAloudBtn');
            const translateBtn = document.getElementById('translateBtn');
            const policyDiv = document.getElementById('policyText');

            if (!readBtn || !translateBtn || !policyDiv) return;

            let isReading = false;
            let utterance = null;
            let isEnglish = false;

            const supportsSpeech = 'speechSynthesis' in window;

            function getCurrentText() {
                const arabic = policyDiv.querySelector('.lang-arabic');
                const english = policyDiv.querySelector('.lang-english');
                if (arabic && english) {
                    return policyDiv.classList.contains('show-english') ? english.innerText : arabic.innerText;
                }
                return policyDiv.innerText;
            }

            function detectLanguage(text) {
                return /[\u0600-\u06FF]/.test(text) ? 'ar-SA' : 'en-US';
            }

            function speakText() {
                if (!supportsSpeech) {
                    alert('متصفحك لا يدعم قراءة النص صوتياً.');
                    return;
                }

                if (isReading) {
                    window.speechSynthesis.cancel();
                    isReading = false;
                    readBtn.innerHTML =
                        `<svg viewBox="0 0 24 24" width="26" height="26"><path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/></svg>`;
                    return;
                }

                const text = getCurrentText().trim();
                if (!text) {
                    alert('لا يوجد نص للقراءة.');
                    return;
                }

                utterance = new SpeechSynthesisUtterance(text);
                const lang = detectLanguage(text);
                utterance.lang = lang;
                utterance.rate = 0.9;
                utterance.pitch = 1;
                utterance.volume = 1;

                const voices = window.speechSynthesis.getVoices();
                const preferred = voices.find(v => v.lang.startsWith(lang.split('-')[0]));
                if (preferred) utterance.voice = preferred;

                utterance.onstart = function() {
                    isReading = true;
                    readBtn.innerHTML =
                        `<svg viewBox="0 0 24 24" width="26" height="26"><path d="M6 19h4V5H6v14zm8-14v14h4V5h-4z"/></svg>`;
                };

                utterance.onend = function() {
                    isReading = false;
                    readBtn.innerHTML =
                        `<svg viewBox="0 0 24 24" width="26" height="26"><path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/></svg>`;
                };

                utterance.onerror = function(event) {
                    isReading = false;
                    readBtn.innerHTML =
                        `<svg viewBox="0 0 24 24" width="26" height="26"><path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/></svg>`;
                    if (event.error !== 'canceled') {
                        console.warn('خطأ في النطق:', event.error);
                    }
                };

                window.speechSynthesis.speak(utterance);
            }

            function toggleTranslationAndSpeak() {
                isEnglish = !isEnglish;
                if (isEnglish) {
                    policyDiv.classList.add('show-english');
                    translateBtn.setAttribute('aria-label', 'عرض النص العربي');
                } else {
                    policyDiv.classList.remove('show-english');
                    translateBtn.setAttribute('aria-label', 'ترجمة إلى الإنجليزية مع القراءة الصوتية');
                }

                if (isReading) {
                    window.speechSynthesis.cancel();
                    isReading = false;
                    readBtn.innerHTML =
                        `<svg viewBox="0 0 24 24" width="26" height="26"><path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/></svg>`;
                }

                setTimeout(function() {
                    speakText();
                }, 100);
            }

            readBtn.addEventListener('click', speakText);
            readBtn.addEventListener('touchstart', function(e) {
                e.preventDefault();
                speakText();
            }, { passive: false });

            translateBtn.addEventListener('click', toggleTranslationAndSpeak);
            translateBtn.addEventListener('touchstart', function(e) {
                e.preventDefault();
                toggleTranslationAndSpeak();
            }, { passive: false });

            if (supportsSpeech) {
                window.speechSynthesis.getVoices();
                window.speechSynthesis.onvoiceschanged = function() {
                    window.speechSynthesis.getVoices();
                };
            }

            window.addEventListener('beforeunload', function() {
                if (isReading) {
                    window.speechSynthesis.cancel();
                }
            });

        })();
    </script>
</body>
</html>
