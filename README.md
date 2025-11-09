<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Sikh History Quiz</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f5f7fa;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      padding: 40px;
    }
    #quiz-container {
      background: #fff;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      display: flex;
      width: 90%;
      max-width: 900px;
      padding: 20px;
      gap: 20px;
    }
    #left-panel {
      flex: 2;
    }
    #right-panel {
      flex: 1;
      background: #f0f0f0;
      padding: 15px;
      border-radius: 8px;
      font-size: 14px;
      line-height: 1.5;
    }
    h2 {
      margin-bottom: 20px;
    }
    .option {
      background: #e0e0e0;
      padding: 10px;
      margin: 8px 0;
      border-radius: 5px;
      cursor: pointer;
      transition: background 0.2s;
    }
    .option:hover {
      background: #d0d0d0;
    }
    #next-btn {
      margin-top: 20px;
      padding: 10px 20px;
      border: none;
      background: #007bff;
      color: white;
      border-radius: 5px;
      cursor: pointer;
      display: none;
    }
    #next-btn:hover {
      background: #0056b3;
    }
    #score {
      margin-top: 15px;
      font-weight: bold;
    }
  </style>
</head>
<body>

   <!-- Header Section -->
  <div id="header">
    <h1>ੴ</h1>
    <p>Dhan Guru Granth Sahib Ji</p>
  </div>
  
  <div id="quiz-container">
    <div id="left-panel">
      <h2 id="question">Question text</h2>
      <div id="options"></div>
      <button id="next-btn">Next Question</button>
      <div id="score"></div>
    </div>
    <div id="right-panel">
      <h3>Explanation</h3>
      <p id="explanation-text">Select an answer to see more information here.</p>
    </div>
  </div>

  <script>
    const quiz = [
      {
        question: "Who was the founder of Sikhism?",
        options: ["Guru Nanak Dev Ji", "Guru Gobind Singh Ji", "Guru Arjan Dev Ji", "Guru Tegh Bahadur Ji"],
        answer: "Guru Nanak Dev Ji",
        marks: 1,
        explanation: "Guru Nanak Dev Ji, born in 1469, was the first Sikh Guru and the founder of Sikhism. His teachings focused on equality, truth, and devotion to one God. He spread the message of peace and unity among all religions."
      },
      {
        question: "In which year was Guru Nanak Dev Ji born?",
        options: ["1469", "1499", "1505", "1450"],
        answer: "1469",
        marks: 1,
        explanation: "Guru Nanak Dev Ji was born in 1469 in Talwandi (now Nankana Sahib, Pakistan). His birth is celebrated worldwide as Gurpurab, a major Sikh festival."
      },
      {
        question: "Which Guru compiled the Adi Granth?",
        options: ["Guru Arjan Dev Ji", "Guru Gobind Singh Ji", "Guru Nanak Dev Ji", "Guru Ram Das Ji"],
        answer: "Guru Arjan Dev Ji",
        marks: 2,
        explanation: "Guru Arjan Dev Ji, the fifth Guru, compiled the Adi Granth in 1604. It contains the hymns of Sikh Gurus and saints, forming the basis of the Guru Granth Sahib."
      },
      {
        question: "What is the significance of Vaisakhi in Sikhism?",
        options: ["Formation of Khalsa in 1699", "Birth of Guru Nanak", "Start of Langar", "Guru Granth Sahib completion"],
        answer: "Formation of Khalsa in 1699",
        marks: 2,
        explanation: "Vaisakhi marks the formation of the Khalsa by Guru Gobind Singh Ji in 1699 at Anandpur Sahib. It symbolizes the birth of the Sikh community committed to courage, equality, and faith."
      },
      {
        question: "Who was the 10th Sikh Guru?",
        options: ["Guru Gobind Singh Ji", "Guru Arjan Dev Ji", "Guru Nanak Dev Ji", "Guru Tegh Bahadur Ji"],
        answer: "Guru Gobind Singh Ji",
        marks: 1,
        explanation: "Guru Gobind Singh Ji, the 10th Sikh Guru, founded the Khalsa in 1699 and completed the Guru Granth Sahib, declaring it the eternal Guru of the Sikhs."
      },
      {
        question: "What are the five Ks of Sikhism?",
        options: ["Kesh, Kangha, Kara, Kachera, Kirpan", "Kangha, Kara, Langar, Kirpan, Kachera", "Kesh, Kara, Langar, Kirpan, Kachera", "Kara, Kesh, Kangha, Kirpan, Langar"],
        answer: "Kesh, Kangha, Kara, Kachera, Kirpan",
        marks: 2,
        explanation: "The five Ks are symbols of Sikh identity: Kesh (uncut hair), Kangha (comb), Kara (steel bracelet), Kachera (cotton shorts), and Kirpan (sword)."
      },
      {
        question: "Which battle is Guru Gobind Singh Ji famous for?",
        options: ["Battle of Chamkaur", "Battle of Panipat", "Battle of Kurukshetra", "Battle of Sirhind"],
        answer: "Battle of Chamkaur",
        marks: 2,
        explanation: "The Battle of Chamkaur (1704) was fought between Guru Gobind Singh Ji's small Sikh force and the Mughal army. Despite being outnumbered, the Sikhs fought bravely for their faith."
      },
      {
        question: "Who was the first Sikh martyr?",
        options: ["Guru Arjan Dev Ji", "Guru Tegh Bahadur Ji", "Guru Gobind Singh Ji", "Guru Nanak Dev Ji"],
        answer: "Guru Arjan Dev Ji",
        marks: 1,
        explanation: "Guru Arjan Dev Ji became the first Sikh martyr in 1606 after refusing to convert to Islam. His sacrifice strengthened the Sikh faith."
      },
      {
        question: "Where is the Golden Temple located?",
        options: ["Amritsar, Punjab, India", "Delhi, India", "Chandigarh, India", "Lahore, Pakistan"],
        answer: "Amritsar, Punjab, India",
        marks: 1,
        explanation: "The Golden Temple, or Harmandir Sahib, is located in Amritsar, Punjab. It’s the holiest shrine of Sikhism and symbolizes equality and humility."
      },
      {
        question: "Which Guru introduced the concept of Langar?",
        options: ["Guru Nanak Dev Ji", "Guru Arjan Dev Ji", "Guru Gobind Singh Ji", "Guru Tegh Bahadur Ji"],
        answer: "Guru Nanak Dev Ji",
        marks: 1,
        explanation: "Guru Nanak Dev Ji introduced Langar — a free community kitchen — promoting equality, where people of all castes and religions share meals together."
      }
    ];

    let currentQuestion = 0;
    let score = 0;

    const questionEl = document.getElementById("question");
    const optionsEl = document.getElementById("options");
    const explanationEl = document.getElementById("explanation-text");
    const scoreEl = document.getElementById("score");
    const nextBtn = document.getElementById("next-btn");

    function loadQuestion() {
      const q = quiz[currentQuestion];
      questionEl.textContent = `Q${currentQuestion + 1}: ${q.question}`;
      optionsEl.innerHTML = "";
      explanationEl.textContent = "Select an answer to see more information here.";
      q.options.forEach(option => {
        const btn = document.createElement("div");
        btn.textContent = option;
        btn.className = "option";
        btn.onclick = () => checkAnswer(option, q);
        optionsEl.appendChild(btn);
      });
      nextBtn.style.display = "none";
    }

    function checkAnswer(selected, q) {
      if (selected === q.answer) {
        score += q.marks;
        alert(`✅ Correct! You earned ${q.marks} marks.`);
      } else {
        alert(`❌ Wrong! Correct answer: ${q.answer}`);
      }
      explanationEl.textContent = q.explanation;
      nextBtn.style.display = "block";
    }

    nextBtn.onclick = () => {
      currentQuestion++;
      if (currentQuestion < quiz.length) {
        loadQuestion();
      } else {
        questionEl.textContent = "🎉 Quiz Completed!";
        optionsEl.innerHTML = "";
        explanationEl.textContent = "";
        scoreEl.textContent = `Your total score: ${score} / ${quiz.reduce((a, q) => a + q.marks, 0)}`;
        nextBtn.style.display = "none";
      }
    };

    loadQuestion();
  </script>
</body>
</html>
