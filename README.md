[index.html](https://github.com/user-attachments/files/35277970/index.html)
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

  /* 课程进度 */
  .courses{grid-template-columns:repeat(auto-fill,minmax(280px,1fr))}
  .course .top{display:flex;justify-content:space-between;align-items:center;margin-bottom:9px}
  .course .name{font-weight:600;font-size:14px}
  .course .pct{font-size:12px;color:var(--muted);font-variant-numeric:tabular-nums}
  .bar{height:8px;background:#eef2f7;border-radius:999px;overflow:hidden}
  .bar > i{display:block;height:100%;border-radius:999px;background:linear-gradient(90deg,#185fa5,#0f6e56);width:0;transition:width 1.1s cubic-bezier(.2,.8,.2,1)}
  .course .note{margin-top:8px;font-size:12px;color:var(--muted)}

  /* 笔记列表 */
  .notes{list-style:none}
  .notes li{display:flex;gap:12px;padding:11px 0;border-bottom:1px dashed var(--line)}
  .notes li:last-child{border-bottom:0}
  .notes .date{flex:0 0 64px;font-size:12px;color:var(--muted);font-variant-numeric:tabular-nums;padding-top:2px}
  .notes .body{flex:1}
  .notes .t{font-size:14px;font-weight:500}
  .notes .tags{margin-top:3px}
  .tag{display:inline-block;font-size:11px;background:var(--accent-soft);color:var(--accent);padding:1px 8px;border-radius:4px;margin-right:5px}
  .tag.b{background:#e6f1fb;color:var(--brand)}
  .tag.a{background:var(--amber-soft);color:var(--amber)}

  /* 项目卡片 */
  .projects{grid-template-columns:repeat(auto-fill,minmax(240px,1fr))}
  .proj .num{font-size:12px;color:var(--brand-2);font-weight:600;letter-spacing:1px}
  .proj .t{font-size:15px;font-weight:600;margin:3px 0 6px}
  .proj ul{margin:8px 0 0 14px;font-size:13px;color:var(--muted)}
  .status{display:inline-block;font-size:11px;padding:2px 9px;border-radius:999px;margin-top:10px}
  .status.doing{background:var(--amber-soft);color:var(--amber)}
  .status.done{background:var(--accent-soft);color:var(--accent)}
  .status.plan{background:#eef2f7;color:var(--muted)}

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
      <div><b id="statCourse">0</b><span>在修课程</span></div>
      <div><b id="statNote">0</b><span>学习笔记</span></div>
      <div><b id="statProj">0</b><span>实验项目</span></div>
      <div><b id="statDay">0</b><span>入学天数</span></div>
    </div>
  </div>
</header>

<!-- ===================================== ① 课程进度看板 =====================================
     说明：在 <div class="grid courses"> 里复制/删除一个 <div class="card course"> 即可增删课程。
     data-pct 是进度百分比(0~100)，页面加载时会自动播放进度条动画。
     ============================================================ -->
<section class="wrap" id="courses">
  <div class="sec-head">
    <h2>课程进度看板</h2>
    <span class="sub">大一上学期 · 点击右上角进度数字查看掌握程度</span>
  </div>
  <div class="grid courses">

    <div class="card course" data-pct="62">
      <div class="top"><span class="name">电路基础</span><span class="pct">62%</span></div>
      <div class="bar"><i></i></div>
      <div class="note">欧姆定律 / 基尔霍夫 / 戴维南定理</div>
    </div>

    <div class="card course" data-pct="55">
      <div class="top"><span class="name">高等数学</span><span class="pct">55%</span></div>
      <div class="bar"><i></i></div>
      <div class="note">极限 / 导数 / 微分基础</div>
    </div>

    <div class="card course" data-pct="70">
      <div class="top"><span class="name">工程制图（CAD）</span><span class="pct">70%</span></div>
      <div class="bar"><i></i></div>
      <div class="note">AutoCAD 基本操作 / 电气符号</div>
    </div>

    <div class="card course" data-pct="40">
      <div class="top"><span class="name">C 语言程序设计</span><span class="pct">40%</span></div>
      <div class="bar"><i></i></div>
      <div class="note">变量 / 流程控制 / 函数入门</div>
    </div>

    <div class="card course" data-pct="80">
      <div class="top"><span class="name">大学英语</span><span class="pct">80%</span></div>
      <div class="bar"><i></i></div>
      <div class="note">词汇积累 / 四级备考中</div>
    </div>

    <div class="card course" data-pct="90">
      <div class="top"><span class="name">思想政治理论</span><span class="pct">90%</span></div>
      <div class="bar"><i></i></div>
      <div class="note">按时完成 / 期末复习中</div>
    </div>

  </div>
</section>

<!-- ===================================== ② 近期学习笔记 =====================================
     说明：在 <ul class="notes"> 里复制一个 <li> 即可新增笔记。
     ============================================================ -->
<section class="wrap" id="notes">
  <div class="sec-head">
    <h2>近期学习笔记</h2>
    <span class="sub">随手记，攒成自己的知识库</span>
  </div>
  <div class="card">
    <ul class="notes">
      <li>
        <div class="date">11-21</div>
        <div class="body">
          <div class="t">基尔霍夫电流定律（KCL）与电压定律（KVL）小结</div>
          <div class="tags"><span class="tag b">电路基础</span><span class="tag">节点/回路</span></div>
        </div>
      </li>
      <li>
        <div class="date">11-18</div>
        <div class="body">
          <div class="t">导数定义与几何意义：切线斜率 = 瞬时变化率</div>
          <div class="tags"><span class="tag a">高等数学</span><span class="tag">求导公式</span></div>
        </div>
      </li>
      <li>
        <div class="date">11-15</div>
        <div class="body">
          <div class="t">AutoCAD 电气图层设置与常用符号库整理</div>
          <div class="tags"><span class="tag b">工程制图</span><span class="tag">CAD</span></div>
        </div>
      </li>
      <li>
        <div class="date">11-12</div>
        <div class="body">
          <div class="t">C 语言 for 循环与一维数组：成绩统计小练习</div>
          <div class="tags"><span class="tag a">C 语言</span><span class="tag">数组</span></div>
        </div>
      </li>
      <li>
        <div class="date">11-09</div>
        <div class="body">
          <div class="t">认识 PLC：可编程逻辑控制器在自动化产线中的作用</div>
          <div class="tags"><span class="tag">专业认知</span><span class="tag">PLC</span></div>
        </div>
      </li>
    </ul>
  </div>
</section>

<!-- ===================================== ③ 实验与项目 =====================================
     说明：在 <div class="grid projects"> 里复制一个 <div class="card proj"> 即可新增项目。
     status 三种：doing(进行中) / done(已完成) / plan(计划中)
     ============================================================ -->
<section class="wrap" id="projects">
  <div class="sec-head">
    <h2>实验与项目</h2>
    <span class="sub">把动手做的记录下来，毕业就是作品集</span>
  </div>
  <div class="grid projects">

    <div class="card proj">
      <div class="num">EXP-01</div>
      <div class="t">万用表测电压电流电阻</div>
      <ul>
        <li>直流/交流电压测量</li>
        <li>电阻档位选择与读数</li>
      </ul>
      <span class="status done">已完成</span>
    </div>

    <div class="card proj">
      <div class="num">EXP-02</div>
      <div class="t">基尔霍夫定律验证实验</div>
      <ul>
        <li>搭建多回路电路</li>
        <li>测量验证 KCL/KVL</li>
      </ul>
      <span class="status doing">进行中</span>
    </div>

    <div class="card proj">
      <div class="num">EXP-03</div>
      <div class="t">日光灯电路与功率因数提高</div>
      <ul>
        <li>感性负载分析</li>
        <li>并联电容补偿</li>
      </ul>
      <span class="status plan">计划中</span>
    </div>

    <div class="card proj">
      <div class="num">PRJ-01</div>
      <div class="t">用 C 语言写一个简易计算器</div>
      <ul>
        <li>练习函数与流程控制</li>
        <li>控制台交互</li>
      </ul>
      <span class="status plan">计划中</span>
    </div>

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
    <label><input type="checkbox"><span>复习电路基础第 3 章，做课后习题</span></label>
    <label><input type="checkbox"><span>整理高数导数公式表</span></label>
    <label><input type="checkbox"><span>完成基尔霍夫实验报告</span></label>
    <label><input type="checkbox"><span>C 语言练习：写一个数组求最值的程序</span></label>
    <label><input type="checkbox"><span>背英语单词 100 个</span></label>
    <label><input type="checkbox"><span>看 2 集 PLC 入门视频</span></label>
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
  document.getElementById('statCourse').textContent = document.querySelectorAll('#courses .course').length;
  document.getElementById('statNote').textContent = document.querySelectorAll('#notes .notes li').length;
  document.getElementById('statProj').textContent = document.querySelectorAll('#projects .proj').length;
  document.getElementById('year').textContent = now.getFullYear();

  // ===== 进度条动画 =====
  const io = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        const pct = e.target.getAttribute('data-pct');
        e.target.querySelector('.bar > i').style.width = pct + '%';
        io.unobserve(e.target);
      }
    });
  }, { threshold: .3 });
  document.querySelectorAll('#courses .course').forEach(c => io.observe(c));
</script>
</body>
</html>
