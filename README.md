<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>社团智配 · 找到属于你的圈子</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+SC:wght@400;600&family=Noto+Sans+SC:wght@300;400;500;700&display=swap" rel="stylesheet">
<style>
  :root {
    --teal: #1D9E75;
    --teal-light: #E1F5EE;
    --teal-mid: #5DCAA5;
    --teal-dark: #0F6E56;
    --coral: #D85A30;
    --coral-light: #FAECE7;
    --amber: #BA7517;
    --amber-light: #FAEEDA;
    --purple: #534AB7;
    --purple-light: #EEEDFE;
    --gray-50: #F8F7F4;
    --gray-100: #EDEBE4;
    --gray-300: #C4C2B8;
    --gray-500: #888780;
    --gray-700: #444441;
    --gray-900: #1A1A18;
    --radius: 12px;
    --radius-sm: 8px;
    --shadow: 0 1px 3px rgba(0,0,0,0.08), 0 1px 2px rgba(0,0,0,0.05);
    --shadow-md: 0 4px 12px rgba(0,0,0,0.1);
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Noto Sans SC', sans-serif;
    background: var(--gray-50);
    color: var(--gray-900);
    min-height: 100vh;
    font-size: 15px;
    line-height: 1.6;
  }

  .app { max-width: 680px; margin: 0 auto; padding: 0 16px 80px; }

  /* NAV */
  .nav {
    display: flex; align-items: center; gap: 10px;
    padding: 20px 0 16px;
    border-bottom: 1px solid var(--gray-100);
    margin-bottom: 32px;
  }
  .logo-mark {
    width: 32px; height: 32px; border-radius: 8px;
    background: var(--teal);
    display: flex; align-items: center; justify-content: center;
    color: white; font-size: 16px; font-weight: 700;
  }
  .logo-text { font-size: 18px; font-weight: 700; color: var(--gray-900); letter-spacing: -0.3px; }
  .logo-sub { font-size: 12px; color: var(--gray-500); margin-left: auto; }

  /* SCREENS */
  .screen { display: none; animation: fadeIn 0.3s ease; }
  .screen.active { display: block; }
  @keyframes fadeIn { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: translateY(0); } }

  /* HERO */
  .hero-badge {
    display: inline-flex; align-items: center; gap: 6px;
    background: var(--teal-light); color: var(--teal-dark);
    font-size: 12px; font-weight: 500;
    padding: 5px 12px; border-radius: 20px;
    margin-bottom: 20px;
  }
  .hero-badge::before { content: ''; width: 6px; height: 6px; border-radius: 50%; background: var(--teal); }
  .hero-title {
    font-family: 'Noto Serif SC', serif;
    font-size: 36px; font-weight: 600;
    line-height: 1.25; letter-spacing: -0.5px;
    color: var(--gray-900);
    margin-bottom: 14px;
  }
  .hero-title span { color: var(--teal); }
  .hero-desc { font-size: 15px; color: var(--gray-500); line-height: 1.7; margin-bottom: 32px; max-width: 480px; }
  .hero-stats {
    display: flex; gap: 24px; margin-bottom: 36px;
    padding: 20px 0; border-top: 1px solid var(--gray-100); border-bottom: 1px solid var(--gray-100);
  }
  .stat-item { display: flex; flex-direction: column; gap: 2px; }
  .stat-num { font-size: 22px; font-weight: 700; color: var(--gray-900); }
  .stat-label { font-size: 12px; color: var(--gray-500); }
  .hero-img-row {
    display: flex; gap: 10px; margin-bottom: 36px; overflow-x: auto;
  }
  .club-pill {
    flex-shrink: 0;
    display: flex; align-items: center; gap: 8px;
    background: white; border: 1px solid var(--gray-100);
    padding: 10px 14px; border-radius: 100px;
    font-size: 13px; font-weight: 500;
    box-shadow: var(--shadow);
  }
  .club-pill-icon { font-size: 18px; }

  /* BUTTONS */
  .btn {
    display: inline-flex; align-items: center; justify-content: center; gap: 8px;
    padding: 14px 28px; border-radius: var(--radius-sm);
    font-size: 15px; font-weight: 500;
    cursor: pointer; border: none; transition: all 0.15s;
    text-decoration: none; font-family: inherit;
  }
  .btn-primary {
    background: var(--teal); color: white;
    width: 100%;
  }
  .btn-primary:hover { background: var(--teal-dark); }
  .btn-secondary {
    background: white; color: var(--gray-700);
    border: 1px solid var(--gray-300);
  }
  .btn-secondary:hover { background: var(--gray-50); }
  .btn-sm { padding: 8px 18px; font-size: 13px; }

  /* PROGRESS */
  .progress-bar { height: 3px; background: var(--gray-100); border-radius: 2px; margin-bottom: 28px; }
  .progress-fill { height: 100%; background: var(--teal); border-radius: 2px; transition: width 0.4s ease; }
  .step-label { font-size: 12px; color: var(--gray-500); margin-bottom: 8px; }

  /* QUIZ */
  .quiz-title { font-size: 22px; font-weight: 700; margin-bottom: 6px; line-height: 1.3; }
  .quiz-sub { font-size: 14px; color: var(--gray-500); margin-bottom: 24px; }

  .interest-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-bottom: 28px; }
  .interest-card {
    padding: 16px 12px; border-radius: var(--radius);
    border: 1.5px solid var(--gray-100); background: white;
    cursor: pointer; text-align: center; transition: all 0.15s;
    display: flex; flex-direction: column; align-items: center; gap: 8px;
  }
  .interest-card:hover { border-color: var(--teal-mid); }
  .interest-card.selected { border-color: var(--teal); background: var(--teal-light); }
  .interest-card .icon { font-size: 28px; }
  .interest-card .label { font-size: 13px; font-weight: 500; color: var(--gray-700); }
  .interest-card.selected .label { color: var(--teal-dark); }

  .option-list { display: flex; flex-direction: column; gap: 10px; margin-bottom: 28px; }
  .option-item {
    padding: 14px 16px; border-radius: var(--radius-sm);
    border: 1.5px solid var(--gray-100); background: white;
    cursor: pointer; transition: all 0.15s;
    display: flex; align-items: center; gap: 12px;
  }
  .option-item:hover { border-color: var(--teal-mid); }
  .option-item.selected { border-color: var(--teal); background: var(--teal-light); }
  .option-dot {
    width: 18px; height: 18px; border-radius: 50%;
    border: 2px solid var(--gray-300); flex-shrink: 0;
    transition: all 0.15s; display: flex; align-items: center; justify-content: center;
  }
  .option-item.selected .option-dot { border-color: var(--teal); background: var(--teal); }
  .option-dot::after { content: ''; width: 6px; height: 6px; border-radius: 50%; background: white; display: none; }
  .option-item.selected .option-dot::after { display: block; }
  .option-text { font-size: 14px; color: var(--gray-700); }
  .option-item.selected .option-text { color: var(--teal-dark); font-weight: 500; }

  .quiz-nav { display: flex; gap: 10px; }
  .quiz-nav .btn { flex: 1; }

  /* LOADING */
  .loading-screen { text-align: center; padding: 60px 20px; }
  .spinner {
    width: 48px; height: 48px; border-radius: 50%;
    border: 3px solid var(--gray-100);
    border-top-color: var(--teal);
    animation: spin 0.8s linear infinite;
    margin: 0 auto 24px;
  }
  @keyframes spin { to { transform: rotate(360deg); } }
  .loading-title { font-size: 20px; font-weight: 600; margin-bottom: 8px; }
  .loading-sub { font-size: 14px; color: var(--gray-500); }
  .loading-tips { margin-top: 32px; display: flex; flex-direction: column; gap: 10px; }
  .tip-item {
    display: flex; align-items: center; gap: 10px;
    background: white; border: 1px solid var(--gray-100);
    padding: 12px 14px; border-radius: var(--radius-sm);
    font-size: 13px; text-align: left;
  }
  .tip-dot { width: 8px; height: 8px; border-radius: 50%; background: var(--teal); flex-shrink: 0; }

  /* RESULTS */
  .results-header { margin-bottom: 24px; }
  .results-title { font-size: 22px; font-weight: 700; margin-bottom: 6px; }
  .results-sub { font-size: 14px; color: var(--gray-500); }
  .match-summary {
    background: var(--teal); color: white;
    border-radius: var(--radius); padding: 20px;
    display: flex; align-items: center; gap: 16px;
    margin-bottom: 24px;
  }
  .match-score-circle {
    width: 64px; height: 64px; border-radius: 50%;
    background: rgba(255,255,255,0.2);
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    flex-shrink: 0;
  }
  .match-score-num { font-size: 22px; font-weight: 700; }
  .match-score-unit { font-size: 10px; opacity: 0.8; }
  .match-summary-text h3 { font-size: 16px; font-weight: 600; margin-bottom: 4px; }
  .match-summary-text p { font-size: 13px; opacity: 0.85; line-height: 1.5; }

  .section-title { font-size: 13px; font-weight: 500; color: var(--gray-500); text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 14px; }

  .club-cards { display: flex; flex-direction: column; gap: 14px; margin-bottom: 32px; }
  .club-card {
    background: white; border: 1px solid var(--gray-100);
    border-radius: var(--radius); padding: 18px;
    cursor: pointer; transition: all 0.15s;
    box-shadow: var(--shadow);
  }
  .club-card:hover { border-color: var(--gray-300); box-shadow: var(--shadow-md); transform: translateY(-1px); }
  .club-card-top { display: flex; align-items: flex-start; gap: 14px; margin-bottom: 12px; }
  .club-avatar {
    width: 48px; height: 48px; border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
    font-size: 24px; flex-shrink: 0;
  }
  .club-card-info { flex: 1; min-width: 0; }
  .club-name { font-size: 16px; font-weight: 700; color: var(--gray-900); margin-bottom: 3px; }
  .club-category { font-size: 12px; color: var(--gray-500); }
  .match-badge {
    display: flex; align-items: center; gap: 4px;
    background: var(--teal-light); color: var(--teal-dark);
    font-size: 13px; font-weight: 600;
    padding: 5px 10px; border-radius: 20px; flex-shrink: 0;
  }
  .club-desc { font-size: 13px; color: var(--gray-500); line-height: 1.6; margin-bottom: 14px; }
  .club-tags { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 14px; }
  .tag {
    font-size: 11px; font-weight: 500;
    padding: 4px 10px; border-radius: 20px;
    background: var(--gray-100); color: var(--gray-700);
  }
  .club-meta { display: flex; gap: 16px; }
  .meta-item { display: flex; align-items: center; gap: 5px; font-size: 12px; color: var(--gray-500); }
  .meta-icon { font-size: 14px; }

  /* DETAIL */
  .detail-back {
    display: flex; align-items: center; gap: 6px;
    color: var(--teal); font-size: 14px; font-weight: 500;
    cursor: pointer; margin-bottom: 20px;
    background: none; border: none; font-family: inherit;
    padding: 0;
  }
  .detail-hero {
    background: white; border: 1px solid var(--gray-100);
    border-radius: var(--radius); padding: 24px;
    margin-bottom: 16px; box-shadow: var(--shadow);
  }
  .detail-top { display: flex; align-items: center; gap: 16px; margin-bottom: 16px; }
  .detail-avatar { width: 64px; height: 64px; border-radius: 16px; font-size: 32px; display: flex; align-items: center; justify-content: center; }
  .detail-name { font-size: 22px; font-weight: 700; margin-bottom: 4px; }
  .detail-sub { font-size: 13px; color: var(--gray-500); }
  .match-bar-row { display: flex; align-items: center; gap: 10px; margin-bottom: 20px; }
  .match-bar-label { font-size: 13px; color: var(--gray-500); min-width: 60px; }
  .match-bar { flex: 1; height: 8px; background: var(--gray-100); border-radius: 4px; overflow: hidden; }
  .match-bar-fill { height: 100%; background: var(--teal); border-radius: 4px; transition: width 1s ease; }
  .match-bar-pct { font-size: 14px; font-weight: 600; color: var(--teal); min-width: 36px; text-align: right; }
  .detail-stats {
    display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px;
    margin-bottom: 16px;
  }
  .detail-stat { text-align: center; background: var(--gray-50); border-radius: var(--radius-sm); padding: 12px 8px; }
  .detail-stat-num { font-size: 18px; font-weight: 700; color: var(--gray-900); }
  .detail-stat-label { font-size: 11px; color: var(--gray-500); margin-top: 2px; }
  .detail-section { background: white; border: 1px solid var(--gray-100); border-radius: var(--radius); padding: 20px; margin-bottom: 14px; }
  .detail-section h3 { font-size: 15px; font-weight: 700; margin-bottom: 12px; }
  .detail-section p { font-size: 14px; color: var(--gray-500); line-height: 1.7; }
  .activity-list { display: flex; flex-direction: column; gap: 10px; }
  .activity-item { display: flex; gap: 12px; }
  .activity-dot-col { display: flex; flex-direction: column; align-items: center; }
  .a-dot { width: 10px; height: 10px; border-radius: 50%; background: var(--teal); margin-top: 4px; flex-shrink: 0; }
  .a-line { width: 1px; background: var(--gray-100); flex: 1; margin-top: 4px; }
  .activity-content { padding-bottom: 10px; }
  .a-title { font-size: 14px; font-weight: 500; color: var(--gray-900); }
  .a-date { font-size: 12px; color: var(--gray-500); margin-top: 2px; }
  .apply-box {
    position: fixed; bottom: 0; left: 0; right: 0;
    background: white; border-top: 1px solid var(--gray-100);
    padding: 16px; display: none;
  }
  .apply-box.visible { display: block; }
  .apply-inner { max-width: 680px; margin: 0 auto; display: flex; gap: 10px; }

  /* TOAST */
  .toast {
    position: fixed; bottom: 100px; left: 50%; transform: translateX(-50%);
    background: var(--gray-900); color: white;
    padding: 12px 20px; border-radius: 100px;
    font-size: 14px; font-weight: 500;
    opacity: 0; pointer-events: none;
    transition: opacity 0.3s;
    white-space: nowrap; z-index: 100;
  }
  .toast.show { opacity: 1; }

  @media (max-width: 480px) {
    .interest-grid { grid-template-columns: repeat(2, 1fr); }
    .hero-title { font-size: 28px; }
    .detail-stats { grid-template-columns: repeat(3, 1fr); }
  }
</style>
</head>
<body>
<div class="app">
  <nav class="nav">
    <div class="logo-mark">社</div>
    <span class="logo-text">社团智配</span>
    <span class="logo-sub">AI驱动 · 精准匹配</span>
  </nav>

  <!-- SCREEN 1: HERO -->
  <div class="screen active" id="screen-hero">
    <div class="hero-badge">全新体验 · 2025 秋季招新</div>
    <h1 class="hero-title">找到<span>属于你</span>的<br>那个社团</h1>
    <p class="hero-desc">告别漫无目的地逛招新展台。3分钟完成兴趣测评，AI为你智能匹配最适合的社团，开启精彩的大学生活。</p>
    <div class="hero-img-row">
      <div class="club-pill"><span class="club-pill-icon">🎸</span>吉他社</div>
      <div class="club-pill"><span class="club-pill-icon">💻</span>编程协会</div>
      <div class="club-pill"><span class="club-pill-icon">🎨</span>绘画社</div>
      <div class="club-pill"><span class="club-pill-icon">🏀</span>篮球队</div>
      <div class="club-pill"><span class="club-pill-icon">📷</span>摄影社</div>
      <div class="club-pill"><span class="club-pill-icon">🌍</span>国际交流</div>
    </div>
    <div class="hero-stats">
      <div class="stat-item">
        <span class="stat-num">128+</span>
        <span class="stat-label">注册社团</span>
      </div>
      <div class="stat-item">
        <span class="stat-num">4,300+</span>
        <span class="stat-label">在校社员</span>
      </div>
      <div class="stat-item">
        <span class="stat-num">96%</span>
        <span class="stat-label">匹配满意度</span>
      </div>
    </div>
    <button class="btn btn-primary" onclick="goTo('screen-q1')">
      开始匹配测评 →
    </button>
  </div>

  <!-- SCREEN 2: Q1 兴趣选择 -->
  <div class="screen" id="screen-q1">
    <div class="step-label">第 1 步 / 共 3 步</div>
    <div class="progress-bar"><div class="progress-fill" style="width: 33%"></div></div>
    <h2 class="quiz-title">你对哪些领域感兴趣？</h2>
    <p class="quiz-sub">可以多选，选择你真正喜欢的领域</p>
    <div class="interest-grid">
      <div class="interest-card" onclick="toggleInterest(this, '科技编程')">
        <span class="icon">💻</span><span class="label">科技编程</span>
      </div>
      <div class="interest-card" onclick="toggleInterest(this, '音乐表演')">
        <span class="icon">🎵</span><span class="label">音乐表演</span>
      </div>
      <div class="interest-card" onclick="toggleInterest(this, '体育运动')">
        <span class="icon">⚽</span><span class="label">体育运动</span>
      </div>
      <div class="interest-card" onclick="toggleInterest(this, '艺术设计')">
        <span class="icon">🎨</span><span class="label">艺术设计</span>
      </div>
      <div class="interest-card" onclick="toggleInterest(this, '文学写作')">
        <span class="icon">📚</span><span class="label">文学写作</span>
      </div>
      <div class="interest-card" onclick="toggleInterest(this, '摄影影视')">
        <span class="icon">📷</span><span class="label">摄影影视</span>
      </div>
      <div class="interest-card" onclick="toggleInterest(this, '公益志愿')">
        <span class="icon">🤝</span><span class="label">公益志愿</span>
      </div>
      <div class="interest-card" onclick="toggleInterest(this, '创业商业')">
        <span class="icon">💡</span><span class="label">创业商业</span>
      </div>
      <div class="interest-card" onclick="toggleInterest(this, '国际交流')">
        <span class="icon">🌍</span><span class="label">国际交流</span>
      </div>
    </div>
    <div class="quiz-nav">
      <button class="btn btn-secondary" onclick="goTo('screen-hero')">返回</button>
      <button class="btn btn-primary" onclick="goToQ2()">下一步</button>
    </div>
  </div>

  <!-- SCREEN 3: Q2 性格 -->
  <div class="screen" id="screen-q2">
    <div class="step-label">第 2 步 / 共 3 步</div>
    <div class="progress-bar"><div class="progress-fill" style="width: 66%"></div></div>
    <h2 class="quiz-title">你更偏向哪种社团风格？</h2>
    <p class="quiz-sub">选择最接近你期望的社团氛围</p>
    <div class="option-list">
      <div class="option-item" onclick="selectOption(this, 'style')">
        <div class="option-dot"></div>
        <span class="option-text">🏆 竞技型 — 参加比赛、追求成绩、精英导向</span>
      </div>
      <div class="option-item" onclick="selectOption(this, 'style')">
        <div class="option-dot"></div>
        <span class="option-text">🎉 休闲型 — 轻松参与、结交朋友、放松减压</span>
      </div>
      <div class="option-item" onclick="selectOption(this, 'style')">
        <div class="option-dot"></div>
        <span class="option-text">📚 学习型 — 技能提升、专业发展、知识积累</span>
      </div>
      <div class="option-item" onclick="selectOption(this, 'style')">
        <div class="option-dot"></div>
        <span class="option-text">🌱 公益型 — 服务社会、传递温暖、积累经历</span>
      </div>
    </div>
    <div class="quiz-nav">
      <button class="btn btn-secondary" onclick="goTo('screen-q1')">返回</button>
      <button class="btn btn-primary" onclick="goToQ3()">下一步</button>
    </div>
  </div>

  <!-- SCREEN 4: Q3 时间 -->
  <div class="screen" id="screen-q3">
    <div class="step-label">第 3 步 / 共 3 步</div>
    <div class="progress-bar"><div class="progress-fill" style="width: 100%"></div></div>
    <h2 class="quiz-title">每周可以投入多少时间？</h2>
    <p class="quiz-sub">帮助我们匹配活动频率合适的社团</p>
    <div class="option-list">
      <div class="option-item" onclick="selectOption(this, 'time')">
        <div class="option-dot"></div>
        <span class="option-text">⏰ 1-2 小时 — 轻度参与，不影响学习</span>
      </div>
      <div class="option-item" onclick="selectOption(this, 'time')">
        <div class="option-dot"></div>
        <span class="option-text">⏰ 3-5 小时 — 适度投入，兼顾学业</span>
      </div>
      <div class="option-item" onclick="selectOption(this, 'time')">
        <div class="option-dot"></div>
        <span class="option-text">⏰ 5-10 小时 — 深度参与，认真对待</span>
      </div>
      <div class="option-item" onclick="selectOption(this, 'time')">
        <div class="option-dot"></div>
        <span class="option-text">⏰ 10小时以上 — 全力投入，视为第二课堂</span>
      </div>
    </div>
    <div class="quiz-nav">
      <button class="btn btn-secondary" onclick="goTo('screen-q2')">返回</button>
      <button class="btn btn-primary" onclick="startMatching()">开始智能匹配</button>
    </div>
  </div>

  <!-- SCREEN 5: LOADING -->
  <div class="screen" id="screen-loading">
    <div class="loading-screen">
      <div class="spinner"></div>
      <h2 class="loading-title">AI 正在为你匹配...</h2>
      <p class="loading-sub">分析你的兴趣画像，对比 128 个社团数据</p>
      <div class="loading-tips">
        <div class="tip-item"><div class="tip-dot"></div>分析兴趣标签与社团契合度</div>
        <div class="tip-item"><div class="tip-dot"></div>匹配社团活动频率与你的时间</div>
        <div class="tip-item"><div class="tip-dot"></div>计算综合匹配分数，排序推荐</div>
      </div>
    </div>
  </div>

  <!-- SCREEN 6: RESULTS -->
  <div class="screen" id="screen-results">
    <div class="results-header">
      <h2 class="results-title">你的专属匹配结果</h2>
      <p class="results-sub">基于你的兴趣与偏好，AI 为你精选了以下社团</p>
    </div>
    <div class="match-summary">
      <div class="match-score-circle">
        <span class="match-score-num">4</span>
        <span class="match-score-unit">个推荐</span>
      </div>
      <div class="match-summary-text">
        <h3>匹配完成！</h3>
        <p>综合你的兴趣偏好、期望氛围和时间安排，我们从128个社团中为你精选出最适合的选择。</p>
      </div>
    </div>
    <div class="section-title">推荐社团 · 按匹配度排序</div>
    <div class="club-cards" id="club-cards-container"></div>
    <button class="btn btn-secondary" onclick="goTo('screen-hero')" style="width:100%">重新测评</button>
  </div>

  <!-- SCREEN 7: DETAIL -->
  <div class="screen" id="screen-detail">
    <button class="detail-back" onclick="goTo('screen-results')">← 返回结果</button>
    <div id="detail-content"></div>
  </div>

</div>

<!-- APPLY BAR -->
<div class="apply-box" id="apply-box">
  <div class="apply-inner">
    <button class="btn btn-secondary" style="flex:1" onclick="goTo('screen-results')">返回列表</button>
    <button class="btn btn-primary" style="flex:2" onclick="showApply()">立即申请加入 →</button>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<script>
  const state = { interests: [], style: null, time: null };

  const clubs = [
    {
      id: 1,
      name: '极客代码协会',
      category: '科技编程 · 学习型',
      icon: '💻',
      color: '#EEF2FF',
      match: 97,
      desc: '致力于编程技术探索与分享，涵盖算法竞赛、项目开发、AI应用等方向。每周例会分享前沿技术，定期举办内部hackathon。',
      tags: ['编程', '人工智能', '竞赛', '项目实战'],
      members: 86,
      freq: '每周二',
      duration: '2小时',
      intro: '极客代码协会成立于2016年，是校内规模最大的技术类社团。我们相信"Learning by Doing"，通过实际项目积累技术能力。社团氛围开放包容，无论你是零基础还是编程达人，都能在这里找到属于自己的位置。',
      activities: [
        { title: '2025秋季算法训练营', date: '9月15日 · 持续8周' },
        { title: 'Hackathon 48小时编程马拉松', date: '10月20日 · 年度大赛' },
        { title: 'AI应用开发工作坊', date: '每月第一个周六' },
        { title: '校际编程竞赛备赛集训', date: '11月起 · 每周三' },
      ],
      contact: '微信公众号：极客代码协会'
    },
    {
      id: 2,
      name: '光影摄影社',
      category: '摄影影视 · 休闲型',
      icon: '📷',
      color: '#FFF7ED',
      match: 91,
      desc: '探索用镜头记录世界的无限可能，从人文纪实到风光摄影，从胶片美学到数字后期，我们在光与影之间讲述故事。',
      tags: ['摄影', '后期修图', '人文纪实', '摄影展'],
      members: 64,
      freq: '每周六',
      duration: '3小时',
      intro: '光影摄影社汇聚了一群热爱用视觉语言表达自我的同学。我们定期举办摄影展、外拍活动和后期分享会。社团拥有专业摄影棚和暗房设备，提供相机借用服务。',
      activities: [
        { title: '秋日外拍 · 城市人文主题', date: '9月22日 · 周六全天' },
        { title: '胶片摄影入门工作坊', date: '10月5日 · 限额20人' },
        { title: '年度摄影展筹备', date: '11月起 · 面向全校' },
        { title: 'Lightroom后期集训', date: '10月每周三晚' },
      ],
      contact: '微信公众号：光影摄影社'
    },
    {
      id: 3,
      name: '创业引力社',
      category: '创业商业 · 学习型',
      icon: '🚀',
      color: '#FFFBEB',
      match: 85,
      desc: '连接有创业梦想的同学，提供商业计划书指导、投资人对接、创业导师辅导等资源，已有3支团队获得天使轮融资。',
      tags: ['创业', '商业计划', '路演', '投资'],
      members: 45,
      freq: '每周四',
      duration: '2小时',
      intro: '创业引力社由一批有创业热情和商业思维的同学共同创立。我们定期邀请成功创业者和投资人来校分享，举办商业计划书大赛，并为有想法的同学提供组队和资源对接平台。',
      activities: [
        { title: '第五届校园商业计划书大赛', date: '10月启动 · 奖金丰厚' },
        { title: '创业者故事分享：从0到1', date: '9月28日 · 特邀嘉宾' },
        { title: '精益创业方法论工作坊', date: '每月第二周周四' },
        { title: '投资人见面会（内部活动）', date: '11月 · 仅限社员' },
      ],
      contact: '微信公众号：创业引力社'
    },
    {
      id: 4,
      name: '国际文化交流协会',
      category: '国际交流 · 休闲型',
      icon: '🌍',
      color: '#F0FDF4',
      match: 78,
      desc: '搭建中外学生交流桥梁，举办各国文化节、语言角、国际美食节等活动，让你不出校门就能体验世界文化。',
      tags: ['国际文化', '语言交流', '文化节', '结交外国友人'],
      members: 120,
      freq: '每周五',
      duration: '2小时',
      intro: '国际文化交流协会是校内成员最多的综合性社团之一，拥有来自30+个国家和地区的学生成员。每月定期举办"语言咖啡馆"，提供轻松愉快的语言练习环境。',
      activities: [
        { title: '秋季国际文化节', date: '10月12日 · 全校开放' },
        { title: '语言咖啡馆（每月）', date: '每月最后一个周五' },
        { title: '中秋文化体验活动', date: '9月下旬' },
        { title: '国际志愿者服务日', date: '11月 · 面向全体同学' },
      ],
      contact: '微信公众号：国际文化交流协会'
    }
  ];

  function goTo(screenId) {
    document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
    document.getElementById(screenId).classList.add('active');
    document.getElementById('apply-box').classList.toggle('visible', screenId === 'screen-detail');
    window.scrollTo(0, 0);
  }

  function toggleInterest(el, label) {
    el.classList.toggle('selected');
    if (el.classList.contains('selected')) {
      if (!state.interests.includes(label)) state.interests.push(label);
    } else {
      state.interests = state.interests.filter(i => i !== label);
    }
  }

  function selectOption(el, group) {
    el.closest('.option-list').querySelectorAll('.option-item').forEach(o => o.classList.remove('selected'));
    el.classList.add('selected');
    state[group] = el.querySelector('.option-text').textContent;
  }

  function goToQ2() {
    if (state.interests.length === 0) { showToast('请至少选择一个兴趣领域'); return; }
    goTo('screen-q2');
  }

  function goToQ3() {
    if (!state.style) { showToast('请选择你喜欢的社团风格'); return; }
    goTo('screen-q3');
  }

  function startMatching() {
    if (!state.time) { showToast('请选择每周可投入的时间'); return; }
    goTo('screen-loading');
    setTimeout(() => {
      renderResults();
      goTo('screen-results');
    }, 2800);
  }

  function renderResults() {
    const container = document.getElementById('club-cards-container');
    container.innerHTML = clubs.map(club => `
      <div class="club-card" onclick="showDetail(${club.id})">
        <div class="club-card-top">
          <div class="club-avatar" style="background:${club.color}">${club.icon}</div>
          <div class="club-card-info">
            <div class="club-name">${club.name}</div>
            <div class="club-category">${club.category}</div>
          </div>
          <div class="match-badge">⚡ ${club.match}%</div>
        </div>
        <div class="club-desc">${club.desc}</div>
        <div class="club-tags">${club.tags.map(t => `<span class="tag">${t}</span>`).join('')}</div>
        <div class="club-meta">
          <div class="meta-item"><span class="meta-icon">👥</span>${club.members} 人</div>
          <div class="meta-item"><span class="meta-icon">📅</span>${club.freq}</div>
          <div class="meta-item"><span class="meta-icon">⏱</span>${club.duration}/次</div>
        </div>
      </div>
    `).join('');
  }

  function showDetail(id) {
    const club = clubs.find(c => c.id === id);
    document.getElementById('detail-content').innerHTML = `
      <div class="detail-hero">
        <div class="detail-top">
          <div class="detail-avatar" style="background:${club.color}">${club.icon}</div>
          <div>
            <div class="detail-name">${club.name}</div>
            <div class="detail-sub">${club.category}</div>
          </div>
        </div>
        <div class="match-bar-row">
          <span class="match-bar-label">匹配度</span>
          <div class="match-bar"><div class="match-bar-fill" id="mbar" style="width:0%"></div></div>
          <span class="match-bar-pct">${club.match}%</span>
        </div>
        <div class="detail-stats">
          <div class="detail-stat">
            <div class="detail-stat-num">${club.members}</div>
            <div class="detail-stat-label">在籍社员</div>
          </div>
          <div class="detail-stat">
            <div class="detail-stat-num">${club.freq.replace('每','')}</div>
            <div class="detail-stat-label">活动频率</div>
          </div>
          <div class="detail-stat">
            <div class="detail-stat-num">${club.duration}</div>
            <div class="detail-stat-label">每次时长</div>
          </div>
        </div>
        <div class="club-tags">${club.tags.map(t => `<span class="tag">${t}</span>`).join('')}</div>
      </div>
      <div class="detail-section">
        <h3>关于我们</h3>
        <p>${club.intro}</p>
      </div>
      <div class="detail-section">
        <h3>近期活动</h3>
        <div class="activity-list">
          ${club.activities.map((a, i) => `
            <div class="activity-item">
              <div class="activity-dot-col">
                <div class="a-dot"></div>
                ${i < club.activities.length-1 ? '<div class="a-line"></div>' : ''}
              </div>
              <div class="activity-content">
                <div class="a-title">${a.title}</div>
                <div class="a-date">${a.date}</div>
              </div>
            </div>
          `).join('')}
        </div>
      </div>
      <div class="detail-section">
        <h3>联系方式</h3>
        <p>${club.contact}</p>
      </div>
      <div style="height: 80px;"></div>
    `;
    goTo('screen-detail');
    setTimeout(() => {
      const bar = document.getElementById('mbar');
      if (bar) bar.style.width = club.match + '%';
    }, 100);
  }

  function showApply() {
    showToast('🎉 申请已提交！社团负责人将在 48 小时内联系你');
  }

  function showToast(msg) {
    const t = document.getElementById('toast');
    t.textContent = msg;
    t.classList.add('show');
    setTimeout(() => t.classList.remove('show'), 2500);
  }
</script>
</body>
</html>
