![image](https://github.com/user-attachments/assets/ecafba85-3ca7-4107-b0e5-8e2acb71cbd6)

## Exam Practice Center

This project is a web-based exam simulation platform designed for practicing certification exams. It includes interactive features like timed quizzes, score tracking, and a leaderboard to enhance the learning experience.

### Key Features
## Frontend

*User-Friendly Interface*
- Built with HTML, CSS, and JavaScript for an intuitive and interactive experience.
- Dynamic rendering of questions and answer options.

*Timer Integration*
- countdown timer keeps track of the remaining exam time (60 minutes by default).

*Responsive Design*
- Fully responsive interface ensuring usability on all devices.

*Dynamic Feedback*

- Provides immediate visual feedback on correct and incorrect answers.
- Highlights correct answers in green and incorrect answers in red.

*Leaderboard*
- Displays user rankings based on scores, fostering competition and motivation.
# Quiz Application

## Technical Breakdown

### HTML Structure
- **Sections include**:
  - Username input to start the exam.
  - A quiz area displaying questions and answer options.
  - A result screen showing the user’s score.
  - A leaderboard to showcase top scorers.

### CSS Styling
- Provides a clean and modern UI with:
  - Rounded corners.
  - Hover effects.
  - Color-coded feedback for answers.
- Ensures a visually appealing experience across different devices.

### JavaScript Logic
- **Question Array**: Stores questions, answer options, and the index of the correct answer.
- **Timer Functionality**: Manages countdown and stops the quiz when time expires.
- **Answer Validation**: Verifies the selected answer against the correct one and visually indicates results.
- **Leaderboard Sorting**: Dynamically ranks users by their scores.

## How It Works

### 1. Start the Exam
- Users enter their name to begin the exam.
- A countdown timer is initiated.

### 2. Answer Questions
- Questions are displayed one at a time.
- Users select an answer and receive immediate feedback.

### 3. Complete the Exam
- After all questions are answered or time expires:
  - The user’s score is displayed.
  - The user can view the leaderboard to see their rank.

### 4. Leaderboard
- Displays the top performers sorted by scores.

## Code Highlights
```javascript
const questions = [
    {
        question: "How do you specify a module's version when publishing it to the public Terraform Module Registry?",
        options: [
            "A. Configure it in the module's Terraform code",
            "B. Mention it on the module's configuration page on the Terraform Module Registry",
            "C. The Terraform Module Registry does not support versioning modules",
            "D. Tag a release in the associated repo"
        ],
        correct: 3
    },
    // More questions...
];
```
Each object contains:

## question: 
The exam question.

## options:
Array of multiple-choice answers.

## correct:
Index of the correct answer.


### Timer Functionality

![image](https://github.com/user-attachments/assets/023ac1a1-342a-4a4f-b11b-3802dea2c608)

```javascript
function startTimer() {
    timerInterval = setInterval(() => {
        if (timer > 0) {
            timer--;
            let minutes = Math.floor(timer / 60);
            let seconds = timer % 60;
            document.getElementById("timer").textContent = `Time Left: ${minutes}:${seconds < 10 ? '0' + seconds : seconds}`;
        } else {
            clearInterval(timerInterval);
            endExam();
        }
    }, 1000);
}
```
Updates the timer every second and ends the exam when time runs out.

### Answer Validation


```javascript
function nextQuestion() {
    const selectedAnswer = document.querySelector("input[name='answer']:checked");
    if (selectedAnswer) {
        const selectedIndex = parseInt(selectedAnswer.value);
        const question = questions[currentQuestionIndex];
        // Check correctness
        if (selectedIndex === question.correct) {
            score++;
        }
        currentQuestionIndex++;
        if (currentQuestionIndex < questions.length) {
            loadQuestion();
        } else {
            endExam();
        }
    }
}
```

Verifies user selection and updates the score.

### Leaderboard Update

![image](https://github.com/user-attachments/assets/943a2ce7-75f1-436b-896d-1ddbe59ff800)

```js
function showLeaderboard() {
    leaderboard.push({ name: username, score: score });
    leaderboard.sort((a, b) => b.score - a.score); // Sort leaderboard by score
}
```

## How to Run

1. Clone the repository.
2. Open the `index.html` file in any modern web browser.
3. Start the exam and track your progress on the leaderboard.

![image](https://github.com/user-attachments/assets/8c144f7b-e525-403d-8b38-5ec89186e9c2)

Questions must be added to the html using array js script format

```javascript
    {
        "question": "Which is not a service type in Kubernetes?",
        "options": ["ClusterIP", "NodePort", "Ingress", "LoadBalancer", "ExternalName"],
        "correct": 2
    },
    {
        "question": "What standard does kubelet use to communicate with the container runtime?",
        "options": ["Service Mesh Interface (SMI)", "CRI-O", "ContainerD", "Container Runtime Interface (CRI)"],
        "correct": 3
    },
```
    
Github repo:

https://github.com/DarkHexSage/CertExamTestCenter/tree/main




