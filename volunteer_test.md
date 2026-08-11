<나의 봉사 성향 테스트>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="theme-color" content="#3f9f7a" />
  <title>나의 봉사 성향 테스트</title>

  <style>
    * {
      box-sizing: border-box;
    }

    :root {
      --text: #203a50;
      --subtext: #6f7d87;
      --line: #e3e9ed;
      --bg: #eef8f4;
      --green: #379a74;
      --green2: #5db88f;
      --blue: #257ed1;
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
        radial-gradient(circle at 10% 10%, rgba(85, 188, 146, 0.14), transparent 25%),
        radial-gradient(circle at 90% 5%, rgba(116, 190, 255, 0.12), transparent 25%),
        #eef8f4;
    }

    button,
    input {
      font: inherit;
    }

    button {
      cursor: pointer;
    }

    .container {
      width: min(92%, 680px);
      min-height: 100vh;
      margin: 0 auto;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 24px 0;
    }

    .screen {
      display: none;
      width: 100%;
    }

    .screen.active {
      display: block;
      animation: fadeIn 0.28s ease;
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
      background: white;
      border-radius: 24px;
      overflow: hidden;
      box-shadow: 0 18px 50px rgba(46, 86, 72, 0.10);
    }

    /* =========================
       시작 화면
    ========================= */

    .start-hero {
      padding: 34px 26px 30px;
      text-align: center;
      background:
        linear-gradient(
          135deg,
          #379a74,
          #5bb68f
        );
      color: white;
    }

    .start-mini-title {
      font-size: 13px;
      font-weight: 900;
      margin-bottom: 18px;
    }

    .start-heart {
      font-size: 42px;
      margin-bottom: 12px;
    }

    .start-title {
      margin: 0;
      font-size: clamp(28px, 7vw, 38px);
      font-weight: 900;
      letter-spacing: -1.5px;
    }

    .start-description {
      margin: 13px auto 0;
      max-width: 470px;
      font-size: 14px;
      line-height: 1.8;
      opacity: 0.96;
    }

    .start-content {
      padding: 26px 24px 24px;
    }

    .section-title {
      margin: 0 0 12px;
      color: #246e56;
      font-size: 15px;
      font-weight: 900;
    }

    .type-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 9px;
      margin-bottom: 22px;
    }

    .type-item {
      padding: 11px 13px;
      border-radius: 12px;
      background: #eaf7f1;
      color: #287258;
      font-size: 13px;
      font-weight: 800;
    }

    .type-item:last-child {
      grid-column: 1 / -1;
    }

    .guide-box {
      margin-bottom: 20px;
      padding: 17px 15px;
      border: 1px solid #efc66d;
      border-radius: 14px;
      background: #fffaf0;
      color: #856523;
      text-align: center;
      font-size: 13px;
      line-height: 1.75;
    }

    .guide-box strong {
      font-weight: 900;
    }

    .name-label {
      display: block;
      margin-bottom: 7px;
      color: #306d58;
      font-size: 14px;
      font-weight: 900;
    }

    .optional {
      color: #899d95;
      font-weight: 500;
    }

    .name-input {
      width: 100%;
      height: 50px;
      padding: 0 15px;
      border: 1px solid #b9ddce;
      border-radius: 12px;
      outline: none;
      background: #f7fcfa;
    }

    .name-input:focus {
      border-color: #3a9c77;
      box-shadow: 0 0 0 3px rgba(58, 156, 119, 0.10);
    }

    .start-btn {
      width: 100%;
      height: 54px;
      margin-top: 13px;
      border: none;
      border-radius: 12px;
      background: #257ed1;
      color: white;
      font-size: 15px;
      font-weight: 900;
      box-shadow: 0 7px 18px rgba(37, 126, 209, 0.18);
    }

    .start-btn:hover {
      background: #1f72bf;
    }

    .center-btn {
      width: 100%;
      height: 50px;
      margin-top: 9px;
      border: none;
      border-radius: 12px;
      background: #379a74;
      color: white;
      font-size: 14px;
      font-weight: 900;
    }

    .notice-box {
      margin-top: 12px;
      padding: 13px;
      border: 1px dashed #9acbb8;
      border-radius: 12px;
      color: #6c8279;
      text-align: center;
      font-size: 12px;
      line-height: 1.6;
    }

    .footer {
      padding: 15px;
      text-align: center;
      color: #91a099;
      font-size: 11px;
    }

    /* =========================
       질문 화면
    ========================= */

    .quiz-card {
      padding: 24px;
    }

    .quiz-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .back-btn {
      border: none;
      background: transparent;
      color: #6f7b84;
      font-size: 14px;
      font-weight: 800;
      padding: 6px 0;
    }

    .counter {
      color: #77838c;
      font-size: 14px;
      font-weight: 800;
    }

    .progress {
      width: 100%;
      height: 8px;
      margin-top: 14px;
      border-radius: 999px;
      overflow: hidden;
      background: #e9eef1;
    }

    .progress-bar {
      height: 100%;
      width: 16.67%;
      border-radius: inherit;
      background: linear-gradient(90deg, #379a74, #69c49d);
      transition: width 0.25s ease;
    }

    .question-area {
      padding: 31px 2px 22px;
    }

    .question-number {
      margin: 0 0 8px;
      color: #3b9874;
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
      min-height: 64px;
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 14px;
      border: 1.5px solid #e1e7eb;
      border-radius: 15px;
      background: white;
      color: #294156;
      text-align: left;
      line-height: 1.5;
      transition: 0.15s ease;
    }

    .answer-btn:hover {
      border-color: #79bea3;
      background: #f5fbf8;
      transform: translateY(-1px);
    }

    .answer-letter {
      flex: 0 0 34px;
      width: 34px;
      height: 34px;
      display: grid;
      place-items: center;
      border-radius: 50%;
      background: #eaf7f1;
      color: #2f8b69;
      font-weight: 900;
    }

    /* =========================
       결과 화면
    ========================= */

    .result-wrap {
      padding: 24px;
    }

    .result-top {
      margin-bottom: 14px;
      text-align: center;
      color: #718078;
      font-size: 14px;
      font-weight: 900;
    }

    .result-card {
      padding: 28px;
      border: 2px solid #ffc6d2;
      border-radius: 22px;
      background: white;
    }

    .result-icon {
      width: 68px;
      height: 68px;
      display: grid;
      place-items: center;
      border-radius: 20px;
      font-size: 34px;
    }

    .result-label {
      margin: 22px 0 5px;
      font-size: 14px;
      font-weight: 900;
    }

    .result-title {
      margin: 0;
      font-size: clamp(31px, 7vw, 42px);
      letter-spacing: -1.8px;
    }

    .result-tagline {
      margin: 12px 0 0;
      font-size: 17px;
      font-weight: 900;
      line-height: 1.6;
    }

    .result-description {
      margin: 13px 0 0;
      color: #68767e;
      font-size: 14px;
      line-height: 1.8;
    }

    .result-section {
      margin-top: 21px;
      padding-top: 17px;
      border-top: 1px dashed #d9e0e3;
    }

    .result-section h3 {
      margin: 0 0 11px;
      font-size: 15px;
    }

    .tag-box {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }

    .tag {
      display: inline-block;
      padding: 8px 10px;
      border-radius: 999px;
      font-size: 13px;
      font-weight: 800;
    }

    .result-message {
      margin-top: 22px;
      padding: 15px;
      border-radius: 13px;
      background: #f8faf9;
      font-size: 14px;
      font-weight: 900;
      line-height: 1.65;
    }

    .result-buttons {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 9px;
      margin-top: 14px;
    }

    .share-btn,
    .restart-btn {
      min-height: 52px;
      border: none;
      border-radius: 12px;
      font-size: 14px;
      font-weight: 900;
    }

    .share-btn {
      background: #eaf7f1;
      color: #2d7b60;
    }

    .restart-btn {
      background: #379a74;
      color: white;
    }

    .share-status {
      min-height: 19px;
      margin: 9px 0 0;
      text-align: center;
      color: #74837b;
      font-size: 12px;
    }

    @media (max-width: 520px) {
      .container {
        width: calc(100% - 18px);
        padding: 12px 0;
      }

      .start-hero {
        padding: 30px 18px 26px;
      }

      .start-content {
        padding: 22px 16px;
      }

      .type-grid {
        grid-template-columns: 1fr;
      }

      .type-item:last-child {
        grid-column: auto;
      }

      .quiz-card,
      .result-wrap {
        padding: 18px 15px;
      }

      .result-card {
        padding: 23px 18px;
      }

      .result-buttons {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>

<body>

<main class="container">

  <!-- 시작 화면 -->
  <section id="startScreen" class="screen active">

    <div class="card">

      <div class="start-hero">

        <div class="start-mini-title">
          🌼 나의 봉사 성향
        </div>

        <div class="start-heart">
          💚
        </div>

        <h1 class="start-title">
          나의 봉사 성향 테스트
        </h1>

        <p class="start-description">
          나는 어떤 봉사와 가장 잘 맞을까요?<br>
          6개의 질문을 통해 나에게 어울리는
          봉사 성향을 찾아보세요!
        </p>

      </div>


      <div class="start-content">

        <h2 class="section-title">
          🌱 나는 어떤 봉사자일까요?
        </h2>

        <div class="type-grid">

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


        <div class="guide-box">
          어떤 성향이 가장 중요한 것은 아니에요.<br>
          <strong>나눔을 시작하는 마음</strong>이 가장 중요합니다.
          <br><br>
          지금부터 나에게 맞는 봉사 성향을 찾아볼까요?
        </div>


        <label for="nameInput" class="name-label">
          이름
          <span class="optional">(선택)</span>
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
          class="start-btn"
          type="button"
          onclick="startTest()"
        >
          나의 봉사 성향 알아보기
        </button>


        <button
          class="center-btn"
          type="button"
          onclick="window.open('https://www.bsjingu1365.or.kr/', '_blank')"
        >
          부산진구자원봉사센터 홈페이지 바로가기
        </button>


        <div class="notice-box">
          💡 6개의 간단한 질문에 답하면<br>
          나에게 어울리는 봉사 유형과 추천 활동을 확인할 수 있어요.
        </div>

      </div>


      <div class="footer">
        부산진구자원봉사센터
      </div>

    </div>

  </section>


  <!-- 질문 화면 -->
  <section id="quizScreen" class="screen">

    <div class="card quiz-card">

      <div class="quiz-header">

        <button
          id="backBtn"
          class="back-btn"
          type="button"
          onclick="goBack()"
        >
          ← 이전
        </button>

        <div class="counter">
          <span id="currentQuestion">1</span>
          /
          <span id="totalQuestion">6</span>
        </div>

      </div>


      <div class="progress">
        <div
          id="progressBar"
          class="progress-bar"
        ></div>
      </div>


      <div class="question-area">

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


  <!-- 결과 화면 -->
  <section id="resultScreen" class="screen">

    <div class="card result-wrap">

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
            추천 봉사활동
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
          class="share-btn"
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
          테스트 다시 하기
        </button>

      </div>

      <p
        id="shareStatus"
        class="share-status"
      ></p>

    </div>

  </section>

</main>


<script>

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
    border: "#FFC6D2"
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
    border: "#ACD5F4"
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



const QUESTIONS = [

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


let currentQuestion = 0;

let answers =
  new Array(
    QUESTIONS.length
  ).fill(null);

let userName = "";


function showScreen(id) {

  document
    .querySelectorAll(".screen")
    .forEach(function(screen) {
      screen.classList.remove("active");
    });

  document
    .getElementById(id)
    .classList.add("active");

  window.scrollTo({
    top: 0,
    behavior: "smooth"
  });

}


function startTest() {

  userName =
    document
      .getElementById("nameInput")
      .value
      .trim();

  currentQuestion = 0;

  answers =
    new Array(
      QUESTIONS.length
    ).fill(null);

  renderQuestion();

  showScreen("quizScreen");

}


function renderQuestion() {

  const question =
    QUESTIONS[currentQuestion];

  document
    .getElementById("currentQuestion")
    .textContent =
    currentQuestion + 1;

  document
    .getElementById("totalQuestion")
    .textContent =
    QUESTIONS.length;

  document
    .getElementById("questionNumber")
    .textContent =
    "QUESTION " +
    String(
      currentQuestion + 1
    ).padStart(2, "0");

  document
    .getElementById("questionText")
    .textContent =
    question.text;


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
    .getElementById("progressBar")
    .style.width =
    progress + "%";


  document
    .getElementById("backBtn")
    .style.visibility =
    currentQuestion === 0
      ? "hidden"
      : "visible";


  const answerList =
    document
      .getElementById("answerList");

  answerList.innerHTML = "";


  Object
    .entries(question.answers)
    .forEach(function([type, text]) {

      const button =
        document.createElement("button");

      button.type = "button";
      button.className = "answer-btn";

      button.innerHTML = `
        <span class="answer-letter">
          ${type}
        </span>

        <span>
          ${text}
        </span>
      `;


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
        .appendChild(button);

    });

}


function goBack() {

  if (
    currentQuestion > 0
  ) {

    currentQuestion--;

    renderQuestion();

  }

}


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
      ...Object.values(score)
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


  if (
    tied.length === 1
  ) {
    return tied[0];
  }


  /*
    동점일 경우

    1순위 Q3
    2순위 Q1
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


function showResult() {

  const type =
    calculateResult();

  const result =
    TYPES[type];


  const icon =
    document
      .getElementById("resultIcon");

  icon.textContent =
    result.icon;

  icon.style.background =
    result.soft;


  const label =
    document
      .getElementById("resultLabel");

  if (userName) {

    label.textContent =
      userName +
      "님의 봉사 성향은?";

  }

  else {

    label.textContent =
      "나의 봉사 성향은?";

  }

  label.style.color =
    result.color;


  const title =
    document
      .getElementById("resultTitle");

  title.textContent =
    result.title;

  title.style.color =
    result.color;


  document
    .getElementById("resultTagline")
    .textContent =
    result.tagline;


  document
    .getElementById("resultDescription")
    .textContent =
    result.description;


  document
    .getElementById("resultCard")
    .style.borderColor =
    result.border;


  const keywordList =
    document
      .getElementById("keywordList");

  keywordList.innerHTML = "";


  result.keywords.forEach(
    function(keyword) {

      const tag =
        document.createElement("span");

      tag.className = "tag";
      tag.textContent = keyword;

      tag.style.background =
        result.soft;

      tag.style.color =
        result.color;

      keywordList
        .appendChild(tag);

    }
  );


  const recommendList =
    document
      .getElementById("recommendList");

  recommendList.innerHTML = "";


  result.recommends.forEach(
    function(item) {

      const tag =
        document.createElement("span");

      tag.className = "tag";
      tag.textContent = item;

      tag.style.background =
        result.soft;

      tag.style.color =
        result.color;

      recommendList
        .appendChild(tag);

    }
  );


  document
    .getElementById("resultMessage")
    .textContent =
    "“" +
    result.message +
    "”";


  document
    .getElementById("shareStatus")
    .textContent = "";


  showScreen("resultScreen");

}


function restartTest() {

  currentQuestion = 0;

  answers =
    new Array(
      QUESTIONS.length
    ).fill(null);

  userName = "";

  document
    .getElementById("nameInput")
    .value = "";

  showScreen("startScreen");

}


async function shareResult() {

  const type =
    calculateResult();

  const result =
    TYPES[type];

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

    }

    catch (error) {}

  }

  else {

    try {

      await navigator
        .clipboard
        .writeText(
          shareText
        );

      document
        .getElementById("shareStatus")
        .textContent =
        "결과와 테스트 링크를 복사했습니다.";

    }

    catch (error) {

      document
        .getElementById("shareStatus")
        .textContent =
        "주소창의 링크를 복사해주세요.";

    }

  }

}


document
  .getElementById("nameInput")
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
