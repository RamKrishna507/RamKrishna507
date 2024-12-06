- 👋 Hi, I’m @RamKrishna507
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
RamKrishna507/RamKrishna507 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BSEB 12th Hindi Quiz</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="quiz-container">
        <h1>BSEB 12th Hindi Quiz</h1>
        <div id="game">
            <div id="question-container">
                <p id="question"></p>
                <div id="options"></div>
            </div>
            <button id="next-btn" onclick="loadNextQuestion()">Next Question</button>
            <p id="score"></p>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>body {
    font-family: Arial, sans-serif;
    background-color: #f9f9f9;
    margin: 0;
    padding: 0;
    text-align: center;
}

.quiz-container {
    width: 90%;
    max-width: 700px;
    margin: 50px auto;
    background: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    color: #333;
}

#question-container {
    margin-bottom: 20px;
}

#options {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.option {
    padding: 10px;
    background: #f1f1f1;
    border: 1px solid #ccc;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
}

.option:hover {
    background: #ddd;
}

#next-btn {
    padding: 10px 20px;
    background: #4CAF50;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

#next-btn:hover {
    background: #45A049;
}

#score {
    font-weight: bold;
    margin-top: 20px;
}const quizData = [
    // Chapter 1: अर्धनारीश्वर
    {
        question: "अर्धनारीश्वर में 'अर्ध' का अर्थ क्या है?",
        options: ["आधा", "पूरा", "भिन्न", "समान"],
        answer: 0
    },
    {
        question: "‘अर्धनारीश्वर’ किससे सम्बंधित है?",
        options: ["शिव और शक्ति", "राम और सीता", "कृष्ण और राधा", "ब्रह्मा और सरस्वती"],
        answer: 0
    },
    // Chapter 2: सिपाही की माँ
    {
        question: "‘सिपाही की माँ’ कहानी किसके द्वारा लिखी गई है?",
        options: ["प्रेमचंद", "महादेवी वर्मा", "रेणु", "निराला"],
        answer: 1
    },
    {
        question: "‘सिपाही की माँ’ कहानी का मुख्य पात्र कौन है?",
        options: ["सिपाही", "माँ", "पिता", "भाई"],
        answer: 1
    },
    // Grammar section
    {
        question: "‘विद्या’ का सही विलोम शब्द क्या है?",
        options: ["अविद्या", "ज्ञान", "अज्ञान", "सत्य"],
        answer: 0
    },
    {
        question: "‘संधि’ का अर्थ क्या है?",
        options: ["शब्दों का मेल", "वाक्य", "अर्थ का जोड़", "उपसर्ग"],
        answer: 0
    }
];

let currentQuestionIndex = 0;
let score = 0;

const questionContainer = document.getElementById("question");
const optionsContainer = document.getElementById("options");
const scoreContainer = document.getElementById("score");

function loadQuestion() {
    const currentQuestion = quizData[currentQuestionIndex];
    questionContainer.innerText = currentQuestion.question;
    optionsContainer.innerHTML = "";
    currentQuestion.options.forEach((option, index) => {
        const optionElement = document.createElement("button");
        optionElement.innerText = option;
        optionElement.className = "option";
        optionElement.onclick = () => checkAnswer(index);
        optionsContainer.appendChild(optionElement);
    });
}

function checkAnswer(selectedOption) {
    const currentQuestion = quizData[currentQuestionIndex];
    if (selectedOption === currentQuestion.answer) {
        score += 10;
        alert("सही उत्तर! आपने 10 अंक अर्जित किए।");
    } else {
        alert("गलत उत्तर! सही उत्तर है: " + currentQuestion.options[currentQuestion.answer]);
    }
    currentQuestionIndex++;
    if (currentQuestionIndex < quizData.length) {
        loadQuestion();
    } else {
        endQuiz();
    }
}

function endQuiz() {
    questionContainer.innerText = "Quiz समाप्त हुआ!";
    optionsContainer.innerHTML = "";
    document.getElementById("next-btn").style.display = "none";
    scoreContainer.innerText = `आपका स्कोर: ${score}`;
}

function loadNextQuestion() {
    loadQuestion();
}

// Initialize quiz
loadQuestion();
