<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Henricson Austria — Cloud Engineer</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400;500&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg: #0b0f14;
      --surface: #111820;
      --surface2: #1a2433;
      --border: rgba(255,255,255,0.07);
      --accent: #00d4aa;
      --accent2: #0ea5e9;
      --text: #e2eaf4;
      --muted: #7a8fa6;
      --heading: #ffffff;
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'DM Mono', monospace;
      background: var(--bg);
      color: var(--text);
      line-height: 1.6;
      overflow-x: hidden;
    }

    /* Ambient background */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background:
        radial-gradient(ellipse 60% 40% at 80% 10%, rgba(0,212,170,0.07) 0%, transparent 70%),
        radial-gradient(ellipse 50% 50% at 10% 80%, rgba(14,165,233,0.06) 0%, transparent 70%);
      pointer-events: none;
      z-index: 0;
    }

    /* NAV */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1.2rem 4rem;
      background: rgba(11,15,20,0.85);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
    }

    .nav-logo {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: 1.1rem;
      color: var(--heading);
      letter-spacing: -0.02em;
      text-decoration: none;
    }

    .nav-logo span { color: var(--accent); }

    .nav-links {
      display: flex;
      gap: 2rem;
      list-style: none;
    }

    .nav-links a {
      font-size: 0.78rem;
      color: var(--muted);
      text-decoration: none;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      transition: color 0.2s;
    }

    .nav-links a:hover { color: var(--accent); }

    /* SECTIONS */
    section {
      position: relative;
      z-index: 1;
      max-width: 1000px;
      margin: 0 auto;
      padding: 6rem 2rem;
    }

    /* HERO */
    #hero {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding-top: 8rem;
    }

    .hero-tag {
      font-size: 0.75rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 1.5rem;
      display: flex;
      align-items: center;
      gap: 0.75rem;
    }

    .hero-tag::before {
      content: '';
      display: block;
      width: 32px;
      height: 1px;
      background: var(--accent);
    }

    h1 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(3rem, 8vw, 5.5rem);
      font-weight: 800;
      line-height: 1;
      color: var(--heading);
      letter-spacing: -0.04em;
      margin-bottom: 1.5rem;
    }

    h1 .line2 {
      display: block;
      background: linear-gradient(90deg, var(--accent), var(--accent2));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .hero-sub {
      font-size: 1rem;
      color: var(--muted);
      max-width: 520px;
      margin-bottom: 3rem;
      line-height: 1.8;
    }

    .hero-meta {
      font-size: 0.75rem;
      color: var(--muted);
      letter-spacing: 0.05em;
      margin-bottom: 3rem;
    }

    .hero-meta span { color: var(--accent); margin-right: 0.25rem; }

    .hero-cta {
      display: flex;
      gap: 1rem;
      flex-wrap: wrap;
    }

    .btn {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.75rem 1.75rem;
      border-radius: 4px;
      font-family: 'DM Mono', monospace;
      font-size: 0.8rem;
      font-weight: 500;
      text-decoration: none;
      letter-spacing: 0.05em;
      transition: all 0.2s;
      cursor: pointer;
      border: none;
    }

    .btn-primary {
      background: var(--accent);
      color: #0b0f14;
    }

    .btn-primary:hover {
      background: #00f0c0;
      transform: translateY(-2px);
      box-shadow: 0 8px 24px rgba(0,212,170,0.3);
    }

    .btn-outline {
      background: transparent;
      color: var(--text);
      border: 1px solid var(--border);
    }

    .btn-outline:hover {
      border-color: var(--accent);
      color: var(--accent);
      transform: translateY(-2px);
    }

    /* SECTION HEADERS */
    .section-label {
      font-size: 0.7rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 0.75rem;
      display: flex;
      align-items: center;
      gap: 0.75rem;
    }

    .section-label::after {
      content: '';
      flex: 1;
      height: 1px;
      background: var(--border);
    }

    h2 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(1.8rem, 4vw, 2.5rem);
      font-weight: 700;
      color: var(--heading);
      letter-spacing: -0.03em;
      margin-bottom: 3rem;
    }

    /* SKILLS GRID */
    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.5rem;
    }

    .skill-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 2rem;
      transition: border-color 0.2s, transform 0.2s;
    }

    .skill-card:hover {
      border-color: rgba(0,212,170,0.3);
      transform: translateY(-4px);
    }

    .skill-icon {
      font-size: 1.5rem;
      margin-bottom: 1rem;
    }

    .skill-card h3 {
      font-family: 'Syne', sans-serif;
      font-size: 1rem;
      font-weight: 700;
      color: var(--heading);
      margin-bottom: 1rem;
    }

    .skill-list {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 0.4rem;
    }

    .skill-list li {
      font-size: 0.78rem;
      color: var(--muted);
      padding-left: 1rem;
      position: relative;
    }

    .skill-list li::before {
      content: '›';
      position: absolute;
      left: 0;
      color: var(--accent);
    }

    /* BADGE TAGS */
    .badge-row {
      display: flex;
      flex-wrap: wrap;
      gap: 0.5rem;
      margin-top: 1rem;
    }

    .badge {
      font-size: 0.7rem;
      padding: 0.3rem 0.75rem;
      border-radius: 100px;
      border: 1px solid var(--border);
      color: var(--muted);
      letter-spacing: 0.05em;
      background: var(--surface);
    }

    .badge.active {
      border-color: rgba(0,212,170,0.4);
      color: var(--accent);
      background: rgba(0,212,170,0.05);
    }

    /* EXPERIENCE TIMELINE */
    .timeline {
      display: flex;
      flex-direction: column;
      gap: 0;
      position: relative;
    }

    .timeline::before {
      content: '';
      position: absolute;
      left: 0;
      top: 0; bottom: 0;
      width: 1px;
      background: var(--border);
    }

    .timeline-item {
      padding: 0 0 2.5rem 2rem;
      position: relative;
    }

    .timeline-item::before {
      content: '';
      position: absolute;
      left: -4px;
      top: 6px;
      width: 9px;
      height: 9px;
      border-radius: 50%;
      background: var(--accent);
      box-shadow: 0 0 12px rgba(0,212,170,0.5);
    }

    .timeline-item h3 {
      font-family: 'Syne', sans-serif;
      font-size: 1.05rem;
      font-weight: 700;
      color: var(--heading);
      margin-bottom: 0.25rem;
    }

    .timeline-meta {
      font-size: 0.72rem;
      color: var(--accent);
      letter-spacing: 0.06em;
      margin-bottom: 0.75rem;
    }

    .timeline-item p {
      font-size: 0.82rem;
      color: var(--muted);
      line-height: 1.7;
    }

    /* CERTS */
    .certs-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 1rem;
    }

    .cert-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 1.5rem;
      display: flex;
      align-items: flex-start;
      gap: 1rem;
      transition: border-color 0.2s;
    }

    .cert-card:hover { border-color: rgba(14,165,233,0.3); }

    .cert-icon {
      font-size: 1.5rem;
      flex-shrink: 0;
    }

    .cert-card h3 {
      font-family: 'Syne', sans-serif;
      font-size: 0.85rem;
      font-weight: 700;
      color: var(--heading);
      margin-bottom: 0.25rem;
    }

    .cert-card p {
      font-size: 0.72rem;
      color: var(--muted);
    }

    .cert-status {
      font-size: 0.65rem;
      padding: 0.2rem 0.5rem;
      border-radius: 100px;
      margin-top: 0.4rem;
      display: inline-block;
    }

    .cert-status.progress {
      background: rgba(251,191,36,0.1);
      color: #fbbf24;
      border: 1px solid rgba(251,191,36,0.3);
    }

    .cert-status.done {
      background: rgba(0,212,170,0.1);
      color: var(--accent);
      border: 1px solid rgba(0,212,170,0.3);
    }

    /* CONTACT */
    #contact {
      text-align: center;
    }

    #contact h2 { margin-bottom: 1rem; }

    .contact-sub {
      font-size: 0.85rem;
      color: var(--muted);
      margin-bottom: 2.5rem;
      max-width: 440px;
      margin-left: auto;
      margin-right: auto;
    }

    .contact-links {
      display: flex;
      gap: 1rem;
      justify-content: center;
      flex-wrap: wrap;
    }

    /* DIVIDER */
    .divider {
      height: 1px;
      background: var(--border);
      max-width: 1000px;
      margin: 0 auto;
    }

    /* FOOTER */
    footer {
      text-align: center;
      padding: 2rem;
      font-size: 0.72rem;
      color: var(--muted);
      position: relative;
      z-index: 1;
    }

    /* ANIMATIONS */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(24px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .hero-tag   { animation: fadeUp 0.6s ease both; }
    h1          { animation: fadeUp 0.6s 0.1s ease both; }
    .hero-sub   { animation: fadeUp 0.6s 0.2s ease both; }
    .hero-meta  { animation: fadeUp 0.6s 0.3s ease both; }
    .hero-cta   { animation: fadeUp 0.6s 0.4s ease both; }

    /* MOBILE */
    @media (max-width: 640px) {
      nav { padding: 1rem 1.5rem; }
      .nav-links { gap: 1.2rem; }
      section { padding: 5rem 1.5rem; }
    }
  </style>
</head>
<body>

  <nav>
    <a href="#hero" class="nav-logo">HA<span>.</span></a>
    <ul class="nav-links">
      <li><a href="#skills">Skills</a></li>
      <li><a href="#experience">Experience</a></li>
      <li><a href="#certs">Certs</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section id="hero">
    <p class="hero-tag">📍 Philippines &nbsp;·&nbsp; Available for Cloud Roles</p>
    <h1>Henricson<br><span class="line2">Austria</span></h1>
    <p class="hero-sub">
      IT Support & Network Specialist with 8+ years of enterprise experience,
      transitioning into <strong style="color:var(--text)">Cloud Engineering</strong> on
      Microsoft Azure and AWS.
    </p>
    <p class="hero-meta">
      <span>›</span> Active Directory &nbsp;&nbsp;
      <span>›</span> Azure VMs &nbsp;&nbsp;
      <span>›</span> AWS S3 / EC2 &nbsp;&nbsp;
      <span>›</span> PowerShell
    </p>
    <div class="hero-cta">
      <a href="#contact" class="btn btn-primary">Get in touch</a>
      <a href="#skills" class="btn btn-outline">View skills</a>
    </div>
  </section>

  <div class="divider"></div>

  <!-- SKILLS -->
  <section id="skills">
    <p class="section-label">What I bring</p>
    <h2>Core Strengths &<br>Cloud Focus</h2>

    <div class="skills-grid">
      <div class="skill-card">
        <div class="skill-icon">🖥️</div>
        <h3>IT Infrastructure</h3>
        <ul class="skill-list">
          <li>Windows Server support</li>
          <li>Active Directory (users & devices)</li>
          <li>Endpoint & asset management</li>
          <li>Remote & onsite support</li>
          <li>Incident root cause analysis</li>
        </ul>
      </div>

      <div class="skill-card">
        <div class="skill-icon">🌐</div>
        <h3>Networking</h3>
        <ul class="skill-list">
          <li>TCP/IP, DNS, DHCP, VPN</li>
          <li>Ping, traceroute, DNS resolution</li>
          <li>Network diagnostics & monitoring</li>
          <li>Enterprise LAN/WAN troubleshooting</li>
        </ul>
      </div>

      <div class="skill-card">
        <div class="skill-icon">☁️</div>
        <h3>Microsoft Azure</h3>
        <ul class="skill-list">
          <li>Virtual Machine deployment</li>
          <li>Azure AD / Identity basics</li>
          <li>AZ-104 track (in progress)</li>
          <li>Basic networking in Azure</li>
        </ul>
        <div class="badge-row">
          <span class="badge active">AZ-104 → In Progress</span>
        </div>
      </div>

      <div class="skill-card">
        <div class="skill-icon">☁️</div>
        <h3>AWS</h3>
        <ul class="skill-list">
          <li>EC2 instance basics</li>
          <li>S3 static website hosting</li>
          <li>IAM users, roles & policies</li>
        </ul>
        <div class="badge-row">
          <span class="badge active">Cloud Practitioner ✓</span>
        </div>
      </div>

      <div class="skill-card">
        <div class="skill-icon">⚙️</div>
        <h3>Tools & Automation</h3>
        <ul class="skill-list">
          <li>PowerShell scripting</li>
          <li>Linux fundamentals</li>
          <li>Basic infrastructure automation</li>
        </ul>
        <div class="badge-row">
          <span class="badge">PowerShell</span>
          <span class="badge">Linux</span>
          <span class="badge">Git</span>
        </div>
      </div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- EXPERIENCE / HANDS-ON -->
  <section id="experience">
    <p class="section-label">Hands-on labs</p>
    <h2>What I've Built<br>& Practiced</h2>

    <div class="timeline">
      <div class="timeline-item">
        <h3>Azure VM Deployment</h3>
        <p class="timeline-meta">Microsoft Azure · Lab</p>
        <p>Deployed and configured Azure Virtual Machines from scratch, including basic networking setup, access controls, and resource group management.</p>
      </div>
      <div class="timeline-item">
        <h3>Static Website on AWS S3</h3>
        <p class="timeline-meta">Amazon Web Services · Lab</p>
        <p>Hosted a static website using S3 with public bucket policies and static website hosting configuration. Explored CloudFront basics for CDN delivery.</p>
      </div>
      <div class="timeline-item">
        <h3>IAM User & Role Config</h3>
        <p class="timeline-meta">Amazon Web Services · Lab</p>
        <p>Created and managed IAM users, groups, roles, and policies following the principle of least privilege in AWS environments.</p>
      </div>
      <div class="timeline-item">
        <h3>Network Diagnostics</h3>
        <p class="timeline-meta">IT Support · Enterprise</p>
        <p>Hands-on enterprise troubleshooting using ping, traceroute, nslookup, and DNS resolution tools across multi-site networks. 8+ years of production experience.</p>
      </div>
      <div class="timeline-item">
        <h3>PowerShell Automation Scripts</h3>
        <p class="timeline-meta">IT Support · Automation</p>
        <p>Built basic PowerShell scripts to automate repetitive IT support tasks, including user provisioning and system health checks.</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- CERTS -->
  <section id="certs">
    <p class="section-label">Learning path</p>
    <h2>Certifications</h2>

    <div class="certs-grid">
      <div class="cert-card">
        <div class="cert-icon">☁️</div>
        <div>
          <h3>AWS Cloud Practitioner</h3>
          <p>Amazon Web Services</p>
          <span class="cert-status done">Completed</span>
        </div>
      </div>
      <div class="cert-card">
        <div class="cert-icon">🤖</div>
        <div>
          <h3>AWS AI Practitioner</h3>
          <p>Amazon Web Services</p>
          <span class="cert-status done">Completed</span>
        </div>
      </div>
      <div class="cert-card">
        <div class="cert-icon">🪟</div>
        <div>
          <h3>Microsoft 365 Fundamentals</h3>
          <p>Microsoft · MS-900</p>
          <span class="cert-status done">Completed</span>
        </div>
      </div>
      <div class="cert-card">
        <div class="cert-icon">🔵</div>
        <div>
          <h3>Azure Fundamentals</h3>
          <p>Microsoft · AZ-900</p>
          <span class="cert-status done">Completed</span>
        </div>
      </div>
      <div class="cert-card">
        <div class="cert-icon">🌐</div>
        <div>
          <h3>GCP Digital Leader</h3>
          <p>Google Cloud</p>
          <span class="cert-status done">Completed</span>
        </div>
      </div>
      <div class="cert-card">
        <div class="cert-icon">⚡</div>
        <div>
          <h3>Azure Administrator</h3>
          <p>Microsoft · AZ-104</p>
          <span class="cert-status progress">In Progress</span>
        </div>
      </div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- CONTACT -->
  <section id="contact">
    <p class="section-label">Let's connect</p>
    <h2>Open to Cloud<br>Engineering Roles</h2>
    <p class="contact-sub">
      I'm actively transitioning into cloud infrastructure and looking for opportunities
      to apply my IT background in AWS and Azure environments.
    </p>
    <div class="contact-links">
      <a href="mailto:austria.henricson26@gmail.com" class="btn btn-primary">✉ Email Me</a>
      <a href="https://linkedin.com/in/henricson-austria-a53aaa126" target="_blank" rel="noopener" class="btn btn-outline">LinkedIn</a>
    </div>
  </section>

  <footer>
    <p>© 2026 Henricson Austria &nbsp;·&nbsp; Built with HTML & CSS</p>
  </footer>

</body>
</html>
