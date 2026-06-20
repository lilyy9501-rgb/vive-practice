// 퀴즈 문제 데이터 (중3 한국사 예시 문항)
const quizData = [
    {
        question: "1. 1894년 동학 농민 군이 관군을 격파하고 전주성을 점령하자, 조선 정부가 청나라에 원병을 요청하면서 발생한 사건과 관련이 없는 것은 무엇일까요?",
        options: ["텐진 조약 체결", "일본군의 경복궁 점령", "청일 전쟁 발발", "집강소 설치"],
        answer: 0 // 첫 번째 보기가 오답/관련 없는 것 (텐진 조약은 1885년 갑신정변 직후 체결됨)
    },
    {
        question: "2. 고종이 대한제국을 선포하고 수립한 독자적인 개혁의 이름으로, '구본신참(옛것을 근본으로 하고 새것을 참고한다)'을 원칙으로 한 개혁은?",
        options: ["갑오개혁", "광무개혁", "을미개혁", "갑신정변"],
        answer: 1 // 두 번째 보기가 정답 (광무개혁)
    },
    {
        question: "3. 일제의 국권 침탈에 맞서 신돌석과 같은 평민 출신 의병장이 활약하는 등 의병 운동이 전 계층으로 확산된 계기가 된 사건은?",
        options: ["을사늑약 체결 (을사의병)", "단발령 실시 (을미의병)", "군대 해산 (정미의병)", "오백나한 사건"],
        answer: 2 // 세 번째 보기가 정답 (정미의병)
    }
];

// 화면에 퀴즈 출제하기
function loadQuiz() {
    const quizBox = document.getElementById("quiz-box");
    quizBox.innerHTML = ""; // 초기화

    quizData.forEach((data, qIndex) => {
        const questionDiv = document.createElement("div");
        questionDiv.classList.add("question-item");

        const title = document.createElement("div");
        title.classList.add("question-title");
        title.innerText = data.score ? `${data.question} (${data.score}점)` : data.question;
        questionDiv.appendChild(title);

        const optionsDiv = document.createElement("div");
        optionsDiv.classList.add("options-list");

        data.options.forEach((option, oIndex) => {
            const label = document.createElement("label");
            label.innerHTML = `
                <input type="radio" name="question${qIndex}" value="${oIndex}">
                ${option}
            `;
            optionsDiv.appendChild(label);
        });

        questionDiv.appendChild(optionsDiv);
        quizBox.appendChild(questionDiv);
    });
}

// 점수 계산 및 결과 출력
function calculateScore() {
    let score = 0;
    let allAnswered = true;

    quizData.forEach((data, qIndex) => {
        const selected = document.querySelector(`input[name="question${qIndex}"]:checked`);
        
        if (!selected) {
            allAnswered = false;
            return;
        }

        if (parseInt(selected.value) === data.answer) {
            score += 1;
        }
    });

    if (!allAnswered) {
        alert("아직 풀지 않은 문제가 있습니다! 모든 문제의 답을 선택해 주세요.");
        return;
    }

    // 결과 보여주기
    const resultBox = document.getElementById("result");
    const scoreText = document.getElementById("score-text");
    
    scoreText.innerText = `총 ${quizData.length}문제 중 ${score}문제를 맞혔습니다! 🎉`;
    resultBox.classList.remove("hidden");
    
    // 제출 버튼 비활성화 (다시 풀기 전까지)
    document.getElementById("submit-btn").disabled = true;
}

// 퀴즈 초기화 (다시 풀기)
function resetQuiz() {
    document.getElementById("result").classList.add("hidden");
    document.getElementById("submit-btn").disabled = false;
    loadQuiz();
}

// 페이지 로드 시 퀴즈 실행
window.onload = loadQuiz;
