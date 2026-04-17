---
layout: default
title: "首页"
permalink: /
---

<!-- Hero -->
<section class="hero animate-fade-in">
  <p class="hero-greeting">
    <span class="lang-zh">你好，我是紫云 ✨</span>
    <span class="lang-en">Hi, I'm Ziyun ✨</span>
  </p>
  <p class="hero-sub">
    <span class="lang-zh">安全研究者 · 终身学习者</span>
    <span class="lang-en">Security Researcher · Lifelong Learner</span>
  </p>
  <div class="hero-actions">
    <a href="/blog/" class="btn btn-primary">
      <span class="lang-zh">✍️ 看看博客</span>
      <span class="lang-en">✍️ Read Blog</span>
    </a>
    <a href="mailto:zyguo@smu.edu.sg" class="btn btn-outline">📧 Email</a>
    <a href="https://github.com/ZiyunGuo-Sec" class="btn btn-outline" target="_blank" rel="noopener">🐙 GitHub</a>
  </div>
</section>

<!-- About -->
<section id="about" class="sp-section animate-fade-in">
  <h2 class="section-title">
    <span class="lang-zh">关于我</span>
    <span class="lang-en">About</span>
  </h2>
  <div class="card">
    <div class="profile-card" style="margin-bottom:0;">
      <div class="profile-avatar">🌸</div>
      <div class="profile-info">
        <h3 style="font-size:1.2rem; margin-bottom:0.25rem;">Ziyun Guo · 紫云</h3>
        <p class="profile-tagline">Research Engineer, Singapore Management University (SMU)</p>
      </div>
    </div>
    <hr style="margin:1.25rem 0; border-color:#f0d6eb;" />
    <div class="lang-zh">
      <p>我目前是新加坡管理大学（SMU）计算机科学系的研究工程师，此前于南洋理工大学（NTU）取得网络安全硕士学位。研究方向聚焦于<strong>软件安全与智能化测试</strong>，具体包括 GUI 自动化测试与网络安全。</p>
      <p>🌍 当前主要研究方向：GUI 测试自动化 · 渗透测试 · 静态分析 · Fuzzing（学习中 🌱）</p>
    </div>
    <div class="lang-en">
      <p>I am a Research Engineer in Computer Science at Singapore Management University (SMU). Prior to that, I received my Master's degree in Cyber Security from Nanyang Technological University (NTU), Singapore. My research interests lie at the intersection of <strong>software security and intelligent testing</strong>, covering GUI testing automation and cybersecurity.</p>
      <p>🌍 Current interests: GUI Testing · Penetration Testing · Static Analysis · Fuzzing (in progress 🌱)</p>
    </div>
  </div>
</section>

<!-- Research -->
<section id="research" class="sp-section animate-fade-in">
  <h2 class="section-title">
    <span class="lang-zh">研究经历</span>
    <span class="lang-en">Research Experience</span>
  </h2>
  <div class="timeline">

    <div class="timeline-entry">
      <div class="timeline-date">Jul 2025 – Present</div>
      <div class="timeline-title">Identifying Compatibility Issues in LLM-powered Webpages</div>
      <div class="timeline-sub">Singapore Management University (SMU)</div>
      <ul>
        <li>Participate in an empirical study on cross-browser and cross-device issues in LLM-generated webpages.</li>
        <li>Contribute to the design of a test oracle and automated framework for evaluating UI rendering consistency across platforms.</li>
        <li>Analyze incompatibility patterns between LLM-generated and human-developed webpages, and explore mitigation strategies.</li>
      </ul>
    </div>

    <div class="timeline-entry">
      <div class="timeline-date">Nov 2024 – May 2025</div>
      <div class="timeline-title">Harnessing Large Language Models for Software Security</div>
      <ul>
        <li>Conducted an empirical evaluation of multiple LLMs for vulnerability discovery, tool orchestration, and multi-stage attack-chain planning.</li>
        <li>Augmented the PentestGPT framework with RAG and knowledge-graph reasoning to improve command fidelity and context retention.</li>
        <li>Refactored the system for modular, multi-model integration (Ollama-compatible), demonstrating the feasibility of scalable LLM-powered code analysis workflows.</li>
      </ul>
    </div>

    <div class="timeline-entry">
      <div class="timeline-date">Mar 2021 – Jul 2023</div>
      <div class="timeline-title">Knowledge Copyright Protection System for Short Video Content</div>
      <ul>
        <li>Developed a program for analyzing content plagiarism in short videos, proposing a copyright protection solution based on graph neural networks and smart contracts.</li>
        <li>Identified video content using GCN model, demonstrating effective content recognition capability.</li>
      </ul>
    </div>

    <div class="timeline-entry">
      <div class="timeline-date">Jun 2021 – Aug 2022</div>
      <div class="timeline-title">Research on Automated Attack Planning</div>
      <ul>
        <li>Proposed a knowledge-graph-based framework to construct an attack behavior database for automated attack route planning.</li>
        <li>Developed a web crawler to collect vulnerability records from the National Vulnerability Database (NVD) and technical blog texts.</li>
        <li>Applied NLP techniques for named entity recognition and knowledge graph ontology construction.</li>
      </ul>
    </div>

  </div>
</section>

<!-- Internship -->
<section id="experience" class="sp-section animate-fade-in">
  <h2 class="section-title">
    <span class="lang-zh">实习经历</span>
    <span class="lang-en">Internship Experience</span>
  </h2>
  <div class="timeline">

    <div class="timeline-entry">
      <div class="timeline-date">Oct 2023 – Jan 2024</div>
      <div class="timeline-title">NetEase · Beijing</div>
      <div class="timeline-sub">
        <span class="lang-zh">实习生，质量保证部</span>
        <span class="lang-en">Intern, Quality Assurance Department</span>
      </div>
      <ul>
        <li>Conducted quality checks for multiple projects during release phases.</li>
        <li>Participated in regression GUI testing, ensuring software stability and integrity after updates.</li>
        <li>Identified and reported bugs across various test cycles.</li>
      </ul>
    </div>

    <div class="timeline-entry">
      <div class="timeline-date">May 2023 – Jun 2023</div>
      <div class="timeline-title">NSFOCUS Technologies Group · Chengdu</div>
      <div class="timeline-sub">
        <span class="lang-zh">实习生，网络安全技术部</span>
        <span class="lang-en">Intern, Cybersecurity Technology Department</span>
      </div>
      <ul>
        <li>Tested and developed the next-generation gateway firewall.</li>
        <li>Designed test cases covering extensive API parameters and detected multiple bugs.</li>
        <li>Completed automated test scripts and analyzed results from test logs.</li>
      </ul>
    </div>

  </div>
</section>

<!-- Education -->
<section id="education" class="sp-section animate-fade-in">
  <h2 class="section-title">
    <span class="lang-zh">教育背景</span>
    <span class="lang-en">Education</span>
  </h2>
  <div class="timeline">

    <div class="timeline-entry">
      <div class="timeline-date">Aug 2024 – Present</div>
      <div class="timeline-title">Nanyang Technological University (NTU)</div>
      <div class="timeline-sub">Master of Science in Cyber Security</div>
    </div>

    <div class="timeline-entry">
      <div class="timeline-date">Sep 2020 – Jun 2024</div>
      <div class="timeline-title">
        <span class="lang-zh">本科</span>
        <span class="lang-en">Undergraduate</span>
      </div>
      <div class="timeline-sub">Bachelor of Engineering in Cyber Security</div>
    </div>

  </div>
</section>

<!-- Skills -->
<section id="skills" class="sp-section animate-fade-in">
  <h2 class="section-title">
    <span class="lang-zh">技能</span>
    <span class="lang-en">Skills</span>
  </h2>
  <div class="skills-grid">
    <div class="skill-group">
      <h3><span class="lang-zh">编程语言</span><span class="lang-en">Programming</span></h3>
      <div class="skill-tags">
        <span class="tag tag-pink">Python</span>
        <span class="tag tag-pink">Java</span>
        <span class="tag tag-pink">C/C++</span>
        <span class="tag tag-pink">C#</span>
        <span class="tag">SQL</span>
        <span class="tag">MATLAB</span>
        <span class="tag">Kotlin</span>
      </div>
    </div>
    <div class="skill-group">
      <h3>LLM Tooling</h3>
      <div class="skill-tags">
        <span class="tag tag-blue">OpenAI API</span>
        <span class="tag tag-blue">Ollama</span>
        <span class="tag tag-blue">RAG Pipelines</span>
        <span class="tag tag-blue">LangChain</span>
      </div>
    </div>
    <div class="skill-group">
      <h3><span class="lang-zh">测试与安全</span><span class="lang-en">Testing & Security</span></h3>
      <div class="skill-tags">
        <span class="tag">GUI Testing</span>
        <span class="tag">Mobile Testing</span>
        <span class="tag tag-pink">Penetration Testing</span>
        <span class="tag tag-pink">Static Analysis</span>
        <span class="tag tag-pink">Fuzzing 🌱</span>
      </div>
    </div>
  </div>
</section>

<!-- Friends -->
<section id="friends" class="sp-section animate-fade-in">
  <h2 class="section-title">
    <span class="lang-zh">友链</span>
    <span class="lang-en">Friends</span>
  </h2>
  <div class="friends-grid">
    {% for friend in site.data.friends %}
    <a class="friend-card" href="{{ friend.url }}" target="_blank" rel="noopener noreferrer">
      <div class="friend-avatar">
        {% if friend.avatar and friend.avatar != "" %}
          <img src="{{ friend.avatar }}" alt="{{ friend.name }}" loading="lazy" />
        {% else %}
          <span class="friend-avatar-placeholder">{{ friend.name | slice: 0 }}</span>
        {% endif %}
      </div>
      <div class="friend-info">
        <span class="friend-name">{{ friend.name }}</span>
        {% if friend.school or friend.degree %}<span class="friend-desc">{{ friend.school }}{% if friend.school and friend.degree %} · {% endif %}{{ friend.degree }}</span>{% endif %}
        {% if friend.research %}<span class="friend-desc">🔬 {{ friend.research }}</span>{% endif %}
      </div>
      <span class="friend-icon" aria-hidden="true">✦</span>
    </a>
    {% endfor %}
  </div>
</section>
