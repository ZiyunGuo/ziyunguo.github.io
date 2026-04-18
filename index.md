---
layout: default
title: "Home"
permalink: /
---

<!-- Hero -->
<section class="hero animate-fade-in">
  <div class="hero-main">
    <div class="hero-left">
      <img src="/assets/images/avatar.png" alt="Ziyun Guo" class="hero-avatar" />
      <p class="hero-greeting">Ziyun Guo</p>
      <p class="hero-sub">Research Engineer · Singapore Management University</p>
    </div>
    <div class="hero-divider" aria-hidden="true"></div>
    <div class="hero-right">
      <p class="hero-meta-item"><span class="hero-meta-icon">📍</span><span>Singapore</span></p>
      <p class="hero-meta-item"><i class="fa-solid fa-envelope"></i><a href="mailto:zyguo@smu.edu.sg">zyguo@smu.edu.sg</a></p>
      <p class="hero-meta-item"><i class="fa-brands fa-github"></i><a href="https://github.com/ZiyunGuo" target="_blank" rel="noopener">ZiyunGuo</a></p>
    </div>
  </div>
</section>

<!-- Post Heatmap -->
<section id="post-heatmap" class="sp-section animate-fade-in">
  <h2 class="section-title">Post Activity</h2>
  <div class="card post-heatmap-card">
    <div class="post-heatmap-head">
      <p class="post-heatmap-sub">Updates in the last 12 months</p>
      <p class="post-heatmap-summary" id="post-heatmap-summary">Loading activity...</p>
    </div>
    <div class="post-heatmap-wrap">
      <div class="post-heatmap-months" id="post-heatmap-months" aria-hidden="true"></div>
      <div class="post-heatmap-grid" id="post-heatmap-grid" aria-label="Post activity heatmap"></div>
    </div>
    <div class="post-heatmap-meta">
      <p class="post-heatmap-tooltip" id="post-heatmap-tooltip">Hover a square to see details.</p>
      <div class="post-heatmap-legend" aria-hidden="true">
        <span>Less</span>
        <span class="post-heatmap-cell level-0"></span>
        <span class="post-heatmap-cell level-1"></span>
        <span class="post-heatmap-cell level-2"></span>
        <span class="post-heatmap-cell level-3"></span>
        <span class="post-heatmap-cell level-4"></span>
        <span>More</span>
      </div>
    </div>
    <div class="post-heatmap-daylist" id="post-heatmap-daylist">
      <p class="post-heatmap-daylist-title" id="post-heatmap-daylist-title">Click a day to view updated posts.</p>
      <ul class="post-heatmap-daylist-items" id="post-heatmap-daylist-items"></ul>
    </div>
  </div>

  <script>
    (() => {
      const posts = [
        {% for post in site.posts %}
          {
            date: "{{ post.date | date: '%Y-%m-%d' }}",
            title: {{ post.title | jsonify }},
            url: "{{ post.url | relative_url }}"
          }{% unless forloop.last %},{% endunless %}
        {% endfor %}
      ];

      const grid = document.getElementById("post-heatmap-grid");
      const months = document.getElementById("post-heatmap-months");
      const summary = document.getElementById("post-heatmap-summary");
      const tooltip = document.getElementById("post-heatmap-tooltip");
      const daylistTitle = document.getElementById("post-heatmap-daylist-title");
      const daylistItems = document.getElementById("post-heatmap-daylist-items");

      if (!grid || !months || !summary || !tooltip || !daylistTitle || !daylistItems) return;

      const byDay = new Map();
      posts.forEach((post) => {
        if (!byDay.has(post.date)) byDay.set(post.date, []);
        byDay.get(post.date).push(post);
      });

      const toISODate = (date) => {
        const y = date.getFullYear();
        const m = String(date.getMonth() + 1).padStart(2, "0");
        const d = String(date.getDate()).padStart(2, "0");
        return `${y}-${m}-${d}`;
      };

      const formatDate = (date) =>
        date.toLocaleDateString("en-US", { year: "numeric", month: "short", day: "numeric" });

      const today = new Date();
      today.setHours(0, 0, 0, 0);

      const firstVisible = new Date(today);
      firstVisible.setDate(firstVisible.getDate() - 364);

      const mondayOffset = (firstVisible.getDay() + 6) % 7;
      const gridStart = new Date(firstVisible);
      gridStart.setDate(gridStart.getDate() - mondayOffset);

      const weeks = 53;
      const maxCount = Math.max(
        0,
        ...Array.from(byDay.values()).map((items) => items.length)
      );

      const getLevel = (count) => {
        if (count === 0) return 0;
        if (maxCount <= 4) return Math.min(4, count);
        return Math.min(4, Math.ceil((count / maxCount) * 4));
      };

      let activeDays = 0;
      let totalPosts = 0;
      let selectedCell = null;

      const showDayPosts = (date, entries) => {
        const count = entries.length;
        daylistTitle.textContent = `${formatDate(date)} · ${count} post${count === 1 ? "" : "s"}`;
        daylistItems.innerHTML = "";

        if (count === 0) {
          const li = document.createElement("li");
          li.textContent = "No post updated on this day.";
          daylistItems.appendChild(li);
          return;
        }

        entries.forEach((item) => {
          const li = document.createElement("li");
          const link = document.createElement("a");
          link.href = item.url;
          link.textContent = item.title;
          li.appendChild(link);
          daylistItems.appendChild(li);
        });
      };

      for (let week = 0; week < weeks; week += 1) {
        const weekStart = new Date(gridStart);
        weekStart.setDate(gridStart.getDate() + week * 7);

        const monthCell = document.createElement("span");
        monthCell.className = "post-heatmap-month";

        for (let day = 0; day < 7; day += 1) {
          const date = new Date(weekStart);
          date.setDate(weekStart.getDate() + day);
          const inRange = date >= firstVisible && date <= today;
          if (inRange && date.getDate() === 1) {
            monthCell.textContent = date.toLocaleDateString("en-US", { month: "short" });
            break;
          }
        }

        months.appendChild(monthCell);
      }

      for (let week = 0; week < weeks; week += 1) {
        const column = document.createElement("div");
        column.className = "post-heatmap-week";

        for (let day = 0; day < 7; day += 1) {
          const date = new Date(gridStart);
          date.setDate(gridStart.getDate() + week * 7 + day);

          const dateKey = toISODate(date);
          const entries = byDay.get(dateKey) || [];
          const count = entries.length;
          const isFuture = date > today;
          const inRange = date >= firstVisible && date <= today;

          if (inRange && count > 0) {
            activeDays += 1;
            totalPosts += count;
          }

          const cell = document.createElement("button");
          cell.type = "button";
          cell.className = `post-heatmap-cell level-${getLevel(count)}`;
          if (isFuture) cell.classList.add("is-future");
          if (!inRange) cell.classList.add("is-out-range");

          const details = entries.length
            ? entries.map((item) => item.title).join(" | ")
            : "No posts";
          const label = `${formatDate(date)}: ${count} post${count === 1 ? "" : "s"}. ${details}`;
          cell.setAttribute("aria-label", label);
          cell.dataset.info = label;

          if (inRange && !isFuture) {
            cell.classList.add("is-interactive");
            cell.addEventListener("click", () => {
              if (selectedCell) selectedCell.classList.remove("is-selected");
              cell.classList.add("is-selected");
              selectedCell = cell;
              showDayPosts(date, entries);
            });
          } else {
            cell.tabIndex = -1;
            cell.setAttribute("aria-disabled", "true");
          }

          const showInfo = () => {
            tooltip.textContent = label;
          };
          cell.addEventListener("mouseenter", showInfo);
          cell.addEventListener("focus", showInfo);

          column.appendChild(cell);
        }

        grid.appendChild(column);
      }

      summary.textContent = `${totalPosts} post${totalPosts === 1 ? "" : "s"} across ${activeDays} active day${activeDays === 1 ? "" : "s"}.`;

      showDayPosts(today, byDay.get(toISODate(today)) || []);
    })();
  </script>
</section>

<!-- About -->
<section id="about" class="sp-section animate-fade-in">
  <h2 class="section-title">About Me</h2>
  <div class="card">
    <p>I am a Research Engineer in Computer Science at Singapore Management University (SMU). I received my Master's degree in Cyber Security from Nanyang Technological University (NTU), Singapore. My research focuses on <strong>software security and intelligent testing</strong>, with work spanning GUI testing automation, penetration testing, and LLM-powered security analysis.</p>
  </div>
</section>

<!-- Research -->
<section id="research" class="sp-section animate-fade-in">
  <h2 class="section-title">Research Experience</h2>
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
  <h2 class="section-title">Internship Experience</h2>
  <div class="timeline">

    <div class="timeline-entry">
      <div class="timeline-date">Oct 2023 – Jan 2024</div>
      <div class="timeline-title">NetEase · Beijing</div>
      <div class="timeline-sub">Intern, Quality Assurance Department</div>
      <ul>
        <li>Conducted quality checks for multiple projects during release phases.</li>
        <li>Participated in regression GUI testing, ensuring software stability and integrity after updates.</li>
        <li>Identified and reported bugs across various test cycles.</li>
      </ul>
    </div>

    <div class="timeline-entry">
      <div class="timeline-date">May 2023 – Jun 2023</div>
      <div class="timeline-title">NSFOCUS Technologies Group · Chengdu</div>
      <div class="timeline-sub">Intern, Cybersecurity Technology Department</div>
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
  <h2 class="section-title">Education</h2>
  <div class="timeline">

    <div class="timeline-entry">
      <div class="timeline-date">Aug 2024 – Present</div>
      <div class="timeline-title">Nanyang Technological University (NTU)</div>
      <div class="timeline-sub">Master of Science in Cyber Security</div>
    </div>

    <div class="timeline-entry">
      <div class="timeline-date">Sep 2020 – Jun 2024</div>
      <div class="timeline-title">Undergraduate</div>
      <div class="timeline-sub">Bachelor of Engineering in Cyber Security</div>
    </div>

  </div>
</section>

<!-- Skills -->
<section id="skills" class="sp-section animate-fade-in">
  <h2 class="section-title">Skills</h2>
  <div class="skills-grid">
    <div class="skill-group">
      <h3>Programming</h3>
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
      <h3>Testing & Security</h3>
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
  <h2 class="section-title">Friends</h2>
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
