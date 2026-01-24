<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0, user-scalable=yes">
<title>أداة إصدار التقارير والشواهد التربوية - الإصدار الآمن</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<style>
@import url('https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;500;600;700;800;900&display=swap');
*{margin:0;padding:0;box-sizing:border-box; -webkit-tap-highlight-color: transparent;}
html,body{font-family:'Cairo',sans-serif;background: linear-gradient(135deg, #f0f9f6 0%, #e8f4f0 50%, #d4ebe2 100%);direction:rtl;overflow-x:hidden;min-height:100vh;-webkit-text-size-adjust:100%; -moz-text-size-adjust:100%; -ms-text-size-adjust:100%; text-size-adjust:100%; touch-action: manipulation;}
.wrapper{max-width:900px;margin:auto;padding:20px;width:100%;}

/* ==================== أنماط الأمان الجديدة ==================== */
.security-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(2, 46, 34, 0.95);
    z-index: 9998;
    display: flex;
    align-items: center;
    justify-content: center;
    backdrop-filter: blur(10px);
}

.security-alert {
    background: linear-gradient(135deg, #ff6b6b 0%, #c92a2a 100%);
    color: white;
    padding: 30px;
    border-radius: 15px;
    text-align: center;
    box-shadow: 0 20px 40px rgba(0,0,0,0.3);
    animation: pulseAlert 2s infinite;
    border: 3px solid #ffd166;
    max-width: 400px;
    width: 90%;
}

@keyframes pulseAlert {
    0%, 100% { transform: scale(1); box-shadow: 0 20px 40px rgba(0,0,0,0.3); }
    50% { transform: scale(1.02); box-shadow: 0 25px 50px rgba(0,0,0,0.4); }
}

.security-countdown {
    font-size: 48px;
    font-weight: 900;
    margin: 20px 0;
    color: #ffd166;
    text-shadow: 0 2px 10px rgba(0,0,0,0.3);
    animation: countdownPulse 1s infinite;
}

@keyframes countdownPulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.7; }
}

.attempt-counter {
    position: fixed;
    top: 10px;
    left: 10px;
    background: rgba(0,0,0,0.9);
    color: white;
    padding: 8px 15px;
    border-radius: 8px;
    font-size: 13px;
    z-index: 9999;
    display: flex;
    align-items: center;
    gap: 8px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.2);
    border: 1px solid rgba(255,255,255,0.1);
}

.attempt-counter.warning {
    background: linear-gradient(135deg, #ffc107 0%, #e0a800 100%);
}

.attempt-counter.danger {
    background: linear-gradient(135deg, #dc3545 0%, #c82333 100%);
    animation: dangerPulse 1s infinite;
}

@keyframes dangerPulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.05); }
}

/* ==================== شاشة التفعيل - محسنة بالأمان ==================== */
#activationScreen {
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    background: linear-gradient(135deg, #022e22 0%, #044a35 100%);
    z-index: 9999;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Cairo', sans-serif;
    padding: 20px;
}

#activationScreen .activation-box {
    background: rgba(255, 255, 255, 0.95);
    padding: 40px 30px;
    border-radius: 20px;
    width: 100%;
    max-width: 500px;
    text-align: center;
    box-shadow: 0 20px 50px rgba(0,0,0,0.4);
    border: 3px solid #ffd166;
    backdrop-filter: blur(10px);
}

#activationScreen .app-icon {
    font-size: 60px;
    color: #066d4d;
    margin-bottom: 20px;
    display: flex;
    justify-content: center;
    gap: 15px;
}

#activationScreen .app-icon i {
    background: linear-gradient(135deg, #066d4d, #ffd166, #4d96ff);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: iconFloat 3s ease-in-out infinite;
}

@keyframes iconFloat {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-10px); }
}

#activationScreen h3 {
    color: #044a35; 
    margin-bottom: 15px; 
    font-size: 28px;
    font-weight: 900;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 15px;
}

#activationScreen .app-description {
    color: #555; 
    font-size: 16px; 
    margin-bottom: 25px;
    line-height: 1.6;
    padding: 0 20px;
    background: linear-gradient(135deg, #e8f4f0, #f0f9f6);
    padding: 15px;
    border-radius: 12px;
    border-right: 4px solid #ffd166;
}

.security-status {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 20px;
    padding: 10px 15px;
    background: #f0f9f6;
    border-radius: 10px;
    border: 2px dashed #d4ebe2;
    font-size: 14px;
}

.security-status-item {
    display: flex;
    align-items: center;
    gap: 8px;
}

.security-timer {
    color: #066d4d;
    font-weight: 700;
    direction: ltr;
}

.attempts-left {
    color: #d9534f;
    font-weight: 700;
}

#activationCodeInput {
    width: 100%;
    padding: 18px;
    border: 2px solid #d4ebe2;
    border-radius: 12px;
    font-size: 18px;
    text-align: center;
    margin-bottom: 20px;
    font-family: 'Cairo', sans-serif;
    transition: all 0.3s;
    background: white;
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    letter-spacing: 1px;
    font-weight: 700;
    color: #022e22;
}

#activationCodeInput:focus {
    outline: none;
    border-color: #066d4d;
    box-shadow: 0 0 0 4px rgba(6, 109, 77, 0.15);
    transform: translateY(-3px);
}

.code-length-hint {
    font-size: 12px;
    color: #666;
    margin-bottom: 15px;
    text-align: center;
}

#activationScreen button {
    width: 100%;
    padding: 18px;
    background: linear-gradient(135deg, #066d4d 0%, #05553d 100%);
    color: white;
    border: none;
    border-radius: 12px;
    font-weight: 800;
    cursor: pointer;
    font-size: 18px;
    transition: all 0.3s;
    font-family: 'Cairo', sans-serif;
    box-shadow: 0 6px 20px rgba(6, 109, 77, 0.3);
    position: relative;
    overflow: hidden;
}

#activationScreen button:hover:not(:disabled) {
    background: linear-gradient(135deg, #05553d 0%, #044a35 100%);
    transform: translateY(-5px);
    box-shadow: 0 10px 25px rgba(6, 109, 77, 0.4);
}

#activationScreen button:disabled {
    opacity: 0.6;
    cursor: not-allowed;
}

#activationError {
    color: #d9534f;
    font-size: 14px;
    margin-top: 15px;
    padding: 12px;
    background: linear-gradient(135deg, #fee 0%, #fdd 100%);
    border-radius: 10px;
    border-right: 4px solid #d9534f;
    display: none;
    animation: shake 0.5s ease-in-out;
}

@keyframes shake {
    0%, 100% { transform: translateX(0); }
    10%, 30%, 50%, 70%, 90% { transform: translateX(-5px); }
    20%, 40%, 60%, 80% { transform: translateX(5px); }
}

/* ==================== باقي الأنماط ==================== */

/* شريط الأخبار العلوي */
.top-marquee{
position:fixed;top:0;left:0;right:0;width:100%;background:linear-gradient(135deg, #022e22 0%, #044a35 100%);color:#fff;
padding:10px 5px;font-size:12px;z-index:300;overflow:hidden;height:45px;
white-space:nowrap;border-bottom:3px solid #ffd166;box-shadow:0 4px 12px rgba(2, 46, 34, 0.25);
display:flex;align-items:center;
}
.marquee-inner{
display:inline-block;
padding-left:2%;
animation:newsScroll 30s linear infinite;
color:#e8f4f0;font-weight:500;
}
@keyframes newsScroll{
0%{transform:translateX(-100%);}
100%{transform:translateX(100%);}
}
.top-marquee:hover .marquee-inner{animation-play-state:paused;}

/* شريط التحكم العلوي */
.control-bar{
position:fixed;top:45px;left:0;right:0;width:100%;z-index:250;
background:linear-gradient(135deg, #ffffff 0%, #f5fcf9 100%);
padding:12px 15px;display:flex;justify-content:space-between;align-items:center;
box-shadow:0 4px 15px rgba(4, 74, 53, 0.12);border-bottom:2px solid #d0e6de;
backdrop-filter:blur(5px);
}

/* تحسين تصميم الهيدر */
.header-controls {
display: flex;
align-items: center;
gap: 15px;
flex: 1;
flex-wrap: wrap;
}

/* تاريخ التحويل */
.date-toggle-container {
display: flex;
flex-direction: column;
gap: 4px;
background: linear-gradient(135deg, #e8f4f0 0%, #d4ebe2 100%);
padding: 6px 10px;
border-radius: 10px;
font-size: 12px;
border-right: 4px solid #ffd166;
box-shadow: 0 3px 8px rgba(6, 109, 77, 0.15);
min-width: 220px;
}

.date-display {
font-weight: 700;
color: #044a35;
text-align: center;
font-size: 12px;
margin-bottom: 5px;
}

/* تصميم عنوان التطبيق */
.app-title {
background: linear-gradient(135deg, #e8f4f0 0%, #d4ebe2 100%);
color: #044a35;
padding: 6px 10px;
border-radius: 10px;
font-size: 12px;
font-weight: 800;
border-right: 4px solid #ffd166;
display: flex;
align-items: center;
gap: 8px;
box-shadow: 0 3px 8px rgba(6, 109, 77, 0.15);
flex: 1;
text-align: center;
justify-content: center;
}

/* مجموعة الأزرار */
.btn-group {
    display: flex;
    flex-direction: column;
    gap: 8px;
    width: 100%;
    max-width: 600px;
    margin: 0 auto;
}

.btn-row {
    display: flex;
    justify-content: space-between;
    gap: 8px;
    width: 100%;
}

button.main-btn{
background:linear-gradient(135deg, #066d4d 0%, #05553d 100%);color:#fff;border:none;
padding:12px 10px;font-size:13px;border-radius:12px;cursor:pointer;
transition:all 0.3s ease;font-weight:700;position:relative;overflow:hidden;
box-shadow:0 4px 10px rgba(6, 109, 77, 0.25);display:flex;flex-direction:column;align-items:center;justify-content:center;
border:1px solid rgba(255,255,255,0.1);flex:1;
min-height: 65px;
}
button.main-btn:hover{
background:linear-gradient(135deg, #05553d 0%, #044a35 100%);transform:translateY(-3px);
box-shadow:0 6px 15px rgba(6, 109, 77, 0.35);
}

/* ==================== تحسينات للهواتف ==================== */
@media (max-width: 768px) {
.security-alert {
    padding: 20px;
    margin: 20px;
}

.security-countdown {
    font-size: 36px;
}

.attempt-counter {
    top: 5px;
    left: 5px;
    font-size: 11px;
    padding: 5px 10px;
}

#activationScreen .app-icon {
    font-size: 40px;
}

#activationScreen h3 {
    font-size: 22px;
}

#activationScreen .app-description {
    font-size: 14px;
}

.control-bar {
    top: 45px;
    padding: 8px;
    flex-direction: column;
    gap: 10px;
    height: auto;
    min-height: 120px;
}

.header-controls {
    width: 100%;
    flex-direction: column;
    gap: 10px;
}

.date-toggle-container {
    width: 100%;
    max-width: 100%;
}

.app-title {
    width: 100%;
    max-width: 100%;
    font-size: 11px;
}

.btn-group {
    width: 100%;
    max-width: 100%;
}

.btn-row button.main-btn {
    min-height: 55px;
    padding: 8px 6px;
}
}

/* ==================== قسم PDF ==================== */
#report-content{
  width:100%;
  max-width:210mm;
  margin:4mm auto 0 auto;
  padding:0 6mm;
  box-sizing:border-box;
  display:none;
  font-family:'Cairo',sans-serif;
  background:#fff;
}

.header{
  background:var(--main);
  height:150px;
  border-radius:8px;
  color:#fff;
  display:flex;
  align-items:center;
  justify-content:center;
  position:relative;
  margin-bottom:8px;
}
.header img{width:140px;}
.header-school-title{
  position:absolute;
  right:12px;
  top:20px;
  font-size:14px;
  font-weight:800;
}
.header-school{
  position:absolute;
  right:12px;
  top:45px;
  font-size:18px;
  font-weight:900;
}
.header-education{
  position:absolute;
  left:50%;
  bottom:18px;
  transform:translateX(-50%);
  font-size:16px;
  font-weight:800;
  text-align:center;
  width:100%;
}
.header-date{
  position:absolute;
  left:12px;
  top:10px;
  font-size:12px;
  text-align:right;
}

/* باقي أنماط PDF تبقى كما هي */
</style>
</head>

<body>

<!-- عداد المحاولات -->
<div class="attempt-counter" id="attemptCounter">
    <i class="fas fa-shield-alt"></i>
    <span>المحاولات: <span id="attemptCount">0</span>/3</span>
</div>

<!-- طبقة الأمان -->
<div class="security-overlay" id="securityOverlay" style="display: none;">
    <div class="security-alert">
        <i class="fas fa-ban" style="font-size: 50px; margin-bottom: 20px;"></i>
        <h3 style="margin-bottom: 15px;">⚠️ تم اكتشاف محاولات غير مصرح بها!</h3>
        <p style="margin-bottom: 20px; font-size: 14px;">النظام مغلق مؤقتاً لأسباب أمنية</p>
        <div class="security-countdown" id="lockdownTimer">60</div>
        <p style="margin-top: 20px; font-size: 12px; opacity: 0.8;">
            سيتم إعادة تحميل الصفحة تلقائياً بعد انتهاء العد التنازلي
        </p>
    </div>
</div>

<!-- شاشة التفعيل -->
<div id="activationScreen">
    <div class="activation-box">
        <div class="app-icon">
            <i class="fas fa-shield-alt"></i>
            <i class="fas fa-lock"></i>
            <i class="fas fa-key"></i>
        </div>
        
        <h3>
            <i class="fas fa-user-shield" style="color:#ffd166;"></i>
            نظام التفعيل الآمن
        </h3>
        
        <div class="app-description">
            <i class="fas fa-exclamation-circle" style="color:#ffd166;"></i>
            نظام محمي بطبقات أمنية متعددة. جميع المحاولات مسجلة ومراقبة.
        </div>
        
        <div class="security-status">
            <div class="security-status-item">
                <i class="fas fa-clock"></i>
                <span class="security-timer" id="securityTimer">00:00:00</span>
            </div>
            <div class="security-status-item">
                <i class="fas fa-history"></i>
                <span class="attempts-left" id="attemptsLeft">3 محاولات</span>
            </div>
        </div>
        
        <input type="text" 
               id="activationCodeInput" 
               placeholder="أدخل كود التفعيل (مثال: cc253d31-4b6e-4abf-a7f3-5104ad38f7c1)" 
               maxlength="36"
               oninput="validateCodeInput(this)"
               onkeypress="handleActivationKeyPress(event)">
        
        <div class="code-length-hint" id="codeLengthHint">
            <i class="fas fa-info-circle"></i>
            <span>36 حرفاً مطلوباً (تنسيق UUID)</span>
        </div>
        
        <button id="activateBtn" onclick="activateTool()">
            <i class="fas fa-play-circle" style="margin-left:10px;"></i>
            تفعيل النظام
        </button>
        
        <div id="activationError">
            <i class="fas fa-exclamation-triangle"></i>
            <span id="errorMessage">كود التفعيل غير صالح</span>
        </div>
        
        <div style="margin-top: 20px; font-size: 11px; color: #999; border-top: 1px solid #eee; padding-top: 10px;">
            <i class="fas fa-server"></i>
            نظام محمي | جميع الحقوق محفوظة
        </div>
    </div>
</div>

<!-- شريط الأخبار العلوي -->
<div class="top-marquee">
<div class="marquee-inner">
<i class="fas fa-bullhorn" style="margin-left:10px;"></i>
اختر نوع التقرير من التصنيفات المتاحة وحدّد الأدوات التعليمية المستخدمة في الدرس،
ثم اضغط زر التعبئة لتوليد محتوى البنود تلقائيًا.
يمكن إعادة التوليد لتغيير الصياغة وتعديل النصوص عند الحاجة.
</div>
</div>

<!-- شريط التحكم العلوي -->
<div class="control-bar">
    <div class="header-controls">
        <div class="app-title">
            <i class="fas fa-chalkboard-teacher"></i>
            <span>أداة التقارير التربوية الذكية</span>
        </div>
        
        <div class="date-toggle-container">
            <div class="date-display" id="currentDateDisplay">
                التاريخ الحالي
            </div>
            <input type="text" id="manualDateInput" 
                   placeholder="أدخل التاريخ الهجري (مثال: ١٤٤٦/٠٦/١٥)" 
                   onchange="updateManualDate()">
        </div>
        
        <div class="btn-group">
            <div class="btn-row">
                <button class="main-btn" id="saveTeacherBtn" onclick="saveTeacherData()" title="حفظ بيانات إدارة التعليم، اسم المدرسة، الصف، المادة، المستهدفون، المكان">
                    <i class="fas fa-chalkboard-teacher btn-icon"></i>
                    <span class="btn-text">حفظ بيانات المعلم</span>
                </button>
                <button class="main-btn" id="aiFillBtn" onclick="fillWithAI()" title="تعبئة جميع الحقول باستخدام الذكاء الاصطناعي">
                    <i class="fas fa-robot btn-icon"></i>
                    <span class="btn-text">تعبئة ذكية</span>
                </button>
                <button class="main-btn" id="pdfBtn" onclick="downloadPDF()" title="تحويل التقرير إلى PDF وتنزيله">
                    <i class="fas fa-file-pdf btn-icon"></i>
                    <span class="btn-text">تنزيل PDF</span>
                </button>
            </div>
            
            <div class="btn-row">
                <button class="main-btn" id="clearBtn" onclick="clearData()" title="مسح جميع البيانات المدخلة">
                    <i class="fas fa-trash-alt btn-icon"></i>
                    <span class="btn-text">مسح البيانات</span>
                </button>
                <button class="main-btn" id="supportBtn" onclick="openSupportModal()" title="الدعم الفني والتواصل مع المطور">
                    <i class="fas fa-headset btn-icon"></i>
                    <span class="btn-text">الدعم الفني</span>
                </button>
                <button class="main-btn" id="whatsappBtn" onclick="sharePDFWhatsApp()" title="مشاركة التقرير عبر واتساب">
                    <i class="fab fa-whatsapp btn-icon"></i>
                    <span class="btn-text">مشاركة واتساب</span>
                </button>
            </div>
        </div>
    </div>
</div>

<div class="wrapper">
<div class="input-section">
  
  <h2><i class="fas fa-tools" style="margin-left:10px;"></i>أداة إصدار التقارير التربوية</h2>
  
  <div class="form-group">
    <label><i class="fas fa-file-alt"></i>اسم التقرير</label>
    
    <!-- التصنيف العام -->
    <select id="reportCategory" oninput="handleReportCategory()" style="margin-bottom:10px;">
        <option value="">اختر تصنيف التقرير</option>
        <option value="التقارير التعليمية الصفية">أولا: التقارير التعليمية الصفية</option>
        <option value="التقارير العلاجية والدعم الفردي">ثانيا: التقارير العلاجية والدعم الفردي</option>
        <option value="التقارير التحفيزية والسلوكية">ثالثا: التقارير التحفيزية والسلوكية</option>
        <option value="تقارير الأنشطة غير الصفية">رابعا: تقارير الأنشطة غير الصفية</option>
        <option value="تقارير التواصل مع أولياء الأمور والمجتمع">سادسا: تقارير التواصل مع أولياء الأمور والمجتمع</option>
        <option value="التقارير التخطيطية والتنظيمية">سادسا: التقارير التخطيطية والتنظيمية</option>
        <option value="تقارير التقييم والمتابعة">سابعا: تقارير التقييم والمتابعة</option>
        <option value="تقارير التدريب والتطوير المهني">ثامنا: تقارير التدريب والتطوير المهني</option>
        <option value="تقارير توظيف التكنولوجيا">تاسعا: تقارير توظيف التكنولوجيا</option>
        <option value="تقارير البحث والتطوير المناهجي">عاشرا: تقارير البحث والتطوير المناهجي</option>
        <option value="تقارير الجودة واللجان">حادي عشر: تقارير الجودة واللجان</option>
        <option value="تقارير الأمن والسلامة">ثاني عشر: تقارير الأمن والسلامة</option>
        <option value="أخرى">تقارير أخرى (إدخال يدوي)</option>
    </select>
    
    <!-- حقل البحث -->
    <div id="reportSearchContainer" style="display:block; margin-bottom:10px; position:relative;">
        <input type="text" id="reportSearch" placeholder="ابحث عن تقرير..." style="width:100%; padding:12px; border:1px solid #d4ebe2; border-radius:6px; font-size:14px;">
        <div id="searchResults" style="display:none; position:absolute; top:100%; left:0; right:0; background:white; border:1px solid #ddd; border-radius:6px; max-height:200px; overflow-y:auto; z-index:1000; box-shadow:0 4px 12px rgba(0,0,0,0.1);"></div>
    </div>
    
    <!-- قائمة التقارير المنسدلة -->
    <select id="reportType" oninput="handleReportType()" style="display:none;">
        <option value="">اختر تقريرًا</option>
    </select>
    
    <!-- حقل الإدخال للنوع "أخرى" -->
    <input id="reportTypeInput" placeholder="أدخل اسم التقرير" oninput="updateReport()" style="display:none; margin-top:8px;">
    
    <!-- خانة عنوان التقرير اليدوية - جديد -->
    <div class="manual-title-container">
        <label><i class="fas fa-heading"></i>عنوان التقرير (يدوي)</label>
        <input type="text" id="manualReportTitle" placeholder="أدخل عنوان التقرير يدوياً..." oninput="updateManualTitle()">
    </div>
  </div>
  
  <div class="form-group">
    <label><i class="fas fa-university"></i>إدارة التعليم</label>
    <select id="education" oninput="updateReport()">
      <option>الإدارة العامة للتعليم بمنطقة مكة المكرمة</option>
      <option>الإدارة العامة للتعليم بمنطقة الرياض</option>
      <option>الإدارة العامة للتعليم بمنطقة المدينة المنورة</option>
      <option>الإدارة العامة للتعليم بالمنطقة الشرقية</option>
      <option>الإدارة العامة للتعليم بمنطقة القصيم</option>
      <option>الإدارة العامة للتعليم بمنطقة عسير</option>
      <option>الإدارة العامة للتعليم بمنطقة تبوك</option>
      <option>الإدارة العامة للتعليم بمنطقة حائل</option>
      <option>الإدارة العامة للتعليم بمنطقة الحدود الشمالية</option>
      <option>الإدارة العامة للتعليم بمنطقة جازان</option>
      <option>الإدارة العامة للتعليم بمنطقة نجران</option>
      <option>الإدارة العامة للتعليم بمنطقة الباحة</option>
      <option>الإدارة العامة للتعليم بمنطقة الجوف</option>
      <option>الإدارة العامة للتعليم بمحافظة الأحساء</option>
      <option>الإدارة العامة للتعليم بمحافظة الطائف</option>
      <option>الإدارة العامة للتعليم بمحافظة جدة</option>
    </select>
  </div>
  
  <div class="form-group">
    <label><i class="fas fa-school"></i>اسم المدرسة</label>
    <input id="school" value="سعيد بن العاص" placeholder="أدخل اسم المدرسة" oninput="updateReport()">
  </div>
  
  <div class="form-row">
    <div class="form-group">
      <label><i class="fas fa-chalkboard-teacher"></i>صفة المعلّم</label>
      <select id="teacherType" oninput="updateReport()">
        <option selected>المعلم</option>
        <option>المعلمة</option>
      </select>
    </div>
    
    <div class="form-group">
      <label><i class="fas fa-user"></i>اسم المعلّم</label>
      <input id="teacher" placeholder="اسم المعلم" oninput="updateReport()">
    </div>
  </div>
  
  <div class="form-row">
    <div class="form-group">
      <label><i class="fas fa-user-tie"></i>صفة المدير</label>
      <select id="principalType" oninput="updateReport()">
        <option selected>المدير</option>
        <option>المديرة</option>
      </select>
    </div>
    
    <div class="form-group">
      <label><i class="fas fa-user-cog"></i>اسم المدير</label>
      <input id="principal" placeholder="اسم مدير المدرسة" oninput="updateReport()">
    </div>
  </div>
  
  <div class="form-row">
    <div class="form-group">
      <label><i class="fas fa-users-class"></i>الصف</label>
      <input id="grade" placeholder="مثال: ٥/٣" oninput="updateReport()">
    </div>
    
    <div class="form-group">
      <label><i class="fas fa-calendar-alt"></i>الفصل الدراسي</label>
      <select id="term" oninput="updateReport()">
        <option></option><option>الأول</option><option>الثاني</option>
      </select>
    </div>
  </div>
  
  <!-- المادة والدرس - أصبحا بجوار بعضهما -->
  <div class="form-row">
    <div class="form-group">
      <label><i class="fas fa-book"></i>المادة</label>
      <input id="subject" placeholder="مثال: لغتي – علوم – رياضيات" oninput="updateReport()">
    </div>
    
    <div class="form-group">
      <label><i class="fas fa-book-open"></i>الدرس</label>
      <input id="lesson" placeholder="مثال: درس الضرب - درس النباتات" oninput="updateReport()">
    </div>
  </div>
  
  <div class="form-row">
    <div class="form-group">
      <label><i class="fas fa-bullseye"></i>المستهدفون</label>
      <input id="target" placeholder="مثال: جميع طلاب الصف" oninput="updateReport()">
    </div>
    
    <div class="form-group">
      <label><i class="fas fa-user-check"></i>عدد الحضور</label>
      <input id="count" placeholder="مثال: ٢٥ طالب" oninput="updateReport()">
    </div>
  </div>
  
  <div class="form-group">
    <label><i class="fas fa-map-marker-alt"></i>مكان التنفيذ</label>
    <input id="place" placeholder="مثال: داخل الصف – المختبر" oninput="updateReport()">
  </div>
  
  <div class="form-group">
    <label><i class="fas fa-flag"></i>الهدف التربوي</label>
    <textarea id="goal" placeholder="أدخل الهدف التربوي" oninput="updateReport()"></textarea>
  </div>
  
  <div class="form-group">
    <label><i class="fas fa-file-signature"></i>نبذة مختصرة</label>
    <textarea id="summary" placeholder="أدخل نبذة مختصرة" oninput="updateReport()"></textarea>
  </div>
  
  <div class="form-group">
    <label><i class="fas fa-tasks"></i>إجراءات التنفيذ</label>
    <textarea id="steps" placeholder="كيف تم تنفيذ النشاط؟" oninput="updateReport()"></textarea>
  </div>
  
  <div class="form-group">
    <label><i class="fas fa-chess-board"></i>الاستراتيجيات</label>
    <textarea id="strategies" placeholder="ما هي الاستراتيجيات" oninput="updateReport()"></textarea>
  </div>
  
  <div class="form-row">
    <div class="form-group">
      <label><i class="fas fa-thumbs-up"></i>نقاط القوة</label>
      <textarea id="strengths" placeholder="نقاط القوة" oninput="updateReport()"></textarea>
    </div>
    
    <div class="form-group">
      <label><i class="fas fa-tools"></i>نقاط التحسين</label>
      <textarea id="improve" placeholder="نقاط تحتاج تطوير" oninput="updateReport()"></textarea>
    </div>
  </div>
  
  <div class="form-group">
    <label><i class="fas fa-lightbulb"></i>التوصيات</label>
    <textarea id="recomm" placeholder="توصيات مستقبلية" oninput="updateReport()"></textarea>
  </div>
  
  <!-- قسم الأدوات والوسائل التعليمية -->
  <div class="form-group">
    <label><i class="fas fa-tools"></i>الأدوات والوسائل التعليمية</label>
    <div class="tools-section">
      <div class="tools-grid">
        <label class="tool-checkbox" onclick="toggleTool(this)">
          <input type="checkbox" id="tool1" value="سبورة" style="display:none;">
          <span>سبورة</span>
          <span class="checkmark">✅</span>
        </label>
        <label class="tool-checkbox" onclick="toggleTool(this)">
          <input type="checkbox" id="tool2" value="سبورة ذكية" style="display:none;">
          <span>سبورة ذكية</span>
          <span class="checkmark">✅</span>
        </label>
        <label class="tool-checkbox" onclick="toggleTool(this)">
          <input type="checkbox" id="tool3" value="جهاز عرض" style="display:none;">
          <span>جهاز عرض</span>
          <span class="checkmark">✅</span>
        </label>
        <label class="tool-checkbox" onclick="toggleTool(this)">
          <input type="checkbox" id="tool4" value="أوراق عمل" style="display:none;">
          <span>أوراق عمل</span>
          <span class="checkmark">✅</span>
        </label>
        <label class="tool-checkbox" onclick="toggleTool(this)">
          <input type="checkbox" id="tool5" value="حاسب" style="display:none;">
          <span>حاسب</span>
          <span class="checkmark">✅</span>
        </label>
        <label class="tool-checkbox" onclick="toggleTool(this)">
          <input type="checkbox" id="tool6" value="عرض تقديمي" style="display:none;">
          <span>عرض تقديمي</span>
          <span class="checkmark">✅</span>
        </label>
        <label class="tool-checkbox" onclick="toggleTool(this)">
          <input type="checkbox" id="tool7" value="بطاقات تعليمية" style="display:none;">
          <span>بطاقات تعليمية</span>
          <span class="checkmark">✅</span>
        </label>
        <label class="tool-checkbox" onclick="toggleTool(this)">
          <input type="checkbox" id="tool8" value="صور توضيحية" style="display:none;">
          <span>صور توضيحية</span>
          <span class="checkmark">✅</span>
        </label>
        <label class="tool-checkbox" onclick="toggleTool(this)">
          <input type="checkbox" id="tool9" value="كتاب" style="display:none;">
          <span>كتاب</span>
          <span class="checkmark">✅</span>
        </label>
        <label class="tool-checkbox" onclick="toggleTool(this)">
          <input type="checkbox" id="tool10" value="أدوات رياضية" style="display:none;">
          <span>أدوات رياضية</span>
          <span class="checkmark">✅</span>
        </label>
      </div>
      <div style="text-align:center; margin-top:10px; font-size:11px; color:#666;">
        <i class="fas fa-info-circle"></i> اضغط على الأداة لتحديدها، ستظهر علامة ✅ عند التحديد
      </div>
    </div>
  </div>
  
  <div class="form-row">
    <div class="form-group">
      <label><i class="fas fa-camera"></i>الصورة 1</label>
      <input type="file" accept="image/*" placeholder="ارفع صورة" onchange="loadImage(this,'imgBox1')">
    </div>
    
    <div class="form-group">
      <label><i class="fas fa-camera"></i>الصورة 2</label>
      <input type="file" accept="image/*" placeholder="ارفع صورة" onchange="loadImage(this,'imgBox2')">
    </div>
  </div>

</div>
</div>

<!-- قسم PDF المعدل - تم تبديل نوع التقرير والمستهدفون حسب طلبك -->
<div id="report-content" class="pdf-export" style="display:none;">

<div class="header">
  <img src="https://i.ibb.co/1fc5gB6v/9-C92-E57-B-23-FA-479-D-A024-1-D5-F871-B4-F8-D.png">
  <div class="header-school-title">اسم المدرسة</div>
  <div class="header-school" id="schoolBox"></div>
  <div class="header-education" id="educationBox"></div>
  <div class="header-date">
    <span id="hDate"></span><br>
    <span id="gDate"></span>
  </div>
</div>

<!-- تم تبديل المستهدفون مكان نوع التقرير هنا -->
<div class="info-grid">
  <div class="info-box"><div class="info-title">الفصل الدراسي</div><div class="info-value" id="termBox"></div></div>
  <div class="info-box"><div class="info-title">الصف</div><div class="info-value" id="gradeBox"></div></div>
  <div class="info-box"><div class="info-title">العدد</div><div class="info-value" id="countBox"></div></div>
  <!-- التعديل: المستهدفون الآن في الصف الأول بدلاً من نوع التقرير -->
  <div class="info-box"><div class="info-title">المستهدفون</div><div class="info-value" id="targetBox"></div></div>
</div>

<!-- تم تبديل نوع التقرير مكان المستهدفون هنا -->
<div class="info-grid2">
  <!-- التعديل: نوع التقرير الآن في الصف الثاني بدلاً من المستهدفون -->
  <div class="info-box"><div class="info-title">نوع التقرير</div><div class="info-value" id="reportTypeBox"></div></div>

  <div class="subject-lesson-box">
    <div class="subject-lesson-title">المادة | الدرس</div>
    <div class="subject-lesson">
      <div id="subjectBox"></div>
      <div class="subject-divider"></div>
      <div id="lessonBox"></div>
    </div>
  </div>

  <div class="info-box"><div class="info-title">مكان التنفيذ</div><div class="info-value" id="placeBox"></div></div>
</div>

<div class="box-objective">
  <div class="box-title">الهدف التربوي</div>
  <div class="box-content" id="goalBox"></div>
</div>

<div class="row">
  <div class="box"><div class="box-title">النبذة</div><div class="box-content" id="summaryBox"></div></div>
  <div class="box"><div class="box-title">إجراءات التنفيذ</div><div class="box-content" id="stepsBox"></div></div>
</div>

<div class="row">
  <div class="box"><div class="box-title">الاستراتيجيات</div><div class="box-content" id="strategiesBox"></div></div>
  <div class="box"><div class="box-title">نقاط القوة</div><div class="box-content" id="strengthsBox"></div></div>
</div>

<div class="row">
  <div class="box"><div class="box-title">نقاط التحسين</div><div class="box-content" id="improveBox"></div></div>
  <div class="box"><div class="box-title">التوصيات</div><div class="box-content" id="recommBox"></div></div>
</div>

<div class="tools-box">
  <div class="tools-title">الأدوات والوسائل التعليمية</div>
  <div class="tools-list" id="toolsListBox"></div>
</div>

<div class="images">
  <div class="image-box" id="imgBox1"></div>
  <div class="image-box" id="imgBox2"></div>
</div>

<div class="signatures">
  <div class="signature-box">
    <div class="signature-role" id="teacherTypeBox"></div>
    <div class="signature-name" id="teacherBox"></div>
    <div class="sign-line"></div>
  </div>
  <div class="signature-box">
    <div class="signature-role" id="principalTypeBox"></div>
    <div class="signature-name" id="principalBox"></div>
    <div class="sign-line"></div>
  </div>
</div>

<div class="footer-box">
  وزارة التعليم – المملكة العربية السعودية
</div>

</div>

<script>
// ==================== متغيرات التفعيل والأمن ====================
const ACTIVATION_KEY_NAME = "activation_code";
const BACKEND_URL = "https://deep-qphc.onrender.com";

// متغيرات الأمن
let activationAttempts = 0;
const MAX_ATTEMPTS = 3;
let isSystemLocked = false;
let lockTimer = null;
let securityTimerInterval = null;
let lastAttemptTime = 0;
const ATTEMPT_DELAY = 2000; // تأخير 2 ثانية بين المحاولات

// ==================== دوال الأمن ====================

// تحديث عداد المحاولات
function updateAttemptCounter() {
    const counter = document.getElementById('attemptCounter');
    const countSpan = document.getElementById('attemptCount');
    const attemptsLeft = document.getElementById('attemptsLeft');
    
    if (counter && countSpan) {
        countSpan.textContent = activationAttempts;
        counter.classList.remove('warning', 'danger');
        
        if (activationAttempts >= MAX_ATTEMPTS) {
            counter.classList.add('danger');
            if (attemptsLeft) attemptsLeft.textContent = 'محاولات منتهية';
        } else if (activationAttempts >= 2) {
            counter.classList.add('warning');
            if (attemptsLeft) attemptsLeft.textContent = `${MAX_ATTEMPTS - activationAttempts} محاولة`;
        } else {
            if (attemptsLeft) attemptsLeft.textContent = `${MAX_ATTEMPTS - activationAttempts} محاولات`;
        }
    }
}

// التحقق من صحة الإدخال في الوقت الحقيقي
function validateCodeInput(input) {
    const value = input.value.toLowerCase();
    const hint = document.getElementById('codeLengthHint');
    
    // السماح فقط بالأحرف الإنجليزية الصغيرة، الأرقام، والشرطات
    const cleaned = value.replace(/[^a-z0-9\-]/g, '');
    input.value = cleaned;
    
    // تحديث التلميح
    if (hint) {
        const remaining = 36 - cleaned.length;
        if (remaining > 0) {
            hint.innerHTML = `<i class="fas fa-info-circle"></i> ${remaining} حرفاً متبقياً`;
            hint.style.color = remaining < 5 ? '#dc3545' : '#666';
        } else {
            hint.innerHTML = `<i class="fas fa-check-circle" style="color:#28a745;"></i> الكود مكتمل`;
            hint.style.color = '#28a745';
        }
    }
}

// التعامل مع ضغط المفاتيح
function handleActivationKeyPress(event) {
    if (event.key === 'Enter') {
        event.preventDefault();
        activateTool();
    }
}

// قفل النظام
function lockSystem() {
    if (isSystemLocked) return;
    
    isSystemLocked = true;
    
    // إظهار طبقة الأمان
    document.getElementById('securityOverlay').style.display = 'flex';
    document.getElementById('activationScreen').style.display = 'none';
    
    // تعطيل زر التفعيل
    const activateBtn = document.getElementById('activateBtn');
    if (activateBtn) {
        activateBtn.disabled = true;
    }
    
    // بدء العد التنازلي
    let seconds = 60;
    const timerElement = document.getElementById('lockdownTimer');
    
    const countdown = setInterval(() => {
        seconds--;
        if (timerElement) {
            timerElement.textContent = seconds;
        }
        
        if (seconds <= 0) {
            clearInterval(countdown);
            location.reload();
        }
    }, 1000);
    
    lockTimer = setTimeout(() => {
        location.reload();
    }, 60000);
}

// إعادة تعيين النظام
function resetSystem() {
    isSystemLocked = false;
    
    if (lockTimer) {
        clearTimeout(lockTimer);
        lockTimer = null;
    }
    
    document.getElementById('securityOverlay').style.display = 'none';
    document.getElementById('attemptCounter').style.display = 'none';
    
    // إعادة تعيين المحاولات
    activationAttempts = 0;
    updateAttemptCounter();
}

// بدء مؤقت الأمان
function startSecurityTimer() {
    if (securityTimerInterval) clearInterval(securityTimerInterval);
    
    securityTimerInterval = setInterval(() => {
        const now = new Date();
        const timeString = now.toLocaleTimeString('ar-SA', {
            hour12: false,
            hour: '2-digit',
            minute: '2-digit',
            second: '2-digit'
        });
        
        const timerElement = document.getElementById('securityTimer');
        if (timerElement) {
            timerElement.textContent = timeString;
        }
    }, 1000);
}

// ==================== دالة التفعيل الرئيسية المعدلة ====================
async function activateTool() {
    // التحقق من التأخير بين المحاولات
    const now = Date.now();
    if (now - lastAttemptTime < ATTEMPT_DELAY) {
        const remaining = Math.ceil((ATTEMPT_DELAY - (now - lastAttemptTime)) / 1000);
        showActivationError(`الرجاء الانتظار ${remaining} ثانية`);
        return;
    }
    
    lastAttemptTime = now;
    
    // التحقق من حالة القفل
    if (isSystemLocked) {
        showActivationError("النظام مغلق مؤقتاً لأسباب أمنية");
        return;
    }
    
    // التحقق من عدد المحاولات
    if (activationAttempts >= MAX_ATTEMPTS) {
        lockSystem();
        return;
    }
    
    const codeInput = document.getElementById("activationCodeInput");
    const code = codeInput.value.trim().toLowerCase();
    
    // التحقق الأساسي
    if (!code) {
        showActivationError("الرجاء إدخال كود التفعيل");
        codeInput.focus();
        return;
    }
    
    // التحقق من نمط UUID (36 حرف مع شرطات)
    const uuidPattern = /^[0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12}$/;
    
    if (!uuidPattern.test(code)) {
        showActivationError("تنسيق كود التفعيل غير صحيح. يجب أن يكون بصيغة UUID مثل: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx");
        codeInput.select();
        return;
    }
    
    // إعداد زر التفعيل
    const activateButton = document.getElementById('activateBtn');
    const originalText = activateButton.innerHTML;
    
    activateButton.innerHTML = '<i class="fas fa-spinner fa-spin" style="margin-left:10px;"></i> جاري التحقق الآمن...';
    activateButton.disabled = true;
    
    try {
        // الاتصال بالخادم للتحقق
        const response = await fetch(BACKEND_URL + "/verify", {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
                'Accept': 'application/json'
            },
            body: JSON.stringify({
                code: code,
                timestamp: new Date().toISOString()
            })
        });
        
        const data = await response.json();
        
        if (response.ok && data.valid) {
            // نجاح التفعيل
            localStorage.setItem(ACTIVATION_KEY_NAME, code);
            hideActivationScreen();
            showNotification("✅ تم تفعيل النظام بنجاح!");
            resetSystem();
            initializeApp();
        } else {
            // زيادة المحاولات عند الفشل
            activationAttempts++;
            updateAttemptCounter();
            throw new Error(data.message || "كود التفعيل غير صالح");
        }
        
    } catch (error) {
        // عرض رسالة الخطأ المناسبة
        let errorMessage = error.message || "كود التفعيل غير صالح";
        
        if (error.message.includes("Too many attempts") || error.message.includes("Locked")) {
            errorMessage = "تم تجاوز عدد المحاولات المسموح بها";
            lockSystem();
        } else if (error.message.includes("expired")) {
            errorMessage = "كود التفعيل منتهي الصلاحية";
        } else if (error.message.includes("inactive")) {
            errorMessage = "كود التفعيل غير مفعل";
        } else if (error.message.includes("not found")) {
            errorMessage = "كود التفعيل غير موجود";
        } else if (error.message.includes("network")) {
            errorMessage = "خطأ في الاتصال بالخادم. تحقق من اتصال الإنترنت";
        }
        
        showActivationError(errorMessage);
        
    } finally {
        // إعادة حالة الزر
        activateButton.innerHTML = originalText;
        activateButton.disabled = false;
        
        // تنظيف حقل الإدخال بعد خطأ
        if (activationAttempts > 0) {
            codeInput.value = '';
            codeInput.focus();
        }
    }
}

// ==================== دوال النظام العامة ====================

function showActivationError(message = "كود التفعيل غير صالح") {
    const errorDiv = document.getElementById('activationError');
    const errorMessage = document.getElementById('errorMessage');
    
    if (errorMessage) {
        errorMessage.textContent = message;
    }
    
    errorDiv.style.display = 'block';
    
    // تأثير اهتزاز
    const inputElement = document.getElementById('activationCodeInput');
    inputElement.style.animation = 'shake 0.5s ease-in-out';
    inputElement.style.borderColor = '#dc3545';
    
    setTimeout(() => {
        inputElement.style.animation = '';
        inputElement.style.borderColor = '#d4ebe2';
        errorDiv.style.display = 'none';
    }, 3000);
}

function hideActivationScreen() {
    document.getElementById("activationScreen").style.display = "none";
    document.body.style.overflow = "auto";
    document.getElementById("attemptCounter").style.display = "none";
}

function showNotification(message) {
    // دالة عرض الإشعارات
    const notification = document.createElement('div');
    notification.className = 'notification';
    notification.innerHTML = `<i class="fas fa-check-circle"></i> <span>${message}</span>`;
    document.body.appendChild(notification);
    
    setTimeout(() => notification.classList.add('show'), 100);
    setTimeout(() => {
        notification.classList.remove('show');
        setTimeout(() => notification.remove(), 400);
    }, 3000);
}

// ==================== تهيئة النظام ====================
window.onload = function() {
    // بدء مؤقت الأمان
    startSecurityTimer();
    
    // إظهار عداد المحاولات
    updateAttemptCounter();
    document.getElementById('attemptCounter').style.display = 'flex';
    
    // التحقق من التفعيل المسبق
    const savedCode = localStorage.getItem(ACTIVATION_KEY_NAME);
    
    if (savedCode) {
        // التحقق من صحة الكود المخزن
        fetch(BACKEND_URL + "/verify", {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({
                code: savedCode
            })
        })
        .then(response => response.json())
        .then(data => {
            if (data.valid) {
                hideActivationScreen();
                initializeApp();
            } else {
                // الكود غير صالح
                localStorage.removeItem(ACTIVATION_KEY_NAME);
                document.getElementById("activationScreen").style.display = "flex";
            }
        })
        .catch(() => {
            // في حالة فشل الاتصال، السماح باستخدام محلي مع تحذير
            hideActivationScreen();
            initializeApp();
            showNotification("⚠️ اتصال محدود - بعض الميزات قد لا تعمل");
        });
    } else {
        // لا يوجد كود مفعل
        document.getElementById("activationScreen").style.display = "flex";
    }
    
    // التركيز على حقل الإدخال بعد تحميل الصفحة
    setTimeout(() => {
        const activationInput = document.getElementById('activationCodeInput');
        if (activationInput) activationInput.focus();
    }, 500);
};

// دالة تهيئة التطبيق
function initializeApp() {
    // تحميل التواريخ
    loadDates();
    
    // تحميل البيانات المحفوظة
    loadTeacherData();
    
    // تحديث التقرير
    updateReport();
    
    // إضافة مستمع البحث
    const reportSearch = document.getElementById('reportSearch');
    if (reportSearch) {
        reportSearch.addEventListener('input', handleReportSearch);
    }
}

// ==================== دوال النظام الأساسية ====================
function loadDates() {
    // دالة تحميل التواريخ
    const now = new Date();
    const hijriDate = "١٤٤٦/٠٦/٠١"; // مثال
    document.getElementById('manualDateInput').value = hijriDate;
    document.getElementById('currentDateDisplay').textContent = `هـ: ${hijriDate}`;
}

function loadTeacherData() {
    // دالة تحميل بيانات المعلم
    const savedData = localStorage.getItem('teacherData');
    if (savedData) {
        try {
            const data = JSON.parse(savedData);
            // تحميل البيانات في الحقول
            if (data.education) document.getElementById('education').value = data.education;
            if (data.school) document.getElementById('school').value = data.school;
            if (data.teacher) document.getElementById('teacher').value = data.teacher;
            if (data.principal) document.getElementById('principal').value = data.principal;
            if (data.grade) document.getElementById('grade').value = data.grade;
            if (data.term) document.getElementById('term').value = data.term;
            if (data.subject) document.getElementById('subject').value = data.subject;
            if (data.lesson) document.getElementById('lesson').value = data.lesson;
            if (data.target) document.getElementById('target').value = data.target;
            if (data.count) document.getElementById('count').value = data.count;
            if (data.place) document.getElementById('place').value = data.place;
            if (data.manualTitle) document.getElementById('manualReportTitle').value = data.manualTitle;
            
            // تحميل النصوص الطويلة
            if (data.goal) document.getElementById('goal').value = data.goal;
            if (data.summary) document.getElementById('summary').value = data.summary;
            if (data.steps) document.getElementById('steps').value = data.steps;
            if (data.strategies) document.getElementById('strategies').value = data.strategies;
            if (data.strengths) document.getElementById('strengths').value = data.strengths;
            if (data.improve) document.getElementById('improve').value = data.improve;
            if (data.recomm) document.getElementById('recomm').value = data.recomm;
            
            // تحميل الأدوات
            if (data.tools && Array.isArray(data.tools)) {
                for (let i = 1; i <= 10; i++) {
                    const toolCheckbox = document.getElementById(`tool${i}`);
                    if (toolCheckbox) {
                        const toolElement = toolCheckbox.closest('.tool-checkbox');
                        const isChecked = data.tools.includes(toolCheckbox.value);
                        toolCheckbox.checked = isChecked;
                        if (isChecked) {
                            toolElement.classList.add('checked');
                        }
                    }
                }
                updateToolsDisplay();
            }
            
        } catch (e) {
            console.error('خطأ في تحميل البيانات:', e);
        }
    }
}

function updateReport() {
    // دالة تحديث التقرير
    const education = document.getElementById('education').value;
    const school = document.getElementById('school').value;
    const teacher = document.getElementById('teacher').value;
    const principal = document.getElementById('principal').value;
    const grade = document.getElementById('grade').value;
    const term = document.getElementById('term').value;
    const subject = document.getElementById('subject').value;
    const lesson = document.getElementById('lesson').value;
    const target = document.getElementById('target').value;
    const count = document.getElementById('count').value;
    const place = document.getElementById('place').value;
    
    // تحديث PDF
    if (document.getElementById('educationBox')) {
        document.getElementById('educationBox').textContent = education;
        document.getElementById('schoolBox').textContent = school;
        document.getElementById('teacherBox').textContent = teacher;
        document.getElementById('principalBox').textContent = principal;
        document.getElementById('gradeBox').textContent = grade;
        document.getElementById('termBox').textContent = term ? `الفصل الدراسي ${term}` : '';
        document.getElementById('subjectBox').textContent = subject;
        document.getElementById('lessonBox').textContent = lesson;
        document.getElementById('targetBox').textContent = target;
        document.getElementById('countBox').textContent = count;
        document.getElementById('placeBox').textContent = place;
    }
}

function handleReportSearch() {
    // دالة البحث (يجب إكمالها حسب الحاجة)
    const searchTerm = document.getElementById('reportSearch').value;
    // تنفيذ البحث
}

function updateToolsDisplay() {
    // تحديث عرض الأدوات
    const toolsListBox = document.getElementById('toolsListBox');
    if (toolsListBox) {
        const selectedTools = [];
        for (let i = 1; i <= 10; i++) {
            const toolCheckbox = document.getElementById(`tool${i}`);
            if (toolCheckbox && toolCheckbox.checked) {
                selectedTools.push(toolCheckbox.value);
            }
        }
        
        toolsListBox.innerHTML = '';
        selectedTools.forEach(tool => {
            const toolElement = document.createElement('div');
            toolElement.className = 'tool';
            toolElement.innerHTML = `<span>✓</span> ${tool}`;
            toolsListBox.appendChild(toolElement);
        });
    }
}

function toggleTool(element) {
    const checkbox = element.querySelector('input[type="checkbox"]');
    checkbox.checked = !checkbox.checked;
    element.classList.toggle('checked');
    updateToolsDisplay();
}

// بقية الدوال حسب الحاجة...
</script>
</body>
</html>