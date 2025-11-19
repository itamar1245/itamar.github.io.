# itamar.github.io.
תכניסו את הטקסט והוא יוצר עליו את המבחן שתרצו
<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>מערכת מבחנים חכמה</title>
<style>
* {
margin: 0;
padding: 0;
box-sizing: border-box;
}

body {
font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
min-height: 100vh;
padding: 20px;
}

.container {
max-width: 1200px;
margin: 0 auto;
}

.header {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 30px;
}

h1 {
color: white;
font-size: 2.5em;
text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
}

.mode-toggle {
background: white;
border-radius: 25px;
padding: 5px;
display: flex;
gap: 5px;
box-shadow: 0 5px 15px rgba(0,0,0,0.2);
}

.mode-btn {
background: transparent;
color: #667eea;
border: none;
padding: 10px 20px;
border-radius: 20px;
font-size: 16px;
font-weight: 600;
cursor: pointer;
transition: all 0.3s;
}

.mode-btn.active {
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
color: white;
}

.welcome-screen {
background: white;
border-radius: 15px;
padding: 50px;
text-align: center;
box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

.welcome-screen h2 {
color: #667eea;
font-size: 2em;
margin-bottom: 20px;
}

.welcome-screen p {
color: #666;
font-size: 1.2em;
margin-bottom: 40px;
}

.option-cards {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
gap: 30px;
margin-top: 30px;
}

.option-card {
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
color: white;
padding: 40px;
border-radius: 15px;
cursor: pointer;
transition: transform 0.3s, box-shadow 0.3s;
text-align: center;
}

.option-card:hover {
transform: translateY(-10px);
box-shadow: 0 15px 40px rgba(102, 126, 234, 0.4);
}

.option-card .icon {
font-size: 4em;
margin-bottom: 20px;
}

.option-card h3 {
font-size: 1.8em;
margin-bottom: 15px;
}

.option-card p {
font-size: 1.1em;
opacity: 0.9;
}

.card {
background: white;
border-radius: 15px;
padding: 30px;
margin-bottom: 20px;
box-shadow: 0 10px 30px rgba(0,0,0,0.2);
display: none;
}

.card.active {
display: block;
animation: fadeIn 0.5s;
}

@keyframes fadeIn {
from { opacity: 0; transform: translateY(20px); }
to { opacity: 1; transform: translateY(0); }
}

.card h2 {
color: #667eea;
margin-bottom: 20px;
font-size: 1.8em;
}

label {
display: block;
margin: 15px 0 5px;
font-weight: 600;
color: #333;
}

textarea, input, select {
width: 100%;
padding: 12px;
border: 2px solid #e0e0e0;
border-radius: 8px;
font-size: 16px;
transition: border-color 0.3s;
font-family: inherit;
}

textarea {
min-height: 150px;
resize: vertical;
}

textarea:focus, input:focus, select:focus {
outline: none;
border-color: #667eea;
}

button {
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
color: white;
border: none;
padding: 12px 30px;
border-radius: 8px;
font-size: 16px;
font-weight: 600;
cursor: pointer;
transition: transform 0.2s, box-shadow 0.2s;
margin: 10px 5px;
}

button:hover {
transform: translateY(-2px);
box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
}

button:active {
transform: translateY(0);
}

button:disabled {
opacity: 0.5;
cursor: not-allowed;
}

.controls {
display: flex;
gap: 15px;
flex-wrap: wrap;
align-items: end;
}

.control-group {
flex: 1;
min-width: 200px;
}

.quiz-question {
background: #f8f9fa;
padding: 20px;
margin: 15px 0;
border-radius: 10px;
border-left: 4px solid #667eea;
}

.quiz-question h3 {
color: #333;
margin-bottom: 15px;
font-size: 1.1em;
}

.quiz-question .type-badge {
display: inline-block;
padding: 4px 12px;
border-radius: 20px;
font-size: 0.85em;
font-weight: 600;
margin-bottom: 10px;
}

.type-mc { background: #e3f2fd; color: #1976d2; }
.type-tf { background: #fff3e0; color: #f57c00; }
.type-blank { background: #f3e5f5; color: #7b1fa2; }

.options label {
display: flex;
align-items: center;
padding: 10px;
margin: 8px 0;
background: white;
border-radius: 8px;
cursor: pointer;
transition: background 0.2s;
}

.options label:hover {
background: #e8eaf6;
}

.options input[type="radio"] {
width: auto;
margin-left: 10px;
}

input[type="text"].answer-input {
margin-top: 10px;
}

.result {
margin-top: 20px;
padding: 20px;
border-radius: 10px;
font-size: 1.2em;
font-weight: 600;
text-align: center;
}

.result.good {
background: #c8e6c9;
color: #2e7d32;
}

.result.medium {
background: #fff9c4;
color: #f57f17;
}

.result.poor {
background: #ffcdd2;
color: #c62828;
}

.share-section {
background: #f8f9fa;
padding: 20px;
border-radius: 10px;
margin-top: 20px;
}

.share-link {
display: flex;
gap: 10px;
align-items: center;
margin-top: 10px;
}

.share-link input {
flex: 1;
background: white;
}

.phone-input-section {
background: #e3f2fd;
padding: 30px;
border-radius: 15px;
text-align: center;
margin-bottom: 20px;
}

.phone-input-section h3 {
color: #1976d2;
margin-bottom: 15px;
}

.phone-input-section input {
max-width: 300px;
margin: 0 auto;
text-align: center;
font-size: 1.2em;
}

.analysis {
background: #f8f9fa;
padding: 20px;
border-radius: 10px;
margin-top: 20px;
}

.analysis h3 {
color: #667eea;
margin-bottom: 15px;
}

.analysis-item {
padding: 10px;
margin: 10px 0;
background: white;
border-radius: 8px;
border-right: 4px solid #667eea;
}

.hidden {
display: none !important;
}

@media (max-width: 768px) {
h1 {
font-size: 1.8em;
}
.header {
flex-direction: column;
gap: 15px;
}
.controls {
flex-direction: column;
}
.control-group {
width: 100%;
}
}
</style>
</head>
<body>
<div class="container">
<div class="header">
<h1>🎓 מערכת מבחנים חכמה</h1>
<div class="mode-toggle">
<button class="mode-btn active" onclick="switchMode('create')">יצירת מבחן</button>
<button class="mode-btn" onclick="switchMode('take')">ביצוע מבחן</button>
</div>
</div>

<div id="welcomeScreen" class="welcome-screen hidden">
<h2>ברוכים הבאים למערכת המבחנים החכמה</h2>
<p>בחר את הפעולה המתאימה עבורך</p>
<div class="option-cards">
<div class="option-card" onclick="selectOption('create')">
<div class="icon">✏️</div>
<h3>צור מבחן חדש</h3>
<p>הדבק טקסט וצור מבחן אוטומטי עם שאלות מגוונות</p>
</div>
<div class="option-card" onclick="selectOption('take')">
<div class="icon">📝</div>
<h3>בצע מבחן</h3>
<p>הזן קוד מבחן והתחל לענות על השאלות</p>
</div>
</div>
</div>

<div id="createSection" class="card">
<h2>צור מבחן חדש</h2>
<label>הדבק טקסט ממנו ייווצר המבחן</label>
<textarea id="textInput" placeholder="הזן או הדבק כאן טקסט באורך כלשהו. המערכת תזהה מילות מפתח ותיצור שאלות באופן אוטומטי..."></textarea>

<div class="controls">
<div class="control-group">
<label>סוג שאלות</label>
<select id="typeSelect">
<option value="mixed">מעורב (כל הסוגים)</option>
<option value="mc">רב ברירה</option>
<option value="tf">נכון/לא נכון</option>
<option value="blank">מילוי חסר</option>
</select>
</div>
<div class="control-group">
<label>רמת קושי</label>
<select id="difficultySelect">
<option value="easy">קל</option>
<option value="medium">בינוני</option>
<option value="hard">קשה</option>
</select>
</div>
<div class="control-group">
<label>מספר שאלות</label>
<input type="number" id="numQuestions" value="10" min="1" max="50" />
</div>
</div>

<button onclick="generateQuiz()">✨ צור מבחן</button>

<div id="quizPreview"></div>

<div id="shareSection" class="share-section hidden">
<h3>שתף את המבחן</h3>
<p>העבר את הקישור הזה למשתתפים:</p>
<div class="share-link">
<input type="text" id="shareLink" readonly />
<button onclick="copyShareLink()">📋 העתק</button>
<button onclick="sendByEmail()">📧 שלח במייל</button>
</div>
<p style="margin-top: 15px; color: #666; font-size: 0.9em;">
💡 המשתתפים יצטרכו להזין מספר טלפון ויקבלו את התוצאות ב-SMS
</p>
</div>
</div>

<div id="takeSection" class="card">
<h2>בצע מבחן</h2>

<div id="quizCodeInput">
<label>הזן קוד מבחן</label>
<input type="text" id="quizCode" placeholder="הזן את קוד המבחן שקיבלת" />
<button onclick="loadQuiz()">📥 טען מבחן</button>
</div>

<div id="phoneInput" class="phone-input-section hidden">
<h3>נדרש מספר טלפון לקבלת התוצאות</h3>
<p>הזן את מספר הטלפון שלך כדי לקבל את הציון וניתוח המבחן ב-SMS</p>
<input type="tel" id="phoneNumber" placeholder="05X-XXX-XXXX" />
<button onclick="startQuiz()">▶️ התחל מבחן</button>
</div>

<div id="quizContent" class="hidden"></div>

<div id="resultsSection" class="hidden">
<div class="result" id="scoreDisplay"></div>
<div class="analysis" id="analysisSection"></div>
<p style="text-align: center; margin-top: 20px; color: #666;">
📱 הציון נשלח ב-SMS למספר הטלפון שהזנת<br>
📧 ניתוח מפורט של כל התשובות נשלח במייל
</p>
</div>
</div>
</div>

<script>
let currentMode = 'create';
let currentQuiz = [];
let quizId = '';
let userPhone = '';

function switchMode(mode) {
currentMode = mode;
document.querySelectorAll('.mode-btn').forEach(btn => btn.classList.remove('active'));
event.target.classList.add('active');

document.getElementById('createSection').classList.remove('active');
document.getElementById('takeSection').classList.remove('active');

if (mode === 'create') {
document.getElementById('createSection').classList.add('active');
} else {
document.getElementById('takeSection').classList.add('active');
}
}

function selectOption(option) {
document.getElementById('welcomeScreen').classList.add('hidden');
if (option === 'create') {
document.getElementById('createSection').classList.add('active');
} else {
document.getElementById('takeSection').classList.add('active');
}
}

function cleanText(t) {
return t.replace(/\r\n/g, ' ').replace(/\s+/g, ' ').trim();
}

function splitSentences(t) {
return t.split(/(?<=[.!?\n])\s+/).filter(s => s.length > 10);
}

function extractKeywords(t) {
const STOP = new Set(['ו', 'ה', 'עם', 'על', 'של', 'את', 'זה', 'זו', 'או', 'אם', 'כי', 'אל', 'גם', 'כל', 'לא', 'מה', 'אך', 'רק', 'יש', 'היה', 'היא', 'הוא', 'אני']);
const freq = {};
Array.from((t || '').matchAll(/\p{L}+/gu)).forEach(m => {
const lw = m[0].toLowerCase();
if (STOP.has(lw) || lw.length < 3) return;
freq[lw] = (freq[lw] || 0) + 1;
});
return Object.keys(freq).sort((a, b) => freq[b] - freq[a]).slice(0, 40);
}

function randomPick(arr) {
return arr[Math.floor(Math.random() * arr.length)];
}

function shuffle(a) {
for (let i = a.length - 1; i > 0; i--) {
const j = Math.floor(Math.random() * (i + 1));
[a[i], a[j]] = [a[j], a[i]];
}
}

function escapeRegExp(s) {
return s.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
}

function generateQuiz() {
const text = cleanText(document.getElementById('textInput').value);
const count = Number(document.getElementById('numQuestions').value);
const type = document.getElementById('typeSelect').value;

if (!text) {
alert('נא להזין טקסט');
return;
}

const sents = splitSentences(text);
const kws = extractKeywords(text);

if (sents.length === 0 || kws.length === 0) {
alert('הטקסט קצר מדי או לא מכיל מספיק תוכן');
return;
}

const quiz = [];
const usedSentences = new Set();

for (let i = 0; i < count; i++) {
const kw = randomPick(kws);
const availableSents = sents.filter(s => 
s.toLowerCase().includes(kw.toLowerCase()) && !usedSentences.has(s)
);
const sent = availableSents.length > 0 ? randomPick(availableSents) : randomPick(sents);
usedSentences.add(sent);

const qType = type === 'mixed' ? randomPick(['mc', 'tf', 'blank']) : type;

if (qType === 'mc') {
const opts = [kw];
const otherKws = kws.filter(k => k !== kw);
while (opts.length < 4 && otherKws.length > 0) {
const opt = randomPick(otherKws);
if (!opts.includes(opt)) opts.push(opt);
}
shuffle(opts);
quiz.push({
type: 'mc',
question: sent.replace(new RegExp(escapeRegExp(kw), 'gi'), '_____'),
options: opts,
answer: kw
});
} else if (qType === 'tf') {
const wrong = randomPick(kws.filter(k => k !== kw)) || 'משהו אחר';
const altered = sent.replace(new RegExp(escapeRegExp(kw), 'gi'), wrong);
quiz.push({
type: 'tf',
question: altered,
answer: altered === sent ? 'נכון' : 'לא נכון'
});
} else if (qType === 'blank') {
quiz.push({
type: 'blank',
question: sent.replace(new RegExp(escapeRegExp(kw), 'gi'), '_____'),
answer: kw
});
}
}

currentQuiz = quiz;
quizId = 'QUIZ_' + Math.random().toString(36).substr(2, 9).toUpperCase();

displayQuizPreview(quiz);
showShareSection();
}

function displayQuizPreview(quiz) {
const container = document.getElementById('quizPreview');
let html = `<h3 style="color: #667eea; margin-top: 30px;">תצוגה מקדימה (${quiz.length} שאלות)</h3>`;

quiz.slice(0, 3).forEach((q, i) => {
const typeLabel = q.type === 'mc' ? 'רב ברירה' : q.type === 'tf' ? 'נכון/לא נכון' : 'מילוי חסר';
html += `<div class="quiz-question">
<span class="type-badge type-${q.type}">${typeLabel}</span>
<h3>${i + 1}. ${q.question}</h3>
</div>`;
});

if (quiz.length > 3) {
html += `<p style="text-align: center; color: #666;">ועוד ${quiz.length - 3} שאלות נוספות...</p>`;
}

container.innerHTML = html;
}

function showShareSection() {
const section = document.getElementById('shareSection');
const link = document.getElementById('shareLink');
const shareUrl = window.location.href.split('?')[0] + '?quiz=' + quizId;
link.value = shareUrl;
section.classList.remove('hidden');
}

function copyShareLink() {
const link = document.getElementById('shareLink');
link.select();
document.execCommand('copy');
alert('הקישור הועתק ללוח! 📋');
}

function sendByEmail() {
const link = document.getElementById('shareLink').value;
const subject = encodeURIComponent('מבחן חדש מחכה לך!');
const body = encodeURIComponent(`היי,\n\nנשלח אליך מבחן חדש.\n\nפתח את הקישור הבא כדי להתחיל:\n${link}\n\nבהצלחה!`);
window.location.href = `mailto:?subject=${subject}&body=${body}`;
}

function loadQuiz() {
const code = document.getElementById('quizCode').value.trim();
if (!code) {
alert('נא להזין קוד מבחן');
return;
}

document.getElementById('quizCodeInput').classList.add('hidden');
document.getElementById('phoneInput').classList.remove('hidden');
}

function startQuiz() {
const phone = document.getElementById('phoneNumber').value.trim();
if (!phone || phone.length < 9) {
alert('נא להזין מספר טלפון תקין');
return;
}

userPhone = phone;
document.getElementById('phoneInput').classList.add('hidden');
document.getElementById('quizContent').classList.remove('hidden');
displayQuizForTaking();
}

function displayQuizForTaking() {
const container = document.getElementById('quizContent');
let html = '<h3 style="color: #667eea; margin-bottom: 20px;">ענה על השאלות הבאות:</h3>';

currentQuiz.forEach((q, i) => {
const typeLabel = q.type === 'mc' ? 'רב ברירה' : q.type === 'tf' ? 'נכון/לא נכון' : 'מילוי חסר';
html += `<div class="quiz-question">
<span class="type-badge type-${q.type}">${typeLabel}</span>
<h3>${i + 1}. ${q.question}</h3>`;

if (q.type === 'mc') {
html += '<div class="options">';
q.options.forEach((opt, j) => {
html += `<label><input type="radio" name="q${i}" value="${opt}">${opt}</label>`;
});
html += '</div>';
} else if (q.type === 'tf') {
html += `<div class="options">
<label><input type="radio" name="q${i}" value="נכון">נכון</label>
<label><input type="radio" name="q${i}" value="לא נכון">לא נכון</label>
</div>`;
} else {
html += `<input type="text" class="answer-input" id="answer${i}" placeholder="הזן תשובה...">`;
}

html += '</div>';
});

html += '<button onclick="submitQuiz()">✅ סיים והגש מבחן</button>';
container.innerHTML = html;
}

function submitQuiz() {
currentQuiz.forEach((q, i) => {
if (q.type === 'mc' || q.type === 'tf') {
const selected = document.querySelector(`input[name="q${i}"]:checked`);
q.userAnswer = selected ? selected.value : '';
} else {
q.userAnswer = document.getElementById(`answer${i}`).value;
}
});

let score = 0;
let correct = [];
let incorrect = [];

currentQuiz.forEach((q, i) => {
const given = (q.userAnswer || '').toLowerCase().trim();
const ans = (q.answer || '').toLowerCase().trim();
if (given === ans) {
score++;
correct.push(i + 1);
} else {
incorrect.push({num: i + 1, question: q.question, correct: q.answer, given: q.userAnswer || 'לא נענה'});
}
});

showResults(score, correct, incorrect);
sendSMS(score, currentQuiz.length);
}

function showResults(score, correct, incorrect) {
document.getElementById('quizContent').classList.add('hidden');
document.getElementById('resultsSection').classList.remove('hidden');

const percent = Math.round((score / currentQuiz.length) * 100);
let className = 'poor';
if (percent >= 80) className = 'good';
else if (percent >= 60) className = 'medium';

const scoreDiv = document.getElementById('scoreDisplay');
scoreDiv.className = 'result ' + className;
scoreDiv.innerHTML = `
<div style="font-size: 2em;">🎯</div>
<div>ציון: ${score} מתוך ${currentQuiz.length}</div>
<div style="font-size: 1.5em; margin-top: 10px;">${percent}%</div>
`;

const analysisDiv = document.getElementById('analysisSection');
let analysisHtml = '<h3>ניתוח מפורט של התשובות</h3>';
analysisHtml += `<div class="analysis-item">
<strong>✅ תשובות נכונות:</strong> ${correct.length} (שאלות: ${correct.join(', ') || 'אין'})
</div>`;

if (incorrect.length > 0) {
analysisHtml += '<div class="analysis-item"><strong>❌ תשובות שגויות:</strong>';
incorrect.forEach(item => {
const q = currentQuiz[item.num - 1];
analysisHtml += `<div style="margin: 10px 0; padding: 10px; background: #fff; border-radius: 5px;">
<div><strong>שאלה ${item.num}:</strong> ${item.question}</div>`;

if (q.type === 'mc' && q.options) {
analysisHtml += '<div style="margin-top: 10px;"><strong>כל האפשרויות:</strong><ul style="margin: 5px 0;">';
q.options.forEach(opt => {
const isCorrect = opt.toLowerCase() === q.answer.toLowerCase();
const isUserChoice = opt.toLowerCase() === (item.given || '').toLowerCase();
let style = '';
let icon = '';
if (isCorrect) {
style = 'color: #2e7d32; font-weight: bold;';
icon = '✓ ';
}
if (isUserChoice && !isCorrect) {
style = 'color: #c62828;';
icon = '✗ ';
}
analysisHtml += `<li style="${style}">${icon}${opt}</li>`;
});
analysisHtml += '</ul></div>';
} else {
analysisHtml += `<div style="color: #c62828; margin-top: 5px;">התשובה שלך: ${item.given}</div>
<div style="color: #2e7d32;">התשובה הנכונה: ${item.correct}</div>`;
}
analysisHtml += '</div>';
});
analysisHtml += '</div>';
}

analysisDiv.innerHTML = analysisHtml;
}

function sendSMS(score, total) {
console.log(`שליחת SMS למספר: ${userPhone}`);
console.log(`תוכן ההודעה: ציון המבחן שלך: ${score}/${total} (${Math.round((score/total)*100)}%)`);
alert(`📱 SMS נשלח למספר ${userPhone} עם הציון!`);
sendEmailWithResults(score, total);
}

function sendEmailWithResults(score, total) {
const percent = Math.round((score / total) * 100);
let emailBody = `תוצאות המבחן שלך\n\n`;
emailBody += `ציון כללי: ${score} מתוך ${total} (${percent}%)\n\n`;
emailBody += `ניתוח מפורט:\n\n`;

currentQuiz.forEach((q, i) => {
const given = (q.userAnswer || '').toLowerCase().trim();
const ans = (q.answer || '').toLowerCase().trim();
const isCorrect = given === ans;

emailBody += `שאלה ${i + 1}: ${q.question}\n`;

if (q.type === 'mc' && q.options) {
emailBody += `אפשרויות:\n`;
q.options.forEach(opt => {
const optLower = opt.toLowerCase();
const isAnswer = optLower === ans;
const isUserChoice = optLower === given;
let prefix = '  ';
if (isAnswer) prefix = '✓ [תשובה נכונה] ';
if (isUserChoice && !isAnswer) prefix = '✗ [בחרת] ';
emailBody += `${prefix}${opt}\n`;
});
} else {
emailBody += `התשובה שלך: ${q.userAnswer || 'לא נענה'}\n`;
emailBody += `התשובה הנכונה: ${q.answer}\n`;
}
emailBody += `סטטוס: ${isCorrect ? '✓ נכון' : '✗ שגוי'}\n\n`;
});

emailBody += `\nמספר הטלפון שהוזן: ${userPhone}`;

const subject = encodeURIComponent(`תוצאות המבחן שלך - ${percent}%`);
const body = encodeURIComponent(emailBody);

const mailtoLink = `mailto:?subject=${subject}&body=${body}`;
window.open(mailtoLink, '_blank');
alert('📧 נפתח חלון שליחת מייל עם התוצאות המפורטות!');
}

document.getElementById('createSection').classList.add('active');

const urlParams = new URLSearchParams(window.location.search);
if (urlParams.has('quiz')) {
switchMode('take');
document.getElementById('quizCode').value = urlParams.get('quiz');
}
</script>
</body>
</html>
