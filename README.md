
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CES 211 Practice Test</title>
  <style>
    :root {
      --bg: #0f172a;
      --card-bg: #1e293b;
      --accent: #6366f1;
      --accent-hover: #4f46e5;
      --text: #f8fafc;
      --text-muted: #94a3b8;
      --correct: #22c55e;
      --correct-bg: rgba(34, 197, 94, 0.15);
      --wrong: #ef4444;
      --wrong-bg: rgba(239, 68, 68, 0.15);
      --border: #334155;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
    }

    body {
      background-color: var(--bg);
      color: var(--text);
      display: flex;
      justify-content: center;
      padding: 16px;
      min-height: 100vh;
    }

    .app-container {
      width: 100%;
      max-width: 650px;
      margin: 0 auto;
    }

    header {
      background-color: var(--card-bg);
      padding: 16px 20px;
      border-radius: 12px;
      margin-bottom: 16px;
      border: 1px solid var(--border);
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .title-area h1 {
      font-size: 1.1rem;
      color: #38bdf8;
    }

    .title-area p {
      font-size: 0.85rem;
      color: var(--text-muted);
    }

    .badge {
      background: var(--border);
      padding: 6px 12px;
      border-radius: 20px;
      font-size: 0.85rem;
      font-weight: 600;
    }

    .card {
      background-color: var(--card-bg);
      padding: 24px;
      border-radius: 12px;
      border: 1px solid var(--border);
      box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.3);
    }

    .progress-bar-container {
      width: 100%;
      height: 6px;
      background: var(--border);
      border-radius: 3px;
      margin-bottom: 20px;
      overflow: hidden;
    }

    .progress-fill {
      height: 100%;
      background: var(--accent);
      width: 0%;
      transition: width 0.3s ease;
    }

    .question-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      color: var(--text-muted);
      font-size: 0.9rem;
      margin-bottom: 12px;
    }

    .question-text {
      font-size: 1.15rem;
      line-height: 1.5;
      font-weight: 500;
      margin-bottom: 24px;
    }

    .options-container {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-bottom: 24px;
    }

    .option-btn {
      background-color: transparent;
      border: 1px solid var(--border);
      color: var(--text);
      padding: 14px 16px;
      border-radius: 8px;
      text-align: left;
      font-size: 0.95rem;
      cursor: pointer;
      transition: all 0.2s ease;
      display: flex;
      align-items: flex-start;
      gap: 12px;
    }

    .option-btn:hover:not(:disabled) {
      background-color: var(--border);
    }

    .option-btn.correct {
      border-color: var(--correct);
      background-color: var(--correct-bg);
      color: #86efac;
    }

    .option-btn.wrong {
      border-color: var(--wrong);
      background-color: var(--wrong-bg);
      color: #fca5a5;
    }

    .feedback-box {
      padding: 16px;
      border-radius: 8px;
      margin-bottom: 20px;
      font-size: 0.9rem;
      line-height: 1.4;
      display: none;
    }

    .feedback-box.correct {
      display: block;
      background: var(--correct-bg);
      border: 1px solid var(--correct);
    }

    .feedback-box.wrong {
      display: block;
      background: var(--wrong-bg);
      border: 1px solid var(--wrong);
    }

    .nav-controls {
      display: flex;
      gap: 10px;
      margin-top: 10px;
    }

    .nav-btn {
      flex: 1;
      background-color: var(--accent);
      color: white;
      border: none;
      padding: 12px;
      border-radius: 8px;
      font-size: 0.95rem;
      font-weight: 600;
      cursor: pointer;
      transition: background 0.2s ease;
    }

    .nav-btn:hover:not(:disabled) {
      background-color: var(--accent-hover);
    }

    .nav-btn:disabled {
      background-color: var(--border);
      color: var(--text-muted);
      cursor: not-allowed;
    }

    .finish-early-btn {
      width: 100%;
      background-color: transparent;
      border: 1px solid var(--wrong);
      color: #fca5a5;
      padding: 10px;
      border-radius: 8px;
      font-size: 0.85rem;
      font-weight: 600;
      cursor: pointer;
      margin-top: 16px;
    }

    .finish-early-btn:hover {
      background-color: var(--wrong-bg);
    }

    .results-screen {
      text-align: center;
      padding: 20px 0;
    }

    .score-circle {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      border: 4px solid var(--accent);
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto 20px auto;
      font-size: 1.8rem;
      font-weight: 700;
    }

    .restart-btn {
      background-color: var(--accent);
      color: white;
      border: none;
      padding: 12px 24px;
      border-radius: 8px;
      font-size: 1rem;
      font-weight: 600;
      cursor: pointer;
      margin-top: 20px;
    }

    .hidden {
      display: none !important;
    }
  </style>
</head>
<body>

  <div class="app-container">
    <header>
      <div class="title-area">
        <h1>CES 211 Practice Test</h1>
        <p>Entrepreneurship & Innovation</p>
      </div>
      <div class="badge" id="scoreBadge">Score: 0</div>
    </header>

    <div class="card" id="quizCard">
      <div class="progress-bar-container">
        <div class="progress-fill" id="progressFill"></div>
      </div>

      <div class="question-header">
        <span id="qIndex">Question 1 of 100</span>
      </div>

      <div class="question-text" id="qText">Loading question...</div>

      <div class="options-container" id="optionsContainer"></div>

      <div class="feedback-box" id="feedbackBox"></div>

      <div class="nav-controls">
        <button class="nav-btn" id="prevBtn" disabled>Previous</button>
        <button class="nav-btn" id="nextBtn">Next</button>
      </div>

      <button class="finish-early-btn" id="finishEarlyBtn">Finish Quiz & See Score</button>
    </div>

    <div class="card hidden" id="resultCard">
      <div class="results-screen">
        <h2>Quiz Results</h2>
        <p style="color: var(--text-muted); margin-top: 6px; margin-bottom: 24px;" id="attemptSummary">Here is your performance summary:</p>
        
        <div class="score-circle" id="finalScore">0%</div>
        
        <p id="scoreDetails" style="font-size: 1.1rem; margin-bottom: 10px;"></p>
        <p id="gradeComment" style="color: var(--text-muted);"></p>

        <button class="restart-btn" id="restartBtn">Retake Quiz</button>
      </div>
    </div>
  </div>

  <script>
    const quizData = [
      { question: "One major objective of entrepreneurship education is to cultivate an ______ mindset.", options: ["Administrative", "Entrepreneurial", "Political", "Bureaucratic"], answer: 1 },
      { question: "Entrepreneurship education develops students' ability to recognize and ______ opportunities.", options: ["reject", "avoid", "seize", "postpone"], answer: 2 },
      { question: "A proactive, risk-taking and ______ approach to problem-solving is encouraged by entrepreneurship education.", options: ["traditional", "innovative", "passive", "conservative"], answer: 1 },
      { question: "Entrepreneurship education teaches the fundamentals of business planning, financial management and ______ acquisition.", options: ["resource", "political", "cultural", "social"], answer: 0 },
      { question: "Developing business models, prototyping and customer ______ are practical entrepreneurial skills.", options: ["rejection", "validation", "avoidance", "replacement"], answer: 1 },
      { question: "Entrepreneurship education prepares students to navigate the challenges and ______ of the entrepreneurial process.", options: ["certainties", "uncertainties", "profits", "policies"], answer: 1 },
      { question: "One learning outcome of entrepreneurship education is the ability to identify opportunities, take calculated risks and ______.", options: ["innovate", "speculate", "withdraw", "complain"], answer: 0 },
      { question: "Effective communication and ______ are important entrepreneurial learning outcomes.", options: ["isolation", "collaboration", "competition", "separation"], answer: 1 },
      { question: "Adaptability refers to the capacity to adjust to changing ______.", options: ["circumstances", "salaries", "positions", "accounts"], answer: 0 },
      { question: "The skill to generate innovative solutions to problems is known as ______.", options: ["creativity", "accounting", "delegation", "negotiation"], answer: 0 },
      { question: "The ability to prioritize tasks, set goals and manage time efficiently is called ______ management.", options: ["financial", "time", "human", "resource"], answer: 1 },
      { question: "The commitment to stay curious and continuously expand one's knowledge is known as ______ learning.", options: ["traditional", "continuous", "temporary", "seasonal"], answer: 1 },
      { question: "Entrepreneurship education can reduce dependence on traditional ______-seeking.", options: ["business", "employment", "job", "market"], answer: 2 },
      { question: "Entrepreneurship involves creating new business ideas and transforming them into tangible goods and ______.", options: ["capital", "services", "theories", "policies"], answer: 1 },
      { question: "According to Schumpeter, entrepreneurship involves new combinations of ______.", options: ["employees", "resources", "governments", "customers"], answer: 1 },
      { question: "The success of entrepreneurship hinges largely on creativity and ______.", options: ["taxation", "innovation", "bureaucracy", "employment"], answer: 1 },
      { question: "Which of the following is a characteristic of entrepreneurship?", options: ["Risk-taking", "Risk avoidance", "Dependence", "Inactivity"], answer: 0 },
      { question: "Entrepreneurship involves transforming raw materials into finished products through ______ addition.", options: ["market", "value", "political", "social"], answer: 1 },
      { question: "Entrepreneurship is regarded as a ______-oriented activity.", options: ["result", "government", "family", "salary"], answer: 0 },
      { question: "One major objective of entrepreneurship is the creation of ______ opportunities.", options: ["employment", "political", "recreational", "foreign"], answer: 0 },
      { question: "Entrepreneurship contributes to ______ alleviation through employment creation.", options: ["poverty", "technology", "competition", "inflation"], answer: 0 },
      { question: "An entrepreneur is a generator of business ideas, organizer of resources and ______ of business.", options: ["critic", "manager", "customer", "employee"], answer: 1 },
      { question: "An entrepreneur must have confidence in himself or herself and believe in his or her ______.", options: ["competitors", "ideas", "employees", "customers"], answer: 1 },
      { question: "Which of the following is a characteristic of a good entrepreneur?", options: ["Pessimism", "Optimism", "Laziness", "Indecision"], answer: 1 },
      { question: "Intrapreneurship creates opportunities for ______ to exhibit entrepreneurial skills within an organization.", options: ["customers", "employees", "competitors", "suppliers"], answer: 1 },
      { question: "The psychological theory of entrepreneurship emphasizes personality traits, locus of control and the need for ______.", options: ["achievement", "employment", "taxation", "ownership"], answer: 0 },
      { question: "Entrepreneurship involves creating or obtaining ______ value.", options: ["economic", "political", "cultural", "personal"], answer: 0 },
      { question: "Entrepreneurs take the majority of the risks and reap the majority of the ______.", options: ["losses", "returns", "expenses", "taxes"], answer: 1 },
      { question: "Which of the following is a type of entrepreneurship?", options: ["Cultural entrepreneurship", "Administrative entrepreneurship", "Bureaucratic entrepreneurship", "Government entrepreneurship"], answer: 0 },
      { question: "A well-written ______ plan is an indicator of entrepreneurial success.", options: ["business", "political", "family", "academic"], answer: 0 },
      { question: "Market indicators include business-to-business and business-to-______ models.", options: ["government", "customer", "employee", "supplier"], answer: 1 },
      { question: "Which of the following is an industry indicator?", options: ["High capital intensity", "Low customer demand", "Poor management", "High employee turnover"], answer: 0 },
      { question: "The first stage of innovative thinking is ______.", options: ["evaluation", "preparation", "commercialization", "implementation"], answer: 1 },
      { question: "Critical thinking involves questioning, analysing, interpreting and ______ information.", options: ["ignoring", "evaluating", "destroying", "selling"], answer: 1 },
      { question: "The first step in critical thinking is to identify the ______.", options: ["profit", "problem", "customer", "product"], answer: 1 },
      { question: "The ability to look at a problem from different perspectives is a basic ______-thinking skill.", options: ["critical", "financial", "accounting", "managerial"], answer: 0 },
      { question: "Reflective thinking involves considering the larger context, meaning and ______ of an experience.", options: ["implications", "profits", "salaries", "prices"], answer: 0 },
      { question: "Creative thinking is the ability to come up with unique ______ solutions.", options: ["original", "traditional", "borrowed", "expensive"], answer: 0 },
      { question: "How many major types of innovation are identified in the material?", options: ["Two", "Three", "Four", "Five"], answer: 2 },
      { question: "Which type of innovation involves gradual and continuous improvements to an existing product or service?", options: ["Radical", "Disruptive", "Incremental", "Sustaining"], answer: 2 },
      { question: "The word entrepreneurship is derived from the French word ______.", options: ["Entrepreneur", "Entreprendre", "Enterprise", "Entreprise"], answer: 1 },
      { question: "The word Entreprendre means ______.", options: ["business", "pledge", "wealth", "innovation"], answer: 1 },
      { question: "Cultural entrepreneurship begins with a cultural ______ and leads to a cultural business.", options: ["product", "idea", "market", "profit"], answer: 1 },
      { question: "Cultural entrepreneurship can contribute to job and ______ creation.", options: ["wealth", "political", "academic", "military"], answer: 0 },
      { question: "NEPZA stands for Nigerian Export Processing Zones ______.", options: ["Administration", "Authority", "Association", "Agency"], answer: 1 },
      { question: "NIPC stands for Nigerian Investment Promotion ______.", options: ["Commission", "Council", "Corporation", "Committee"], answer: 0 },
      { question: "NEPC stands for Nigerian Export Promotion ______.", options: ["Commission", "Council", "Corporation", "Committee"], answer: 1 },
      { question: "NEPC encourages the growth of ______-oil exports from Nigeria.", options: ["high", "non", "crude", "foreign"], answer: 1 },
      { question: "ANE stands for Association of Nigerian ______.", options: ["Entrepreneurs", "Exporters", "Employers", "Educators"], answer: 1 },
      { question: "NEXIM Bank was established to provide easy access to ______ financing.", options: ["export", "personal", "political", "agricultural"], answer: 0 },
      { question: "Entrepreneurship support institutions act as catalysts for ______ businesses.", options: ["large", "small", "foreign", "government"], answer: 1 },
      { question: "Mentoring programmes match experienced entrepreneurs with ______ entrepreneurs.", options: ["old", "young", "foreign", "retired"], answer: 1 },
      { question: "An unstable political climate may discourage business because investors fear the safety and ______ of their investments.", options: ["security", "profit", "marketing", "expansion"], answer: 0 },
      { question: "Opportunity identification is the ability to identify a good idea and transform it into a business ______.", options: ["policy", "concept", "regulation", "salary"], answer: 1 },
      { question: "A good business concept should add value and generate ______.", options: ["revenue", "taxes", "debt", "salaries"], answer: 0 },
      { question: "Opportunity identification is an essential component of the ______ process.", options: ["accounting", "entrepreneurial", "political", "manufacturing"], answer: 1 },
      { question: "Entrepreneurs identify opportunities based on personal qualities, networks and ______ processes.", options: ["cognitive", "financial", "political", "accounting"], answer: 0 },
      { question: "Opportunity discovery involves being proactive in ______ chances.", options: ["avoiding", "seizing", "rejecting", "delaying"], answer: 1 },
      { question: "When choosing a business opportunity, an entrepreneur should examine his or her ______.", options: ["rivals", "family", "lecturers", "neighbours"], answer: 0 },
      { question: "The objective of brainstorming is to come up with many ______.", options: ["employees", "ideas", "products", "companies"], answer: 1 },
      { question: "During brainstorming, there should be no criticism, rewards or ______.", options: ["judgments", "ideas", "discussions", "participation"], answer: 0 },
      { question: "A focus group is guided by a ______.", options: ["manager", "moderator", "customer", "secretary"], answer: 1 },
      { question: "A typical focus group consists of approximately ______ to ______ recruited people.", options: ["2–4", "5–7", "8–14", "20–30"], answer: 2 },
      { question: "Which technique uses a graphical approach to turn an idea into a visual representation?", options: ["Brainwriting", "Mind mapping", "Focus grouping", "Interviewing"], answer: 1 },
      { question: "Persuading investors to invest in a groundbreaking concept is known as ______.", options: ["business planning", "idea pitching", "market research", "risk analysis"], answer: 1 },
      { question: "Identifying, generating and seizing new business prospects for a firm is known as ______.", options: ["business development", "business closure", "business taxation", "business auditing"], answer: 0 },
      { question: "A business plan outlines the company's objectives and ______ for achieving them.", options: ["strategies", "salaries", "employees", "competitors"], answer: 0 },
      { question: "The title page of a business plan contains the firm's name, address, logo and names of the ______.", options: ["customers", "founders", "competitors", "suppliers"], answer: 1 },
      { question: "The executive summary provides a quick description of the issue or ______.", options: ["proposition", "salary", "employee", "competitor"], answer: 0 },
      { question: "The mission statement guides the company's growth and ______.", options: ["direction", "taxation", "salary", "production"], answer: 0 },
      { question: "Market analysis involves competition analysis, marketing strategy, market research and sales ______.", options: ["expenses", "forecasts", "salaries", "taxes"], answer: 1 },
      { question: "Technical analysis outlines the results of the technical ______ study.", options: ["marketing", "feasibility", "accounting", "leadership"], answer: 1 },
      { question: "The simplest form of business ownership is ______.", options: ["partnership", "corporation", "sole proprietorship", "cooperative"], answer: 2 },
    { question: "In a sole proprietorship, there is only ______ owner.", options: ["one", "two", "three", "several"], answer: 0 },
      { question: "In a general partnership, partners share the company's gains and ______.", options: ["assets", "losses", "employees", "customers"], answer: 1 },
      { question: "Small Business Management refers to practices and strategies used in running a ______-scale enterprise.", options: ["large", "small", "multinational", "governmental"], answer: 1 },
      { question: "Small businesses commonly operate with limited ______.", options: ["resources", "customers", "markets", "technology"], answer: 0 },
      { question: "Family business involves family members in the ownership and ______ of the business.", options: ["management", "taxation", "marketing", "advertising"], answer: 0 },
      { question: "Leadership primarily involves influencing and ______ others to achieve common goals.", options: ["inspiring", "controlling", "punishing", "replacing"], answer: 0 },
      { question: "Management focuses on planning, organizing and ______ resources.", options: ["wasting", "controlling", "selling", "borrowing"], answer: 1 },
      { question: "Which leadership style inspires followers to exceed their self-interests for the good of the organization?", options: ["Autocratic", "Transformational", "Laissez-faire", "Transactional"], answer: 1 },
      { question: "Transactional leadership focuses on routine procedures and clear ______-term goals.", options: ["long", "short", "permanent", "indefinite"], answer: 1 },
      { question: "Which leadership style prioritizes the needs of the team?", options: ["Servant", "Autocratic", "Transactional", "Bureaucratic"], answer: 0 },
      { question: "Autocratic leadership centralizes ______.", options: ["communication", "authority", "employment", "innovation"], answer: 1 },
      { question: "Democratic leadership encourages team participation in ______-making.", options: ["profit", "decision", "market", "resource"], answer: 1 },
      { question: "Laissez-faire leadership gives followers freedom and ______.", options: ["punishment", "autonomy", "restrictions", "supervision"], answer: 1 },
      { question: "Situational leaders adjust their leadership style according to the current ______.", options: ["situation", "salary", "company", "customer"], answer: 0 },
      { question: "Henri Fayol identified planning, organizing, staffing, leading and ______ as management functions.", options: ["financing", "controlling", "marketing", "selling"], answer: 1 },
      { question: "The management function concerned with setting goals and determining the best course of action is ______.", options: ["planning", "staffing", "controlling", "leading"], answer: 0 },
      { question: "Staffing involves getting the ______ person for the ______ job.", options: ["available; difficult", "right; right", "senior; junior", "trained; wrong"], answer: 1 },
      { question: "Negotiation is critical in defining the terms of agreements and ______.", options: ["contracts", "salaries", "products", "advertisements"], answer: 0 },
      { question: "Principled negotiation was popularized by Fisher, Ury and ______.", options: ["Fayol", "Patton", "Drucker", "Schumpeter"], answer: 1 },
      { question: "Principled negotiation emphasizes separating people from the ______.", options: ["customer", "problem", "company", "contract"], answer: 1 },
      { question: "Distributive bargaining is also known as ______-sum negotiation.", options: ["positive", "zero", "double", "equal"], answer: 1 },
      { question: "Integrative negotiation seeks mutually ______ solutions.", options: ["harmful", "beneficial", "expensive", "competitive"], answer: 1 },
      { question: "BATNA means Best Alternative to a ______ Negotiated Agreement.", options: ["Business", "Best", "Bad", "Basic"], answer: 1 },
      { question: "The originator of a message in the communication process is the ______.", options: ["receiver", "sender", "channel", "decoder"], answer: 1 },
      { question: "The person who receives a message is the ______.", options: ["sender", "receiver", "channel", "encoder"], answer: 1 },
      { question: "The response given by the receiver after receiving and understanding a message is called ______.", options: ["feedback", "encoding", "noise", "channel"], answer: 0 },
      { question: "The five basic elements of communication include sender, receiver, message, feedback and ______.", options: ["channel", "profit", "negotiation", "leadership"], answer: 0 }
    ];

    let currentIndex = 0;
    const userAnswers = {};

    const qIndexSpan = document.getElementById("qIndex");
    const qTextDiv = document.getElementById("qText");
    const optionsContainer = document.getElementById("optionsContainer");
    const feedbackBox = document.getElementById("feedbackBox");
    const prevBtn = document.getElementById("prevBtn");
    const nextBtn = document.getElementById("nextBtn");
    const finishEarlyBtn = document.getElementById("finishEarlyBtn");
    const progressFill = document.getElementById("progressFill");
    const scoreBadge = document.getElementById("scoreBadge");
    const quizCard = document.getElementById("quizCard");
    const resultCard = document.getElementById("resultCard");

    function updateScoreBadge() {
      let correctCount = 0;
      Object.values(userAnswers).forEach(ans => {
        if (ans.isCorrect) correctCount++;
      });
      scoreBadge.textContent = `Score: ${correctCount}`;
    }

    function loadQuestion() {
      const item = quizData[currentIndex];
      qIndexSpan.textContent = `Question ${currentIndex + 1} of ${quizData.length}`;
      qTextDiv.textContent = item.question;

      const progressPercent = ((currentIndex + 1) / quizData.length) * 100;
      progressFill.style.width = `${progressPercent}%`;

      prevBtn.disabled = (currentIndex === 0);
      nextBtn.textContent = (currentIndex === quizData.length - 1) ? "Finish Quiz" : "Next";

      optionsContainer.innerHTML = "";
      feedbackBox.className = "feedback-box";
      feedbackBox.style.display = "none";

      const previousAttempt = userAnswers[currentIndex];

      item.options.forEach((optText, i) => {
        const btn = document.createElement("button");
        btn.className = "option-btn";
        btn.innerHTML = `<strong>${String.fromCharCode(65 + i)}.</strong> ${optText}`;
        
        if (previousAttempt !== undefined) {
          btn.disabled = true;
          if (i === item.answer) {
            btn.classList.add("correct");
          }
          if (i === previousAttempt.selected && !previousAttempt.isCorrect) {
            btn.classList.add("wrong");
          }
        } else {
          btn.addEventListener("click", () => handleOptionSelect(i));
        }

        optionsContainer.appendChild(btn);
      });

      if (previousAttempt !== undefined) {
        feedbackBox.style.display = "block";
        if (previousAttempt.isCorrect) {
          feedbackBox.classList.add("correct");
          feedbackBox.innerHTML = `<strong>Correct!</strong> Choice ${String.fromCharCode(65 + item.answer)} is the correct answer.`;
        } else {
          feedbackBox.classList.add("wrong");
          feedbackBox.innerHTML = `<strong>Incorrect.</strong> Correct answer is ${String.fromCharCode(65 + item.answer)}: ${item.options[item.answer]}`;
        }
      }
    }

    function handleOptionSelect(index) {
      if (userAnswers[currentIndex] !== undefined) return;

      const item = quizData[currentIndex];
      const isCorrect = (index === item.answer);

      userAnswers[currentIndex] = {
        selected: index,
        isCorrect: isCorrect
      };

      updateScoreBadge();

      const buttons = optionsContainer.children;
      if (isCorrect) {
        buttons[index].classList.add("correct");
        feedbackBox.classList.add("correct");
        feedbackBox.innerHTML = `<strong>Correct!</strong> Choice ${String.fromCharCode(65 + item.answer)} is correct.`;
      } else {
        buttons[index].classList.add("wrong");
        buttons[item.answer].classList.add("correct");
        feedbackBox.classList.add("wrong");
        feedbackBox.innerHTML = `<strong>Incorrect.</strong> Correct answer is ${String.fromCharCode(65 + item.answer)}: ${item.options[item.answer]}`;
      }

      feedbackBox.style.display = "block";
      Array.from(buttons).forEach(btn => btn.disabled = true);
    }

    prevBtn.addEventListener("click", () => {
      if (currentIndex > 0) {
        currentIndex--;
        loadQuestion();
      }
    });

    nextBtn.addEventListener("click", () => {
      if (currentIndex < quizData.length - 1) {
        currentIndex++;
        loadQuestion();
      } else {
        showResults();
      }
    });

    finishEarlyBtn.addEventListener("click", () => {
      if (confirm("Are you sure you want to stop and grade your quiz now?")) {
        showResults();
      }
    });

    function showResults() {
      quizCard.classList.add("hidden");
      resultCard.classList.remove("hidden");

      const attemptedCount = Object.keys(userAnswers).length;
      let correctCount = 0;
      Object.values(userAnswers).forEach(ans => {
        if (ans.isCorrect) correctCount++;
      });

      const percentage = attemptedCount > 0 ? Math.round((correctCount / attemptedCount) * 100) : 0;
      
      document.getElementById("finalScore").textContent = `${percentage}%`;
      document.getElementById("attemptSummary").textContent = `You completed ${attemptedCount} out of ${quizData.length} questions.`;
      document.getElementById("scoreDetails").textContent = `Score: ${correctCount} correct out of ${attemptedCount} attempted`;

      let comment = "Keep practicing!";
      if (attemptedCount === 0) {
        comment = "No questions were answered.";
      } else if (percentage >= 80) {
        comment = "Outstanding performance!";
      } else if (percentage >= 60) {
        comment = "Good effort! Review missed questions to improve.";
      }

      document.getElementById("gradeComment").textContent = comment;
    }

    document.getElementById("restartBtn").addEventListener("click", () => {
      currentIndex = 0;
      for (let key in userAnswers) delete userAnswers[key];
      updateScoreBadge();
      resultCard.classList.add("hidden");
      quizCard.classList.remove("hidden");
      loadQuestion();
    });

    loadQuestion();
  </script>
</body>
</html>
