<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Кто ты из «Тайной истории» Донны Тартт?</title>
<style>
  :root {
    --bg: #1a1614;
    --card: #241f1c;
    --accent: #b8925a;
    --accent-soft: #d4b483;
    --text: #e8e0d5;
    --muted: #9a8f80;
    --border: #3a322c;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: Georgia, 'Times New Roman', serif;
    background: var(--bg);
    color: var(--text);
    line-height: 1.6;
    min-height: 100vh;
    padding: 40px 20px;
    background-image:
      radial-gradient(circle at 20% 10%, rgba(184,146,90,0.08), transparent 50%),
      radial-gradient(circle at 80% 90%, rgba(184,146,90,0.06), transparent 50%);
  }

  .container {
    max-width: 760px;
    margin: 0 auto;
    background: var(--card);
    border: 1px solid var(--border);
    padding: 50px 45px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.5);
  }

  h1 {
    font-size: 32px;
    font-weight: normal;
    letter-spacing: 0.5px;
    color: var(--accent-soft);
    text-align: center;
    margin-bottom: 12px;
  }

  .subtitle {
    text-align: center;
    color: var(--muted);
    font-style: italic;
    font-size: 15px;
    margin-bottom: 40px;
  }

  .intro {
    font-size: 16px;
    margin-bottom: 30px;
    color: var(--text);
  }

  .scale-hint {
    background: rgba(184,146,90,0.08);
    border-left: 3px solid var(--accent);
    padding: 16px 20px;
    margin-bottom: 35px;
    font-size: 14px;
    color: var(--muted);
  }

  .scale-hint strong { color: var(--accent-soft); font-weight: normal; }

  .question {
    padding: 20px 0;
    border-bottom: 1px solid var(--border);
  }

  .question:last-of-type { border-bottom: none; }

  .q-text {
    font-size: 16px;
    margin-bottom: 14px;
    display: flex;
    gap: 10px;
  }

  .q-num {
    color: var(--accent);
    min-width: 28px;
    font-variant-numeric: tabular-nums;
  }

  .options {
    display: flex;
    gap: 8px;
    padding-left: 38px;
    flex-wrap: wrap;
  }

  .options label {
    flex: 1;
    min-width: 60px;
    text-align: center;
    cursor: pointer;
    padding: 8px 6px;
    border: 1px solid var(--border);
    border-radius: 3px;
    font-size: 13px;
    color: var(--muted);
    transition: all 0.2s;
    user-select: none;
  }

  .options input { display: none; }

  .options label:hover {
    border-color: var(--accent);
    color: var(--accent-soft);
  }

  /* Подсветка выбранного варианта — через класс .selected, который ставит JS */
  .options label.selected {
    background: var(--accent);
    color: var(--bg);
    border-color: var(--accent);
  }

  .btn {
    display: block;
    width: 100%;
    margin-top: 40px;
    padding: 16px;
    background: var(--accent);
    color: var(--bg);
    border: none;
    font-family: inherit;
    font-size: 17px;
    letter-spacing: 1px;
    cursor: pointer;
    transition: background 0.2s;
  }

  .btn:hover { background: var(--accent-soft); }

  .btn:disabled {
    background: var(--border);
    color: var(--muted);
    cursor: not-allowed;
  }

  .error {
    color: #c97070;
    text-align: center;
    margin-top: 20px;
    font-size: 14px;
    min-height: 20px;
  }

  /* Результат */
  .result { display: none; text-align: center; }

  .result h2 {
    font-weight: normal;
    color: var(--accent-soft);
    font-size: 15px;
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 20px;
  }

  .result-name {
    font-size: 40px;
    color: var(--accent);
    margin-bottom: 8px;
    font-style: italic;
  }

  .result-desc {
    text-align: left;
    margin-top: 30px;
    font-size: 16px;
    color: var(--text);
  }

  .scores {
    margin-top: 35px;
    text-align: left;
    border-top: 1px solid var(--border);
    padding-top: 25px;
  }

  .scores h3 {
    font-size: 14px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 18px;
    font-weight: normal;
  }

  .score-row {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 10px;
    font-size: 14px;
  }

  .score-name { width: 130px; color: var(--muted); }

  .score-bar {
    flex: 1;
    height: 6px;
    background: var(--border);
    border-radius: 3px;
    overflow: hidden;
  }

  .score-fill {
    height: 100%;
    width: 0;
    background: var(--accent);
    border-radius: 3px;
    transition: width 0.8s ease;
  }

  .score-val {
    width: 40px;
    text-align: right;
    color: var(--accent-soft);
    font-variant-numeric: tabular-nums;
  }

  .restart {
    margin-top: 35px;
    background: transparent;
    border: 1px solid var(--accent);
    color: var(--accent);
  }

  .restart:hover {
    background: var(--accent);
    color: var(--bg);
  }

  @media (max-width: 600px) {
    .container { padding: 30px 22px; }
    h1 { font-size: 24px; }
    .result-name { font-size: 30px; }
    .options { padding-left: 0; }
    .options label { min-width: 50px; font-size: 12px; padding: 7px 3px; }
  }
</style>
</head>
<body>
<div class="container">

  <!-- ЭКРАН 1: Приветствие -->
  <div id="screen-start">
    <h1>Кто ты из «Тайной истории»?</h1>
    <p class="subtitle">Психологический тест по роману Донны Тартт</p>
    <p class="intro">
      Оцените, насколько каждое утверждение про вас. В конце вы узнаете,
      на кого из героев вы похожи больше всего.
    </p>
    <div class="scale-hint">
      <strong>1</strong> — совсем не про меня &nbsp;·&nbsp;
      <strong>2</strong> — скорее нет &nbsp;·&nbsp;
      <strong>3</strong> — иногда / отчасти &nbsp;·&nbsp;
      <strong>4</strong> — скорее да &nbsp;·&nbsp;
      <strong>5</strong> — очень про меня
    </div>
    <button class="btn" onclick="startTest()">Начать тест</button>
  </div>

  <!-- ЭКРАН 2: Вопросы -->
  <div id="screen-quiz" style="display:none;">
    <h1>Кто ты из «Тайной истории»?</h1>
    <p class="subtitle">Донна Тартт · 35 утверждений</p>
    <form id="quizForm"></form>
    <div class="error" id="errorMsg"></div>
    <button class="btn" id="submitBtn" onclick="submitQuiz()">Узнать результат</button>
  </div>

  <!-- ЭКРАН 3: Результат -->
  <div id="screen-result" class="result">
    <h2>Ваш архетип</h2>
    <div class="result-name" id="resultName"></div>
    <div class="result-desc" id="resultDesc"></div>

    <div class="scores">
      <h3>Ваши баллы</h3>
      <div id="scoreList"></div>
    </div>

    <button class="btn restart" onclick="restart()">Пройти заново</button>
  </div>

</div>

<script>
/* ==================== ДАННЫЕ ==================== */

const questions = [
  "Я часто чувствую себя чужим в компании, к которой хочу принадлежать.",
  "Я предпочитаю холодный расчёт и стратегию эмоциональным порывам.",
  "Я легко завожу разговор и умею быть в центре внимания.",
  "Я очень чувствителен к атмосфере, красоте и эстетике.",
  "Мои чувства и желания часто сильнее меня.",
  "Я произвожу впечатление спокойной и загадочной, хотя внутри много чувств.",
  "Я ценю интеллект, вкус и культурную изысканность выше обыденности.",
  "Я склонен идеализировать людей, которые кажутся мне уверенными и «избранными».",
  "Мне важно сохранять контроль над собой и ситуацией.",
  "Мне нужно, чтобы меня замечали, одобряли и любили.",
  "Я часто тревожусь и предпочёл бы избежать конфликта.",
  "Я склонен к ревности и собственничеству в близких отношениях.",
  "Я умею приспосабливаться к обстоятельствам, чтобы выжить.",
  "Я предпочитаю держать дистанцию и не пускать людей слишком близко.",
  "Я могу скрывать своё прошлое или происхождение, чтобы меня приняли.",
  "Я считаю, что цель может оправдывать средства, если речь о важном.",
  "Я люблю удовольствия, веселье и не люблю скуку и ограничения.",
  "Мне важно иметь рядом человека, который поддержит и успокоит.",
  "Я могу быть разрушительным для себя и других, когда мне плохо.",
  "Я не люблю показывать слабость и предпочитаю держать дистанцию.",
  "Я умею создавать вокруг себя атмосферу исключительности.",
  "В конфликте мне легче промолчать или подстроиться, чем открыто возразить.",
  "Я часто ощущаю внутреннее одиночество, даже среди близких.",
  "Я могу давить на людей, шутить колко или провоцировать, чтобы получить своё.",
  "Я могу скрывать свою настоящую сущность из страха осуждения.",
  "Я ищу сильные ощущения, чтобы заглушить внутреннюю боль.",
  "Я могу быть преданной, но не позволяю собой управлять.",
  "Я склонен закрывать глаза на неприятную реальность, если она разрушает красоту.",
  "Я наблюдаю за другими и мысленно примеряю их жизнь на себя.",
  "Я могу казаться спокойным, когда внутри всё сложно.",
  "В глубине души я боюсь, что без обаяния меня не будут ценить.",
  "Я ищу комфорт, изящество и эмоциональную безопасность.",
  "Мои настроение и поведение могут резко меняться.",
  "Я часто оказываюсь сильнее, чем обо мне думают.",
  "Люди часто видят во мне наставника или авторитет, даже если я этого не прошу."
];

const characters = [
  {
    key: "richard",
    name: "Ричард Пэйпен",
    questions: [1, 8, 15, 22, 29],
    desc: "Вы — наблюдатель и аутсайдер, который очень хочет принадлежать к «избранному» кругу. Вы чувствительны к атмосфере, умеете подстраиваться, но иногда идеализируете людей и избегаете прямой ответственности. Ваш ресурс — эмпатия, наблюдательность и способность видеть скрытые мотивы. Тень — пассивность, зависимость от чужого одобрения и моральная нерешительность."
  },
  {
    key: "henry",
    name: "Генри Уинтер",
    questions: [2, 9, 16, 23, 30],
    desc: "Вы — стратег, интеллектуал и стоик. Вы цените контроль, ясность и внутреннюю дисциплину, умеете сохранять спокойствие в кризисе. Ваш ресурс — воля, ум и способность видеть картину целиком. Тень — холодность, отстранённость, склонность оправдывать средства целью и одиночество даже среди близких."
  },
  {
    key: "bunny",
    name: "Банни Коркоран",
    questions: [3, 10, 17, 24, 31],
    desc: "Вы — социальный, яркий, гедонистичный человек. Вы легко заводите знакомства, любите внимание, юмор и удовольствия. Ваш ресурс — обаяние, живость и умение создавать настроение. Тень — зависимость от одобрения, инфантильность, манипулятивность и страх остаться незамеченным."
  },
  {
    key: "francis",
    name: "Фрэнсис Абернати",
    questions: [4, 11, 18, 25, 32],
    desc: "Вы — чувствительный эстет и тревожный наблюдатель. Вы цените красоту, комфорт и эмоциональную безопасность, но часто избегаете конфликтов и прячете свою настоящую сущность. Ваш ресурс — вкус, мягкость и глубокая эмоциональность. Тень — избегание, зависимость от поддержки и склонность закрывать глаза на проблемы."
  },
  {
    key: "charles",
    name: "Чарльз Маколей",
    questions: [5, 12, 19, 26, 33],
    desc: "Вы — импульсивный, страстный и эмоционально интенсивный человек. Чувства у вас часто сильнее разума, а в близких отношениях возможны ревность и собственничество. Ваш ресурс — страстность, честность в эмоциях и способность на сильную привязанность. Тень — нестабильность, склонность к саморазрушению и зависимостям."
  },
  {
    key: "camilla",
    name: "Камилла Маколей",
    questions: [6, 13, 20, 27, 34],
    desc: "Вы — загадочная, сдержанная и выживающая фигура. Вы умеете держать дистанцию, приспосабливаться и не показывать слабость. Ваш ресурс — стойкость, грация и внутренняя сила. Тень — эмоциональная закрытость, недоверие и трудность в том, чтобы позволить кому-то подойти слишком близко."
  },
  {
    key: "julian",
    name: "Джулиан Морроу",
    questions: [7, 14, 21, 28, 35],
    desc: "Вы — наставник-эстет, интеллектуальный авторитет и создатель атмосферы исключительности. Вы цените вкус, культуру и дистанцию, умеете вдохновлять, но не любите грязную реальность. Ваш ресурс — харизма, эрудиция и чувство формы. Тень — элитизм, отстранённость и склонность прятаться от последствий в красивых идеях."
  }
];

/* ==================== ЛОГИКА ==================== */

const MAX_PER_CHARACTER = 25; // 5 вопросов * 5 баллов
const answers = {};           // { questionNumber: value }

/* --- Экраны --- */
function showScreen(id) {
  ['screen-start', 'screen-quiz', 'screen-result'].forEach(s => {
    const el = document.getElementById(s);
    if (el) el.style.display = (s === id) ? 'block' : 'none';
  });
  window.scrollTo(0, 0);
}

/* --- Старт --- */
function startTest() {
  renderQuiz();
  showScreen('screen-quiz');
}

/* --- Рендер вопросов --- */
function renderQuiz() {
  const form = document.getElementById('quizForm');
  let html = '';

  questions.forEach((q, i) => {
    const num = i + 1;
    let opts = '';
    for (let v = 1; v <= 5; v++) {
      // data-атрибуты вместо inline onclick — надёжнее и безопаснее
      opts += `
        <label data-q="${num}" data-v="${v}">
          <input type="radio" name="q${num}" value="${v}">
          <span>${v}</span>
        </label>`;
    }
    html += `
      <div class="question">
        <div class="q-text"><span class="q-num">${num}.</span><span>${q}</span></div>
        <div class="options">${opts}</div>
      </div>`;
  });

  form.innerHTML = html;

  // Один делегированный обработчик на всю форму
  form.addEventListener('change', (e) => {
    const input = e.target;
    if (input && input.type === 'radio' && input.name.startsWith('q')) {
      const num = parseInt(input.name.slice(1), 10);
      answers[num] = parseInt(input.value, 10);

      // Подсветка выбранной опции
      const group = form.querySelectorAll(`label[data-q="${num}"]`);
      group.forEach(lbl => lbl.classList.remove('selected'));
      const chosenLabel = input.closest('label');
      if (chosenLabel) chosenLabel.classList.add('selected');

      // Сброс сообщения об ошибке
      const err = document.getElementById('errorMsg');
      if (err) err.textContent = '';
    }
  });
}

/* --- Отправка --- */
function submitQuiz() {
  const total = questions.length;
  const missing = [];
  for (let i = 1; i <= total; i++) {
    if (!answers[i]) missing.push(i);
  }

  if (missing.length > 0) {
    document.getElementById('errorMsg').textContent =
      `Пожалуйста, ответьте на все вопросы. Осталось: ${missing.length}.`;
    const el = document.querySelectorAll('.question')[missing[0] - 1];
    if (el) el.scrollIntoView({ behavior: 'smooth', block: 'center' });
    return;
  }

  // Подсчёт баллов
  const scores = characters.map(ch => {
    const sum = ch.questions.reduce((acc, qn) => acc + (answers[qn] || 0), 0);
    return { name: ch.name, desc: ch.desc, score: sum };
  });

  scores.sort((a, b) => b.score - a.score);
  showResult(scores);
}

/* --- Показ результата --- */
function showResult(scores) {
  const winner = scores[0];
  const runnerUp = scores[1];

  document.getElementById('resultName').textContent = winner.name;

  let descHtml = winner.desc;
  if (runnerUp && (winner.score - runnerUp.score) <= 3) {
    descHtml += `<br><br><em style="color:var(--muted)">Вы — смешанный тип: черты ${winner.name} и ${runnerUp.name} у вас выражены почти одинаково сильно.</em>`;
  }
  document.getElementById('resultDesc').innerHTML = descHtml;

  const list = document.getElementById('scoreList');
  list.innerHTML = scores.map(s => {
    const percent = Math.round((s.score / MAX_PER_CHARACTER) * 100);
    return `
      <div class="score-row">
        <div class="score-name">${s.name}</div>
        <div class="score-bar"><div class="score-fill" data-width="${percent}"></div></div>
        <div class="score-val">${s.score}/${MAX_PER_CHARACTER}</div>
      </div>`;
  }).join('');

  showScreen('screen-result');

  // Плавная анимация полосок: сначала 0, затем нужная ширина
  requestAnimationFrame(() => {
    list.querySelectorAll('.score-fill').forEach(el => {
      el.style.width = el.dataset.width + '%';
    });
  });
}

/* --- Рестарт --- */
function restart() {
  Object.keys(answers).forEach(k => delete answers[k]);
  const form = document.getElementById('quizForm');
  if (form) form.reset();
  document.getElementById('errorMsg').textContent = '';
  document.getElementById('scoreList').innerHTML = '';
  showScreen('screen-start');
}
</script>
</body>
</html>