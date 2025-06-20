<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>So‘zlarni o‘qib beruvchi</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      background: #f0f4f8;
    }
    h1 {
      text-align: center;
      color: #333;
    }
    .note {
      text-align: center;
      font-size: 14px;
      color: #555;
      margin-bottom: 20px;
    }
    .word {
  background: linear-gradient(135deg, #f12711, #f5af19);
  padding: 2px; /* 🔸 Ramka qalinligi */
  border-radius: 12px;
  margin: 10px 0;
  box-shadow: 0 4px 10px rgba(0,0,0,0.15);
}
    
    .number {
      font-weight: bold;
      font-size: 20px;
      color: #007acc;
      min-width: 30px;
      cursor: pointer;
    }
    .english {
      font-weight: bold;
      font-size: 18px;
    }
    .uzbek {
      font-size: 14px;
      color: #555;
    }
    body{
   background: linear-gradient(to right, #f12711, #f5af19);

    }
  </style>
</head>
<body>

<h1>Vocabulary Speaker</h1>
<div class="note">Raqamga bosib yoki klaviaturadan 1–9, 0, q–u tugmalarini bosib eshitishingiz mumkin</div>

<!-- Har bir raqamga onclick qo‘shildi -->
<div class="word"><div class="number" onclick="speakBoth('Employ', 'Ishga olmoq')">1</div><div><div class="english">Employ</div><div class="uzbek">Ishga olmoq</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Recruit', 'Yollamoq')">2</div><div><div class="english">Recruit</div><div class="uzbek">Yollamoq</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Deal with', 'Shug‘ullanmoq')">3</div><div><div class="english">Deal with</div><div class="uzbek">Shug‘ullanmoq</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Attend', 'Qatnashmoq')">4</div><div><div class="english">Attend</div><div class="uzbek">Qatnashmoq</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Employer', 'Ish beruvchi')">5</div><div><div class="english">Employer</div><div class="uzbek">Ish beruvchi</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Employee', 'Xodim')">6</div><div><div class="english">Employee</div><div class="uzbek">Xodim</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Enquiry', 'So‘rov')">7</div><div><div class="english">Enquiry</div><div class="uzbek">So‘rov</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Entertain', 'Ko‘ngil ochmoq')">8</div><div><div class="english">Entertain</div><div class="uzbek">Ko‘ngil ochmoq</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Challenging', 'Qiyin lekin qiziqarli')">9</div><div><div class="english">Challenging</div><div class="uzbek">Qiyin lekin qiziqarli</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Campaign', 'Kampaniya')">0</div><div><div class="english">Campaign</div><div class="uzbek">Kampaniya</div></div></div>

<div class="word"><div class="number" onclick="speakBoth('Necessary', 'Zarur')">Q</div><div><div class="english">Necessary</div><div class="uzbek">Zarur</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Reveal', 'Fosh qilmoq')">W</div><div><div class="english">Reveal</div><div class="uzbek">Fosh qilmoq</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Currently', 'Hozirda')">E</div><div><div class="english">Currently</div><div class="uzbek">Hozirda</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Make a good impression', 'Yaxshi taassurot')">R</div><div><div class="english">Make a good impression</div><div class="uzbek">Yaxshi taassurot</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Sensible', 'Aqlga to‘g‘ri')">T</div><div><div class="english">Sensible</div><div class="uzbek">Aqlga to‘g‘ri</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Make eye contact', 'Ko‘z bilan qaramoq')">Y</div><div><div class="english">Make eye contact</div><div class="uzbek">Ko‘z bilan qaramoq</div></div></div>
<div class="word"><div class="number" onclick="speakBoth('Sudden', 'To‘satdan')">U</div><div><div class="english">Sudden</div><div class="uzbek">To‘satdan</div></div></div>

<script>
  const wordMap = {
    '1': ['Employ', 'Ishga olmoq'],
    '2': ['Recruit', 'Yollamoq'],
    '3': ['Deal with', 'Shug‘ullanmoq'],
    '4': ['Attend', 'Qatnashmoq'],
    '5': ['Employer', 'Ish beruvchi'],
    '6': ['Employee', 'Xodim'],
    '7': ['Enquiry', 'So‘rov'],
    '8': ['Entertain', 'Ko‘ngil ochmoq'],
    '9': ['Challenging', 'Qiyin lekin qiziqarli'],
    '0': ['Campaign', 'Kampaniya'],
    'q': ['Necessary', 'Zarur'],
    'w': ['Reveal', 'Fosh qilmoq'],
    'e': ['Currently', 'Hozirda'],
    'r': ['Make a good impression', 'Yaxshi taassurot'],
    't': ['Sensible', 'Aqlga to‘g‘ri'],
    'y': ['Make eye contact', 'Ko‘z bilan qaramoq'],
    'u': ['Sudden', 'To‘satdan']
  };

  document.addEventListener('keydown', (event) => {
    const key = event.key.toLowerCase();
    if (wordMap[key]) {
      const [en, uz] = wordMap[key];
      speakBoth(en, uz);
    }
  });

  function speak(text) {
    const msg = new SpeechSynthesisUtterance(text);
    msg.lang = 'en-US';
    window.speechSynthesis.speak(msg);
  }

  function speakUzbek(text) {
    const msg = new SpeechSynthesisUtterance(text);
    msg.lang = 'uz-UZ'; // yoki 'ru-RU'
    window.speechSynthesis.speak(msg);
  }

  function speakBoth(en, uz) {
    speak(en);
    setTimeout(() => speakUzbek(uz), 1500);
  }
  function speakUzbek(text) {
  const msg = new SpeechSynthesisUtterance(text);
  msg.lang = 'uz-UZ'; // yoki 'ru-RU' agar uzbekcha yo‘q bo‘lsa
  msg.rate = 0.7; // 🔹 Ovoz tezligi 0.7x qilindi
  window.speechSynthesis.speak(msg);
}

</script>

</body>
</html>
