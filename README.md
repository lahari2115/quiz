<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Simple Quiz App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
        }
        .question {
            font-size: 18px;
            margin-bottom: 10px;
        }
        .options {
            list-style: none;
            padding: 0;
        }
        .option {
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Simple Quiz</h1>
        <div class="question"></div>
        <ul class="options"></ul>
        <button id="next">Next</button>
    </div>

    <script>
        const questions = [
            {
                question: "What is the capital of France?",
                options: ["London", "Madrid", "Paris", "Berlin"],
                answer: "Paris"
            },
            {
                question: "Which planet is known as the Red Planet?",
                options: ["Mars", "Jupiter", "Earth", "Venus"],
                answer: "Mars"
            },
            {
                question: "What is the largest mammal in the world?",
                options: ["Giraffe", "Elephant", "Blue Whale", "Lion"],
                answer: "Blue Whale"
            }
        ];

        let currentQuestion = 0;

        const questionText = document.querySelector('.question');
        const optionsList = document.querySelector('.options');
        const nextButton = document.getElementById('next');

        function displayQuestion() {
            const current = questions[currentQuestion];
            questionText.textContent = current.question;
            optionsList.innerHTML = "";
            current.options.forEach(option => {
                const li = document.createElement('li');
                li.textContent = option;
                li.classList.add('option');
                li.addEventListener('click', () => checkAnswer(option));
                optionsList.appendChild(li);
            });
        }

        function checkAnswer(selected) {
            const current = questions[currentQuestion];
            if (selected === current.answer) {
                // You can add code to handle correct answers
                alert("Correct!");
            } else {
                // You can add code to handle incorrect answers
                alert("Incorrect. The correct answer is: " + current.answer);
            }
            currentQuestion++;
            if (currentQuestion < questions.length) {
                displayQuestion();
            } else {
                // Quiz is over
                alert("Quiz is over. You got " + (currentQuestion) + " out of " + questions.length + " questions correct.");
            }
        }

        nextButton.addEventListener('click', () => {
            if (currentQuestion < questions.length) {
                displayQuestion();
            }
        });

        // Start the quiz
        displayQuestion();
    </script>
</body>
</html>
