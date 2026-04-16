<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>콘텐츠 아이디어 메이커</title>
    <style>
      * { box-sizing: border-box; }
      body {
        margin: 0;
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
        background: #f8fafc;
        color: #0f172a;
      }
      .wrap {
        max-width: 1100px;
        margin: 0 auto;
        padding: 40px 20px;
      }
      h1 {
        font-size: 40px;
        margin: 0 0 12px;
      }
      .lead {
        color: #475569;
        font-size: 18px;
        line-height: 1.6;
        max-width: 760px;
        margin-bottom: 28px;
      }
      .grid {
        display: grid;
        grid-template-columns: 1fr 1.1fr;
        gap: 24px;
      }
      .card {
        background: white;
        border: 1px solid #e2e8f0;
        border-radius: 24px;
        padding: 24px;
        box-shadow: 0 2px 10px rgba(15, 23, 42, 0.04);
      }
      h2 {
        margin-top: 0;
        margin-bottom: 20px;
        font-size: 24px;
      }
      label {
        display: block;
        margin-bottom: 8px;
        font-size: 14px;
        font-weight: 600;
        color: #334155;
      }
      .field { margin-bottom: 18px; }
      input {
        width: 100%;
        padding: 14px 16px;
        border-radius: 16px;
        border: 1px solid #cbd5e1;
        font-size: 16px;
      }
      input:focus {
        outline: 2px solid #cbd5e1;
        border-color: #94a3b8;
      }
      button {
        width: 100%;
        border: 0;
        border-radius: 16px;
        padding: 15px 18px;
        background: #0f172a;
        color: white;
        font-size: 16px;
        font-weight: 700;
        cursor: pointer;
      }
      button:hover { opacity: 0.92; }
      .placeholder {
        min-height: 520px;
        display: flex;
        align-items: center;
        justify-content: center;
        border: 1px dashed #cbd5e1;
        border-radius: 18px;
        background: #f8fafc;
        color: #64748b;
        text-align: center;
        line-height: 1.7;
        padding: 24px;
      }
      .section { margin-bottom: 22px; }
      .label-small {
        color: #64748b;
        font-size: 14px;
        margin-bottom: 8px;
      }
      .title-box {
        background: #f8fafc;
        border: 1px solid #e2e8f0;
        border-radius: 18px;
        padding: 18px;
      }
      .title-box h3 {
        margin: 0;
        font-size: 30px;
        line-height: 1.35;
      }
      .result-text {
        color: #334155;
        line-height: 1.7;
      }
      .list-item {
        border: 1px solid #e2e8f0;
        border-radius: 14px;
        padding: 13px 14px;
        margin-bottom: 10px;
        color: #334155;
        background: white;
      }
      .tag-wrap {
        display: flex;
        gap: 8px;
        flex-wrap: wrap;
      }
      .tag {
        border: 1px solid #cbd5e1;
        background: #f8fafc;
        border-radius: 999px;
        padding: 8px 12px;
        font-size: 14px;
        color: #334155;
      }
      .compare-box {
        margin-top: 28px;
        border: 1px solid #e2e8f0;
        background: white;
        border-radius: 20px;
        padding: 18px 20px;
        color: #475569;
        line-height: 1.7;
      }
      @media (max-width: 900px) {
        .grid { grid-template-columns: 1fr; }
        h1 { font-size: 32px; }
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <h1>콘텐츠 아이디어 메이커</h1>
      <p class="lead">
        주제, 타깃, 톤을 입력하면 간단한 콘텐츠 기획 초안을 바로 만들어보는 단일 HTML 버전이에요.
      </p>

      <div class="grid">
        <div class="card">
          <h2>입력</h2>

          <div class="field">
            <label for="topic">주제</label>
            <input id="topic" placeholder="예: 초등 영어 학습, AI 독서 습관, 학부모 가이드" />
          </div>

          <div class="field">
            <label for="target">타깃</label>
            <input id="target" placeholder="예: 초등 학부모, 30대 직장인, 중학생" />
          </div>

          <div class="field">
            <label for="tone">톤</label>
            <input id="tone" value="친근하고 전문적인" placeholder="예: 친근한, 전문적인, 감성적인" />
          </div>

          <button id="generateBtn">아이디어 초안 만들기</button>
        </div>

        <div class="card">
          <h2>결과</h2>
          <div id="resultArea" class="placeholder">
            입력값을 넣고<br />
            <strong>아이디어 초안 만들기</strong> 버튼을 눌러보세요.
          </div>
        </div>
      </div>

      <div class="compare-box">
        이 버전은 HTML/CSS/JS 한 파일로 되어 있어서 GitHub Pages에 올리기 쉽고, 구조를 이해하기도 쉬워요.
      </div>
    </div>

    <script>
      function buildIdeaDraft(topic, target, tone) {
        const cleanTopic = (topic || '').trim() || '새로운 교육 콘텐츠';
        const cleanTarget = (target || '').trim() || '학부모와 초등 학습자';
        const cleanTone = (tone || '').trim() || '친근하고 전문적인';

        return {
          title: `${cleanTarget}을 위한 ${cleanTopic} 콘텐츠`,
          summary: `${cleanTarget}이 흥미를 느끼고 바로 이해할 수 있도록, ${cleanTone} 톤으로 ${cleanTopic}를 풀어낸 콘텐츠 아이디어입니다.`,
          concept: `${cleanTopic}를 어렵게 설명하지 않고, 실제 상황과 가까운 예시로 연결해 이해와 공감을 동시에 얻는 방향입니다.`,
          hooks: [
            `${cleanTarget}이 가장 자주 겪는 고민에서 시작하기`,
            `${cleanTopic}를 3초 안에 이해되는 한 문장으로 요약하기`,
            `${cleanTone} 분위기로 부담 없이 읽히는 구성 만들기`
          ],
          format: [
            '카드뉴스형 요약 콘텐츠',
            '짧은 블로그/아티클 초안',
            'SNS 업로드용 짧은 카피 세트'
          ],
          message: `${cleanTopic}는 어렵거나 멀리 있는 이야기가 아니라, ${cleanTarget}의 일상에 바로 연결될 수 있는 가치라는 점을 강조합니다.`,
          cta: `${cleanTarget}이 바로 반응할 수 있도록 ‘지금 적용해보기’, ‘체크리스트 받아보기’, ‘간단히 비교해보기’ 같은 행동 유도를 넣습니다.`
        };
      }

      function renderResult(result) {
        return `
          <div class="section">
            <div class="label-small">제목</div>
            <div class="title-box"><h3>${result.title}</h3></div>
          </div>

          <div class="section">
            <div class="label-small">콘텐츠 요약</div>
            <div class="result-text">${result.summary}</div>
          </div>

          <div class="section">
            <div class="label-small">핵심 콘셉트</div>
            <div class="result-text">${result.concept}</div>
          </div>

          <div class="section">
            <div class="label-small">오프닝 훅 아이디어</div>
            ${result.hooks.map(item => `<div class="list-item">${item}</div>`).join('')}
          </div>

          <div class="section">
            <div class="label-small">추천 포맷</div>
            <div class="tag-wrap">${result.format.map(item => `<span class="tag">${item}</span>`).join('')}</div>
          </div>

          <div class="section">
            <div class="label-small">핵심 메시지</div>
            <div class="result-text">${result.message}</div>
          </div>

          <div class="section">
            <div class="label-small">CTA 제안</div>
            <div class="result-text">${result.cta}</div>
          </div>
        `;
      }

      function runTests() {
        const tests = [
          {
            name: '빈 입력이면 기본값을 사용한다',
            run: () => {
              const r = buildIdeaDraft('', '', '');
              return r.title.includes('새로운 교육 콘텐츠') && r.title.includes('학부모와 초등 학습자');
            }
          },
          {
            name: '입력값이 반영된다',
            run: () => {
              const r = buildIdeaDraft('AI 독서 습관', '초등 학부모', '신뢰감 있는');
              return r.summary.includes('신뢰감 있는') && r.title === '초등 학부모을 위한 AI 독서 습관 콘텐츠';
            }
          },
          {
            name: '공백을 제거한다',
            run: () => {
              const r = buildIdeaDraft('  학부모 가이드 ', ' 초등 부모 ', ' 친근한 ');
              return r.title === '초등 부모을 위한 학부모 가이드 콘텐츠';
            }
          }
        ];

        console.log('테스트 결과:', tests.map(test => ({ name: test.name, passed: test.run() })));
      }

      document.getElementById('generateBtn').addEventListener('click', function () {
        const topic = document.getElementById('topic').value;
        const target = document.getElementById('target').value;
        const tone = document.getElementById('tone').value;
        const result = buildIdeaDraft(topic, target, tone);
        document.getElementById('resultArea').className = '';
        document.getElementById('resultArea').innerHTML = renderResult(result);
      });

      runTests();
    </script>
  </body>
</html>

