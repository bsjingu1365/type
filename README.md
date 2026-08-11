<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#4A90D9">

  <title>나의 봉사 성향 테스트</title>

  <style>
    * {
      box-sizing: border-box;
    }

    :root {
      --main: #438fd5;
      --main-light: #eaf4ff;
      --text: #203d59;
      --gray: #6f7c89;
      --line: #e2e8ee;
      --background: #f5f8fb;
    }

    html {
      min-height: 100%;
    }

    body {
      margin: 0;
      min-height: 100vh;
      font-family:
        Pretendard,
        "Noto Sans KR",
        "Apple SD Gothic Neo",
        "Malgun Gothic",
        sans-serif;

      color: var(--text);

      background:
        radial-gradient(
          circle at 10% 10%,
          rgba(255, 190, 203, 0.18),
          transparent 25%
        ),
        radial-gradient(
          circle at 90% 10%,
          rgba(117, 194, 255, 0.16),
          transparent 28%
        ),
        radial-gradient(
          circle at 50% 100%,
          rgba(154, 218, 154, 0.15),
          transparent 28%
        ),
        var(--background);
    }

    button,
    input {
      font: inherit;
    }

    button {
      cursor: pointer;
    }

    /* 전체 영역 */

    .container {
      width: min(92%, 720px);
      min-height: 100vh;
      margin: 0 auto;

      display: flex;
      align-items: center;
      justify-content: center;

      padding: 25px 0;
    }

    .screen {
      display: none;
      width: 100%;
    }

    .screen.active {
      display: block;
      animation: fadeIn 0.3s ease;
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: translateY(8px);
      }

      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .card {
      width: 100%;
      padding: 38px 30px;

      background: rgba(255, 255, 255, 0.97);

      border: 1px solid #e7ebf0;
      border-radius: 28px;

      box-shadow:
        0 18px 50px rgba(31, 55, 80, 0.09);
    }


    /* =========================
       시작 화면
    ========================= */

    .start-card {
      text-align: center;
    }

    .small-title {
      display: inline-block;

      padding: 8px 14px;

      border-radius: 999px;

      background: #eaf4ff;
      color: #3a83ca;

      font-size: 12px;
      font-weight: 900;
      letter-spacing: 1px;
    }

    .main-title {
      margin: 17px 0 12px;

      font-size: clamp(32px, 7vw, 46px);
      line-height: 1.2;

      letter-spacing: -2px;
    }

    .intro {
      margin: 0 0 27px;

      color: var(--gray);

      font-size: 16px;
      line-height: 1.8;
    }

    .type-list {
      display: grid;
      grid-template-columns: 1fr 1fr;

      gap: 10px;

      margin-bottom: 28px;

      text-align: left;
    }

    .type-item {
      padding: 13px 14px;

      border: 1px solid #e4e9ef;
      border-radius: 14px;

      background: #f8fafc;

      font-size: 14px;
      font-weight: 800;
    }

    .type-item:last-child {
      grid-column: 1 / -1;
    }

    .name-label {
      display: block;

      margin-bottom: 8px;

      text-align: left;

      font-size: 14px;
      font-weight: 900;
    }

    .optional {
      color: #929ba5;
      font-weight: 500;
    }

    .name-input {
      width: 100%;
      height: 54px;

      padding: 0 16px;

      border: 1.5px solid #dce4ec;
      border-radius: 14px;

      outline: none;

      background: white;

      transition: 0.2s;
    }

    .name-input:focus {
      border-color: #4a95db;

      box-shadow:
        0 0 0 4px rgba(74, 149, 219, 0.1);
    }

    .main-btn {
      width: 100%;
      min-height: 55px;

      margin-top: 16px;

      border: none;
      border-radius: 15px;

      background:
        linear-gradient(
          135deg,
          #3d86cf,
          #55a1e4
        );

      color: white;

      font-size: 16px;
      font-weight: 900;

      box-shadow:
        0 10px 22px rgba(61, 134, 207, 0.2);

      transition: 0.15s;
    }

    .main-btn:hover {
      transform: translateY(-1px);
    }

    .notice {
      margin-top: 15px;

      color: #929ba5;

      font-size: 13px;
    }


    /* =========================
       질문 화면
    ========================= */

    .quiz-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .back-btn {
      padding: 8px 0;

      border: none;

      background: transparent;

      color: #6d7883;

      font-size: 14px;
      font-weight: 800;
    }

    .counter {
      color: #77818c;

      font-size: 14px;
      font-weight: 800;
    }

    .progress {
      width: 100%;
      height: 8px;

      margin-top: 16px;

      overflow: hidden;

      border-radius: 999px;

      background: #ebeff4;
    }

    .progress-bar {
      width: 16.67%;
      height: 100%;

      border-radius: 999px;

      background:
        linear-gradient(
          90deg,
          #4b94d7,
          #6eb8e5
        );

      transition: width 0.3s ease;
    }

    .question-box {
      padding: 35px 2px 25px;
    }

    .question-number {
      margin: 0 0 9px;

      color: #4187c9;

      font-size: 12px;
      font-weight: 900;
      letter-spacing: 1px;
    }

    .question-text {
      margin: 0;

      font-size: clamp(22px, 5vw, 28px);
      line-height: 1.5;

      letter-spacing: -1px;
    }

    .answer-list {
      display: grid;

      gap: 11px;
    }

    .answer-btn {
      width: 100%;
      min-height: 65px;

      display: flex;
      align-items: center;

      gap: 13px;

      padding: 14px 15px;

      border: 1.5px solid #e1e7ed;
      border-radius: 16px;

      background: white;

      color: #253f59;

      text-align: left;
      line-height: 1.5;

      transition: 0.15s;
    }

    .answer-btn:hover {
      border-color: #83b8e5;

      background: #f7fbff;

      transform: translateY(-1px);
    }

    .answer-letter {
      flex: 0 0 35px;

      width: 35px;
      height: 35px;

      display: flex;
      align-items: center;
      justify-content: center;

      border-radius: 50%;

      background: #eaf4fd;

      color: #347fc4;

      font-size: 14px;
      font-weight: 900;
    }


    /* =========================
       결과 화면
    ========================= */

    .result-top {
      margin-bottom: 15px;

      text-align: center;

      color: #7a8590;

      font-size: 15px;
      font-weight: 800;
    }

    .result-card {
      position: relative;

      overflow: hidden;

      padding: 30px;

      border: 2px solid #ffc5d1;
      border-radius: 24px;

      background: white;
    }

    .result-icon {
      width: 70px;
      height: 70px;

      display: flex;
      align-items: center;
      justify-content: center;

      border-radius: 20px;

      background: #fff0f4;

      font-size: 34px;
    }

    .result-label {
      margin: 23px 0 5px;

      font-size: 14px;
      font-weight: 900;
    }

    .result-title {
      margin: 0;

      font-size: clamp(32px, 7vw, 42px);

      letter-spacing: -2px;
    }

    .result-tagline {
      margin-top: 12px;

      font-size: 17px;
      font-weight: 900;
      line-height: 1.6;
    }

    .result-description {
      color: #65717d;

      font-size: 15px;
      line-height: 1.8;
    }

    .result-section {
      margin-top: 22px;
      padding-top: 18px;

      border-top: 1px dashed #d9dfe5;
    }

    .result-section h3 {
      margin: 0 0 12px;

      font-size: 15px;
    }

    .tag-box {
      display: flex;
      flex-wrap: wrap;

      gap: 8px;
    }

    .tag {
      display: inline-block;

      padding: 8px 11px;

      border-radius: 999px;

      font-size: 13px;
      font-weight: 800;
    }

    .result-message {
      margin-top: 23px;

      padding: 16px;

      border-radius: 14px;

      background: #f8fafc;

      font-size: 15px;
      font-weight: 900;
      line-height: 1.6;
    }

    .result-buttons {
      display: grid;
      grid-template-columns: 1fr 1fr;

      gap: 10px;

      margin-top: 16px;
    }

    .sub-btn,
    .restart-btn {
      min-height: 53px;

      border: none;
      border-radius: 14px;

      font-weight: 900;
    }

    .sub-btn {
      background: #eaf4ff;

      color: #347fc4;
    }

    .restart-btn {
      background: #438fd5;

      color: white;
    }

    .share-message {
      min-height: 20px;

      margin: 10px 0 0;

      text-align: center;

      color: #75808b;

      font-size: 13px;
    }


    /* =========================
       모바일
    ========================= */

    @media (max-width: 520px) {

      .container {
        width: calc(100% - 20px);

        padding: 15px 0;
      }

      .card {
        padding: 27px 18px;

        border-radius: 22px;
      }

      .type-list {
        grid-template-columns: 1fr;
      }

      .type-item:last-child {
        grid-column: auto;
      }

      .answer-btn {
        min-height: 61px;

        padding: 13px;
      }

      .result-card {
        padding: 24px 19px;
      }

      .result-buttons {
        grid-template-columns: 1fr;
      }

    }

  </style>
</head>


<body>

  <main class="container">


    <!-- =========================
         시작 화면
    ========================== -->

    <section
      id="startScreen"
      class="screen active"
    >

      <div class="card start-card">

        <div class="small-title">
          VOLUNTEER TYPE TEST
        </div>

        <h1 class="main-title">
          나의 봉사 성향 테스트
        </h1>

        <p class="intro">
          나는 어떤 봉사와 가장 잘 맞을까요?<br>
          6개의 질문에 답하고
          나의 봉사 성향을 확인해보세요!
        </p>


        <div class="type-list">

          <div class="type-item">
            ❤️ 따뜻한 나눔형
          </div>

          <div class="type-item">
            ⭐ 함께하는 리더형
          </div>

          <div class="type-item">
            🌱 환경 실천형
          </div>

          <div class="type-item">
            🎨 재능나눔형
          </div>

          <div class="type-item">
            📚 성장 지원형
          </div>

        </div>


        <label
          class="name-label"
          for="nameInput"
        >
          이름
          <span class="optional">
            (선택)
          </span>
        </label>


        <input
          id="nameInput"
          class="name-input"
          type="text"
          maxlength="12"
          placeholder="이름을 입력해주세요"
          autocomplete="off"
        >


        <button
          class="main-btn"
          type="button"
          onclick="startTest()"
        >
          테스트 시작하기
        </button>


        <div class="notice">
          정답은 없어요!
          나와 가장 가까운 답을 골라주세요.
        </div>

      </div>

    </section>



    <!-- =========================
         질문 화면
    ========================== -->

    <section
      id="quizScreen"
      class="screen"
    >

      <div class="card">


        <div class="quiz-header">

          <button
            id="backButton"
            class="back-btn"
            type="button"
            onclick="goBack()"
          >
            ← 이전
          </button>


          <div class="counter">
            <span id="currentQuestion">
              1
            </span>

            /

            <span id="totalQuestion">
              6
            </span>
          </div>

        </div>


        <div class="progress">

          <div
            id="progressBar"
            class="progress-bar"
          ></div>

        </div>


        <div class="question-box">

          <p
            id="questionNumber"
            class="question-number"
          >
            QUESTION 01
          </p>


          <h2
            id="questionText"
            class="question-text"
          ></h2>

        </div>


        <div
          id="answerList"
          class="answer-list"
        ></div>


      </div>

    </section>



    <!-- =========================
         결과 화면
    ========================== -->

    <section
      id="resultScreen"
      class="screen"
    >

      <div class="card">


        <div class="result-top">
          나의 봉사 성향은?
        </div>


        <div
          id="resultCard"
          class="result-card"
        >


          <div
            id="resultIcon"
            class="result-icon"
          ></div>


          <div
            id="resultLabel"
            class="result-label"
          >
            나의 봉사 성향은?
          </div>


          <h2
            id="resultTitle"
            class="result-title"
          ></h2>


          <p
            id="resultTagline"
            class="result-tagline"
          ></p>


          <p
            id="resultDescription"
            class="result-description"
          ></p>



          <div class="result-section">

            <h3>
              나의 봉사 키워드
            </h3>

            <div
              id="keywordList"
              class="tag-box"
            ></div>

          </div>



          <div class="result-section">

            <h3>
              나에게 잘 맞는 봉사활동
            </h3>

            <div
              id="recommendList"
              class="tag-box"
            ></div>

          </div>



          <div
            id="resultMessage"
            class="result-message"
          ></div>


        </div>



        <div class="result-buttons">

          <button
            class="sub-btn"
            type="button"
            onclick="shareResult()"
          >
            결과 공유하기
          </button>


          <button
            class="restart-btn"
            type="button"
            onclick="restartTest()"
          >
            다시 테스트하기
          </button>

        </div>


        <p
          id="shareMessage"
          class="share-message"
        ></p>


      </div>

    </section>


  </main>



  <script>

    /* =========================
       5가지 봉사 성향
    ========================== */

    const TYPES = {

      A: {

        title: "따뜻한 나눔형",

        icon: "❤️",

        tagline:
          "따뜻한 마음으로 이웃에게 힘이 되어주는 봉사자",

        description:
          "다른 사람의 이야기에 귀 기울이고, 도움이 필요한 사람을 직접 돕는 활동에서 보람을 느끼는 유형이에요. 작은 관심과 배려를 통해 누군가에게 따뜻한 하루를 선물하는 것을 좋아해요.",

        keywords: [
          "공감",
          "배려",
          "소통",
          "돌봄"
        ],

        recommends: [
          "어르신 말벗",
          "취약계층 나눔",
          "도시락·반찬 나눔",
          "아동 돌봄 보조",
          "안부 확인 활동"
        ],

        message:
          "당신의 따뜻한 관심은 누군가에게 큰 힘이 됩니다!",

        color: "#EF607D",

        soft: "#FFF0F4",

        border: "#FFC5D1"

      },



      B: {

        title: "함께하는 리더형",

        icon: "⭐",

        tagline:
          "사람들과 힘을 모아 변화를 만들어가는 봉사자",

        description:
          "여러 사람과 함께 활동하고 의견을 나누는 것을 좋아하는 유형이에요. 활동을 계획하거나 친구들을 이끌고, 모두가 함께 참여할 수 있도록 분위기를 만드는 데 강점이 있어요.",

        keywords: [
          "리더십",
          "협동",
          "적극성",
          "소통"
        ],

        recommends: [
          "캠페인 운영",
          "행사 진행 보조",
          "봉사단 활동",
          "체험부스 운영",
          "지역사회 홍보활동"
        ],

        message:
          "함께할 때 더 큰 변화를 만드는 당신은 우리 동네의 든든한 리더!",

        color: "#3488D1",

        soft: "#EDF7FF",

        border: "#ACD4F3"

      },



      C: {

        title: "환경 실천형",

        icon: "🌱",

        tagline:
          "작은 실천으로 지구와 우리 동네를 지키는 봉사자",

        description:
          "환경문제에 관심이 많고 일상에서 직접 실천하는 것을 중요하게 생각하는 유형이에요. 환경을 위한 작은 행동도 꾸준히 이어지면 큰 변화를 만들 수 있다고 믿어요.",

        keywords: [
          "실천",
          "환경",
          "책임감",
          "지속가능성"
        ],

        recommends: [
          "플로깅",
          "자원순환 활동",
          "환경캠페인",
          "생태보호 활동",
          "탄소중립 실천",
          "환경교육 보조"
        ],

        message:
          "오늘의 작은 실천이 내일의 지구를 바꿉니다!",

        color: "#37A55A",

        soft: "#EEFAF0",

        border: "#BCE3C6"

      },



      D: {

        title: "재능나눔형",

        icon: "🎨",

        tagline:
          "내가 잘하고 좋아하는 것으로 나눔을 실천하는 봉사자",

        description:
          "그림, 음악, 만들기, 사진, 글쓰기 등 자신의 재능과 관심사를 다른 사람과 나눌 때 즐거움을 느끼는 유형이에요. 내가 가진 작은 재능도 누군가에게는 특별한 선물이 될 수 있어요.",

        keywords: [
          "창의성",
          "재능",
          "표현",
          "즐거움"
        ],

        recommends: [
          "미술·공예 봉사",
          "공연 봉사",
          "사진·영상 촬영",
          "디자인·홍보 봉사",
          "교육 재능기부"
        ],

        message:
          "당신의 재능이 누군가에게 특별한 선물이 될 수 있어요!",

        color: "#8D65C7",

        soft: "#F5F0FC",

        border: "#D6C4ED"

      },



      E: {

        title: "성장 지원형",

        icon: "📚",

        tagline:
          "배움과 경험을 나누며 함께 성장하는 봉사자",

        description:
          "새로운 것을 배우고 알려주는 것을 좋아하며, 다른 사람의 성장을 돕는 과정에서 보람을 느끼는 유형이에요. 지식과 경험을 나누면서 나 자신도 함께 성장하는 봉사를 선호해요.",

        keywords: [
          "배움",
          "교육",
          "성장",
          "책임감"
        ],

        recommends: [
          "학습 멘토링",
          "진로 멘토링",
          "교육 보조",
          "아동·청소년 프로그램 지원",
          "디지털 교육 봉사"
        ],

        message:
          "함께 배우고 성장할 때 더 나은 내일이 만들어집니다!",

        color: "#EC8A22",

        soft: "#FFF5E8",

        border: "#FFD29D"

      }

    };



    /* =========================
       6개 질문
    ========================== */

    const QUESTIONS = [


      /* Q1 */

      {

        text:
          "봉사활동을 시작한다면 가장 끌리는 활동은?",

        answers: {

          A:
            "혼자 계신 어르신의 말벗이 되어드리기",

          B:
            "친구들과 함께 캠페인을 기획하고 진행하기",

          C:
            "우리 동네를 걸으며 환경정화 활동하기",

          D:
            "그림이나 만들기 재능을 활용해 나눔하기",

          E:
            "어린 친구들의 공부나 체험활동 도와주기"

        }

      },



      /* Q2 */

      {

        text:
          "친구들과 무언가를 준비할 때 나는?",

        answers: {

          A:
            "힘들어하는 친구가 없는지 먼저 살펴본다.",

          B:
            "의견을 내고 친구들의 역할을 정리한다.",

          C:
            "작은 것이라도 직접 행동으로 옮기는 편이다.",

          D:
            "재미있고 새로운 아이디어를 제안한다.",

          E:
            "친구들이 어려워하는 부분을 설명해준다."

        }

      },



      /* Q3 */

      {

        text:
          "봉사활동을 마친 뒤 가장 뿌듯할 것 같은 순간은?",

        answers: {

          A:
            "“덕분에 힘이 됐어요.”라는 말을 들었을 때",

          B:
            "모두가 힘을 합쳐 목표를 달성했을 때",

          C:
            "나의 작은 행동으로 주변에 변화가 생겼을 때",

          D:
            "내가 가진 재능으로 사람들이 즐거워할 때",

          E:
            "내가 도운 사람이 새로운 것을 배우거나 성장했을 때"

        }

      },



      /* Q4 */

      {

        text:
          "우리 동네에 새로운 봉사활동을 만든다면?",

        answers: {

          A:
            "홀로 지내는 이웃에게 안부를 전하는 활동",

          B:
            "주민들이 함께 참여하는 캠페인",

          C:
            "깨끗한 우리 동네를 만드는 환경 프로젝트",

          D:
            "주민들과 함께하는 문화·예술 체험활동",

          E:
            "아이들과 함께 배우는 교육·멘토링 활동"

        }

      },



      /* Q5 */

      {

        text:
          "봉사활동에서 내가 맡고 싶은 역할은?",

        answers: {

          A:
            "참여자를 세심하게 챙기는 역할",

          B:
            "사람들을 이끌고 전체 활동을 진행하는 역할",

          C:
            "현장에서 직접 움직이고 실천하는 역할",

          D:
            "홍보물이나 체험 프로그램을 만드는 역할",

          E:
            "활동 내용을 설명하고 알려주는 역할"

        }

      },



      /* Q6 */

      {

        text:
          "내가 생각하는 가장 멋진 봉사자는?",

        answers: {

          A:
            "다른 사람의 마음을 따뜻하게 살피는 사람",

          B:
            "여러 사람을 하나로 모아 함께 행동하는 사람",

          C:
            "작은 일이라도 꾸준히 실천하는 사람",

          D:
            "자신이 가진 재능을 기꺼이 나누는 사람",

          E:
            "자신의 지식과 경험을 다른 사람과 나누는 사람"

        }

      }

    ];



    /* =========================
       테스트 상태
    ========================== */

    let currentQuestion = 0;

    let answers =
      new Array(
        QUESTIONS.length
      ).fill(null);

    let userName = "";



    /* =========================
       화면 전환
    ========================== */

    function showScreen(id) {

      document
        .querySelectorAll(".screen")
        .forEach(function(screen) {

          screen.classList.remove(
            "active"
          );

        });


      document
        .getElementById(id)
        .classList.add(
          "active"
        );


      window.scrollTo({
        top: 0,
        behavior: "smooth"
      });

    }



    /* =========================
       테스트 시작
    ========================== */

    function startTest() {

      userName =
        document
          .getElementById(
            "nameInput"
          )
          .value
          .trim();


      currentQuestion = 0;


      answers =
        new Array(
          QUESTIONS.length
        ).fill(null);


      renderQuestion();


      showScreen(
        "quizScreen"
      );

    }



    /* =========================
       질문 출력
    ========================== */

    function renderQuestion() {

      const question =
        QUESTIONS[
          currentQuestion
        ];


      document
        .getElementById(
          "currentQuestion"
        )
        .textContent =
        currentQuestion + 1;


      document
        .getElementById(
          "totalQuestion"
        )
        .textContent =
        QUESTIONS.length;


      document
        .getElementById(
          "questionNumber"
        )
        .textContent =
        "QUESTION " +
        String(
          currentQuestion + 1
        ).padStart(
          2,
          "0"
        );


      document
        .getElementById(
          "questionText"
        )
        .textContent =
        question.text;



      /* 진행률 */

      const progress =
        (
          (
            currentQuestion + 1
          )
          /
          QUESTIONS.length
        )
        *
        100;


      document
        .getElementById(
          "progressBar"
        )
        .style.width =
        progress + "%";



      /* 이전 버튼 */

      document
        .getElementById(
          "backButton"
        )
        .style.visibility =
        currentQuestion === 0
          ? "hidden"
          : "visible";



      /* 선택지 생성 */

      const answerList =
        document
          .getElementById(
            "answerList"
          );


      answerList.innerHTML = "";


      Object
        .entries(
          question.answers
        )
        .forEach(
          function(entry) {

            const type =
              entry[0];

            const text =
              entry[1];


            const button =
              document
                .createElement(
                  "button"
                );


            button.type =
              "button";


            button.className =
              "answer-btn";


            button.innerHTML =

              '<span class="answer-letter">' +

              type +

              '</span>' +

              '<span>' +

              text +

              '</span>';



            button.addEventListener(
              "click",
              function() {


                answers[
                  currentQuestion
                ] =
                  type;



                if (
                  currentQuestion
                  <
                  QUESTIONS.length - 1
                ) {

                  currentQuestion++;

                  renderQuestion();

                }

                else {

                  showResult();

                }

              }
            );


            answerList
              .appendChild(
                button
              );

          }
        );

    }



    /* =========================
       이전 질문
    ========================== */

    function goBack() {

      if (
        currentQuestion > 0
      ) {

        currentQuestion--;

        renderQuestion();

      }

    }



    /* =========================
       결과 계산
    ========================== */

    function calculateResult() {

      const score = {

        A: 0,
        B: 0,
        C: 0,
        D: 0,
        E: 0

      };


      answers.forEach(
        function(answer) {

          if (answer) {

            score[answer]++;

          }

        }
      );



      const maxScore =
        Math.max(
          ...Object.values(
            score
          )
        );



      const tied =
        Object
          .keys(score)
          .filter(
            function(type) {

              return (
                score[type]
                ===
                maxScore
              );

            }
          );



      /* 한 유형이 가장 높으면 바로 결과 */

      if (
        tied.length === 1
      ) {

        return tied[0];

      }



      /*
        동점 처리

        1순위 : Q3 선택
        2순위 : Q1 선택
      */


      if (
        tied.includes(
          answers[2]
        )
      ) {

        return answers[2];

      }


      if (
        tied.includes(
          answers[0]
        )
      ) {

        return answers[0];

      }


      return tied[0];

    }



    /* =========================
       결과 출력
    ========================== */

    function showResult() {

      const resultType =
        calculateResult();


      const result =
        TYPES[
          resultType
        ];



      /* 아이콘 */

      const resultIcon =
        document
          .getElementById(
            "resultIcon"
          );


      resultIcon.textContent =
        result.icon;


      resultIcon.style.background =
        result.soft;



      /* 유형명 */

      const resultTitle =
        document
          .getElementById(
            "resultTitle"
          );


      resultTitle.textContent =
        result.title;


      resultTitle.style.color =
        result.color;



      /* 이름 */

      const resultLabel =
        document
          .getElementById(
            "resultLabel"
          );


      if (userName) {

        resultLabel.textContent =
          userName +
          "님의 봉사 성향은?";

      }

      else {

        resultLabel.textContent =
          "나의 봉사 성향은?";

      }


      resultLabel.style.color =
        result.color;



      /* 한 줄 설명 */

      document
        .getElementById(
          "resultTagline"
        )
        .textContent =
        result.tagline;



      /* 상세 설명 */

      document
        .getElementById(
          "resultDescription"
        )
        .textContent =
        result.description;



      /* 결과 카드 색상 */

      document
        .getElementById(
          "resultCard"
        )
        .style.borderColor =
        result.border;



      /* 키워드 */

      const keywordList =
        document
          .getElementById(
            "keywordList"
          );


      keywordList.innerHTML = "";


      result.keywords.forEach(
        function(keyword) {

          const tag =
            document
              .createElement(
                "span"
              );


          tag.className =
            "tag";


          tag.textContent =
            keyword;


          tag.style.background =
            result.soft;


          tag.style.color =
            result.color;


          keywordList
            .appendChild(
              tag
            );

        }
      );



      /* 추천 봉사 */

      const recommendList =
        document
          .getElementById(
            "recommendList"
          );


      recommendList.innerHTML = "";


      result.recommends.forEach(
        function(item) {

          const tag =
            document
              .createElement(
                "span"
              );


          tag.className =
            "tag";


          tag.textContent =
            item;


          tag.style.background =
            result.soft;


          tag.style.color =
            result.color;


          recommendList
            .appendChild(
              tag
            );

        }
      );



      /* 결과 메시지 */

      document
        .getElementById(
          "resultMessage"
        )
        .textContent =
        "“" +
        result.message +
        "”";



      document
        .getElementById(
          "shareMessage"
        )
        .textContent = "";



      showScreen(
        "resultScreen"
      );

    }



    /* =========================
       다시 테스트
    ========================== */

    function restartTest() {

      currentQuestion = 0;


      answers =
        new Array(
          QUESTIONS.length
        ).fill(null);


      userName = "";


      document
        .getElementById(
          "nameInput"
        )
        .value = "";


      showScreen(
        "startScreen"
      );

    }



    /* =========================
       결과 공유
    ========================== */

    async function shareResult() {

      const resultType =
        calculateResult();


      const result =
        TYPES[
          resultType
        ];


      let shareText = "";


      if (userName) {

        shareText +=
          userName +
          "님의 ";

      }

      else {

        shareText +=
          "나의 ";

      }


      shareText +=
        "봉사 성향은 " +
        result.icon +
        " " +
        result.title +
        "!\n\n" +
        result.message +
        "\n\n" +
        window.location.href;



      /* 모바일 기본 공유 기능 */

      if (
        navigator.share
      ) {

        try {

          await navigator.share({

            title:
              "나의 봉사 성향 테스트",

            text:
              shareText

          });


          document
            .getElementById(
              "shareMessage"
            )
            .textContent =
            "결과를 공유했습니다.";

        }

        catch (error) {

          /*
            사용자가 공유창을
            닫은 경우는 아무것도 하지 않음
          */

        }

      }


      /* 공유 기능이 없는 브라우저 */

      else {

        try {

          await navigator
            .clipboard
            .writeText(
              shareText
            );


          document
            .getElementById(
              "shareMessage"
            )
            .textContent =
            "결과와 테스트 링크를 복사했습니다.";

        }

        catch (error) {

          document
            .getElementById(
              "shareMessage"
            )
            .textContent =
            "주소창의 링크를 복사해주세요.";

        }

      }

    }



    /* =========================
       이름 입력 후 Enter
    ========================== */

    document
      .getElementById(
        "nameInput"
      )
      .addEventListener(
        "keydown",
        function(event) {

          if (
            event.key === "Enter"
          ) {

            startTest();

          }

        }
      );

  </script>

</body>
</html>
