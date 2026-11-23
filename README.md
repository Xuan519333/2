[index.html](https://github.com/user-attachments/files/35278818/index.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>我的学习工作台 · 电气自动化</title>
<meta name="description" content="电气自动化技术专业大专大一新生的个人学习仪表盘">
<style>
  /* ===== 基础 ===== */
  :root{
    --bg:#f4f7fa; --card:#ffffff; --ink:#1f2a37; --muted:#6b7785;
    --line:#e4e9f0; --brand:#0c447c; --brand-2:#185fa5;
    --accent:#0f6e56; --accent-soft:#e1f5ee; --amber:#854f0b;
    --amber-soft:#faeeda; --red:#a32d2d; --shadow:0 1px 3px rgba(16,24,40,.06),0 1px 2px rgba(16,24,40,.04);
  }
  *{box-sizing:border-box;margin:0;padding:0}
  html{scroll-behavior:smooth}
  body{
    font-family:-apple-system,BlinkMacSystemFont,"Segoe UI","PingFang SC","Microsoft YaHei",sans-serif;
    background:var(--bg);color:var(--ink);line-height:1.6;
    background-image:
      linear-gradient(var(--line) 1px,transparent 1px),
      linear-gradient(90deg,var(--line) 1px,transparent 1px);
    background-size:32px 32px;background-position:-1px -1px;
  }
  a{color:var(--brand-2);text-decoration:none}
  a:hover{text-decoration:underline}
  .wrap{max-width:1080px;margin:0 auto;padding:0 20px}

  /* ===== Hero ===== */
  .hero{
    background:linear-gradient(135deg,#0c447c 0%,#185fa5 55%,#0f6e56 100%);
    color:#fff;padding:46px 0 40px;position:relative;overflow:hidden;
  }
  .hero::after{
    content:"";position:absolute;right:-60px;top:-60px;width:260px;height:260px;
    border:2px solid rgba(255,255,255,.12);border-radius:50%;
    box-shadow:inset 0 0 0 24px rgba(255,255,255,.04);
  }
  .hero .wrap{position:relative;z-index:1}
  .hero h1{font-size:30px;font-weight:700;letter-spacing:.5px}
  .hero .tagline{margin-top:8px;font-size:15px;opacity:.92;max-width:640px}
  .hero .meta{margin-top:18px;display:flex;flex-wrap:wrap;gap:10px}
  .pill{
    background:rgba(255,255,255,.14);border:1px solid rgba(255,255,255,.22);
    padding:5px 13px;border-radius:999px;font-size:13px;backdrop-filter:blur(4px);
  }
  .hero .stats{margin-top:22px;display:flex;flex-wrap:wrap;gap:26px}
  .hero .stats b{font-size:24px;font-weight:700;display:block}
  .hero .stats span{font-size:12px;opacity:.8}

  /* ===== 区块 ===== */
  section{padding:34px 0}
  section + section{padding-top:0}
  .sec-head{display:flex;align-items:baseline;justify-content:space-between;margin-bottom:16px}
  .sec-head h2{font-size:18px;font-weight:600;color:var(--ink)}
  .sec-head .sub{font-size:13px;color:var(--muted)}
  .grid{display:grid;gap:16px}
  .card{background:var(--card);border:1px solid var(--line);border-radius:12px;padding:18px;box-shadow:var(--shadow)}
  .card h3{font-size:15px;font-weight:600;margin-bottom:4px}
  .card .desc{font-size:13px;color:var(--muted)}

  /* 学习笔记（自由卡片式） */
  .notes-grid{grid-template-columns:repeat(auto-fill,minmax(260px,1fr))}
  .note{display:flex;flex-direction:column;gap:10px}
  .note-date{font-size:12px;color:var(--brand-2);font-weight:600;letter-spacing:.5px;border-left:3px solid var(--accent);padding-left:8px}
  .note-body{font-size:14px;color:var(--ink);white-space:pre-wrap}

  /* 资源 */
  .links{grid-template-columns:repeat(auto-fill,minmax(200px,1fr))}
  .link{display:flex;flex-direction:column;gap:3px}
  .link .t{font-weight:600;font-size:14px}
  .link .d{font-size:12px;color:var(--muted)}
  .link .go{margin-top:8px;font-size:12px}

  /* 本周计划 */
  .todo label{display:flex;align-items:center;gap:10px;padding:8px 0;font-size:14px;cursor:pointer;border-bottom:1px dashed var(--line)}
  .todo label:last-child{border-bottom:0}
  .todo input{width:17px;height:17px;accent-color:var(--accent);cursor:pointer}
  .todo input:checked + span{text-decoration:line-through;color:var(--muted)}

  /* 页脚 */
  footer{margin-top:20px;padding:26px 0 40px;text-align:center;color:var(--muted);font-size:12px}
  footer .tip{display:inline-block;background:#fff;border:1px solid var(--line);border-radius:8px;padding:8px 14px;margin-bottom:12px}

  @media(max-width:640px){
    .hero h1{font-size:24px}
    .hero .stats{gap:18px}
    .hero .stats b{font-size:20px}
  }
</style>
</head>
<body>

<!-- ============================== Hero ============================== -->
<header class="hero">
  <div class="wrap">
    <h1>我的学习工作台</h1>
    <p class="tagline">电气自动化技术专业 · 一步一步，把零散的学习攒成看得见的成长。</p>
    <div class="meta">
      <span class="pill">电气自动化技术</span>
      <span class="pill">大专 · 大一</span>
      <span class="pill" id="weekPill">第 — 周</span>
    </div>
    <div class="stats">
      <div><b id="statNote">0</b><span>学习笔记</span></div>
      <div><b id="statTodo">0</b><span>本周计划</span></div>
      <div><b id="statDay">0</b><span>入学天数</span></div>
    </div>
  </div>
</header>

<!-- ===================================== 学习笔记 =====================================
     说明：每条笔记是一个 <article>，复制一个就新增一条。
     正文随便写，几行都行；日期格式如 11-21。
     ============================================================ -->
<section class="wrap" id="notes">
  <div class="sec-head">
    <h2>学习笔记</h2>
    <span class="sub">想写什么写什么，自由记录</span>
  </div>
  <div class="grid notes-grid">

    <article class="card note">
      <div class="note-date">11-21</div>
      <div class="note-body">
        今天学了基尔霍夫定律：KCL 节点电流进=出，KVL 回路电压升=降。难点在判断方向，先标好参考方向再列方程就不容易错。
      </div>
    </article>

    <article class="card note">
      <div class="note-date">11-18</div>
      <div class="note-body">
        导数的几何意义是切线斜率，也就是瞬时变化率。记几个常用公式：幂函数、sin、cos、e^x，多做题找手感。
      </div>
    </article>

    <article class="card note">
      <div class="note-date">11-15</div>
      <div class="note-body">
        AutoCAD 电气图层：强电、弱电、控制分开画，符号按国标。今天整理了一份常用符号表，放在桌面。
      </div>
    </article>

  </div>
</section>

<!-- ===================================== ④ 学习资源 =====================================
     说明：href 改成你想跳转的网址。
     ============================================================ -->
<section class="wrap" id="links">
  <div class="sec-head">
    <h2>常用学习资源</h2>
    <span class="sub">点一下直达</span>
  </div>
  <div class="grid links">
    <a class="card link" href="https://www.bilibili.com" target="_blank" rel="noopener">
      <span class="t">B 站</span><span class="d">电路 / 自控 / PLC 教程视频</span><span class="go">前往 →</span>
    </a>
    <a class="card link" href="https://www.icourse163.org" target="_blank" rel="noopener">
      <span class="t">中国大学 MOOC</span><span class="d">高校精品课，免费学</span><span class="go">前往 →</span>
    </a>
    <a class="card link" href="https://www.zhihu.com" target="_blank" rel="noopener">
      <span class="t">知乎</span><span class="d">专业经验与学习路径</span><span class="go">前往 →</span>
    </a>
    <a class="card link" href="https://csdiy.wiki" target="_blank" rel="noopener">
      <span class="t">CS 自学指南</span><span class="d">自学方法与课程导航</span><span class="go">前往 →</span>
    </a>
    <a class="card link" href="https://www.runoob.com" target="_blank" rel="noopener">
      <span class="t">菜鸟教程</span><span class="d">C 语言 / Git / HTML 速查</span><span class="go">前往 →</span>
    </a>
    <a class="card link" href="https://github.com" target="_blank" rel="noopener">
      <span class="t">GitHub</span><span class="d">托管代码 / 看开源项目</span><span class="go">前往 →</span>
    </a>
  </div>
</section>

<!-- ===================================== ⑤ 本周计划 =====================================
     说明：改文字即可。勾选状态刷新页面会重置（保持简单，零依赖）。
     ============================================================ -->
<section class="wrap" id="todo">
  <div class="sec-head">
    <h2>本周计划</h2>
    <span class="sub">每周初更新一次，做完就打勾</span>
  </div>
  <div class="card todo">
    <label><input type="checkbox"><span>学习电气知识</span></label>
    <label><input type="checkbox"><span>每天背 60 个英语单词</span></label>
    <label><input type="checkbox"><span>每周英语周刊</span></label>
  </div>
</section>

<footer>
  <div class="wrap">
    <div class="tip">💡 想改内容？打开 <b>index.html</b>，找到对应区块的注释，照着样子改文字就行。</div>
    <div>由 GitHub Pages 托管 · 个人学习工作台 · © <span id="year"></span></div>
  </div>
</footer>

<script>
  // ===== 自动计算：开学周次 / 入学天数 / 统计数字 =====
  // 把下面的日期改成你这学期开学的第一天（年,月-1,日）。注意月份从 0 开始：9月写 8。
  const termStart = new Date(2026, 8, 1); // 2026年9月1日开学

  const now = new Date();
  const days = Math.max(0, Math.floor((now - termStart) / 86400000));
  const week = Math.max(1, Math.ceil(days / 7));
  document.getElementById('statDay').textContent = days;
  document.getElementById('weekPill').textContent = '第 ' + week + ' 周';
  document.getElementById('statNote').textContent = document.querySelectorAll('#notes .note').length;
  document.getElementById('statTodo').textContent = document.querySelectorAll('#todo input[type=checkbox]').length;
  document.getElementById('year').textContent = now.getFullYear();
</script>
</body>
</html>
