# fire<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>My Clever Portal</title>

  <style>
    /* ====== Global Styles ====== */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    }

    body {
      background: #f5f7fb;
      color: #1f2933;
    }

    a {
      text-decoration: none;
      color: inherit;
    }

    img {
      max-width: 100%;
      display: block;
    }

    .page {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    /* ====== Top Navigation ====== */
    .navbar {
      height: 64px;
      background: #1f3b8c; /* dark blue */
      color: #ffffff;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 0 24px;
      box-shadow: 0 2px 4px rgba(15, 23, 42, 0.4);
    }

    .navbar-left {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .logo-circle {
      width: 32px;
      height: 32px;
      border-radius: 50%;
      background: #ffffff;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #1f3b8c;
      font-weight: 700;
      font-size: 18px;
    }

    .brand-text {
      font-weight: 600;
      letter-spacing: 0.02em;
    }

    .navbar-right {
      display: flex;
      align-items: center;
      gap: 16px;
      font-size: 14px;
    }

    .user-avatar {
      width: 32px;
      height: 32px;
      border-radius: 50%;
      background: #4f46e5;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 14px;
      font-weight: 600;
    }

    /* ====== Main Layout ====== */
    .main {
      flex: 1;
      padding: 24px;
      max-width: 1120px;
      margin: 0 auto;
      width: 100%;
    }

    .header-row {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      margin-bottom: 24px;
    }

    .page-title {
      font-size: 24px;
      font-weight: 700;
      color: #1f2937;
    }

    .subtitle {
      font-size: 14px;
      color: #6b7280;
      margin-top: 4px;
    }

    .search-box {
      position: relative;
      max-width: 260px;
      width: 100%;
    }

    .search-box input {
      width: 100%;
      padding: 8px 12px 8px 32px;
      border-radius: 999px;
      border: 1px solid #d1d5db;
      font-size: 14px;
      outline: none;
      transition: border-color 0.15s ease, box-shadow 0.15s ease;
    }

    .search-box input:focus {
      border-color: #4f46e5;
      box-shadow: 0 0 0 1px #4f46e5;
    }

    .search-icon {
      position: absolute;
      left: 10px;
      top: 50%;
      transform: translateY(-50%);
      font-size: 14px;
      color: #9ca3af;
    }

    /* ====== App Grid ====== */
    .apps-section {
      background: #ffffff;
      border-radius: 16px;
      padding: 20px;
      box-shadow: 0 10px 25px rgba(15, 23, 42, 0.08);
    }

    .apps-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 16px;
      gap: 8px;
      flex-wrap: wrap;
    }

    .apps-title {
      font-weight: 600;
      font-size: 16px;
      color: #111827;
    }

    .apps-count {
      font-size: 13px;
      color: #6b7280;
    }

    .apps-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
      gap: 16px;
    }

    .app-card {
      background: #f9fafb;
      border-radius: 12px;
      padding: 12px;
      border: 1px solid transparent;
      cursor: pointer;
      display: flex;
      flex-direction: column;
      gap: 8px;
      transition: transform 0.12s ease, box-shadow 0.12s ease, border-color 0.12s ease, background 0.12s ease;
    }

    .app-card:hover {
      transform: translateY(-2px);
      border-color: #4f46e5;
      box-shadow: 0 8px 16px rgba(15, 23, 42, 0.12);
      background: #ffffff;
    }

    .app-icon {
      width: 40px;
      height: 40px;
      border-radius: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: 700;
      color: #ffffff;
      font-size: 20px;
    }

    .app-name {
      font-size: 14px;
      font-weight: 600;
      color: #111827;
    }

    .app-desc {
      font-size: 12px;
      color: #6b7280;
    }

    .app-meta {
      font-size: 11px;
      color: #9ca3af;
      margin-top: 4px;
    }

    /* Icon colors */
    .bg-blue {
      background: linear-gradient(135deg, #3b82f6, #1d4ed8);
    }

    .bg-green {
      background: linear-gradient(135deg, #10b981, #059669);
    }

    .bg-purple {
      background: linear-gradient(135deg, #8b5cf6, #6d28d9);
    }

    .bg-amber {
      background: linear-gradient(135deg, #fbbf24, #d97706);
    }

    /* ====== Footer ====== */
    .footer {
      padding: 12px 24px 20px;
      font-size: 12px;
      color: #9ca3af;
      text-align: center;
    }

    /* ====== Responsive tweaks ====== */
    @media (max-width: 640px) {
      .navbar {
        padding: 0 16px;
      }

      .main {
        padding: 16px;
      }

      .apps-section {
        padding: 16px;
      }
    }
  </style>
</head>
<body>
  <div class="page">
    <!-- ====== NAVBAR ====== -->
    <header class="navbar">
      <div class="navbar-left">
        <div class="logo-circle">C</div>
        <div class="brand-text">My Clever Portal</div>
      </div>
      <div class="navbar-right">
        <span>Signed in as <strong>Nolan</strong></span>
        <div class="user-avatar">N</div>
      </div>
    </header>

    <!-- ====== MAIN CONTENT ====== -->
    <main class="main">
      <section class="header-row">
        <div>
          <h1 class="page-title">Your Learning Apps</h1>
          <p class="subtitle">Click an app below to open it in a new tab.</p>
        </div>

        <div class="search-box">
          <span class="search-icon">🔍</span>
          <input
            type="text"
            id="appSearch"
            placeholder="Search apps..."
            oninput="filterApps()"
          />
        </div>
      </section>

      <!-- Apps -->
      <section class="apps-section">
        <div class="apps-header">
          <div>
            <div class="apps-title">All Apps</div>
            <div class="apps-count" id="appsCount">6 apps</div>
          </div>
        </div>

        <div class="apps-grid" id="appsGrid">
          <!-- Example App Cards -->
          <a
            class="app-card"
            href="https://classroom.google.com"
            target="_blank"
            data-name="Google Classroom"
          >
            <div class="app-icon bg-green">C</div>
            <div class="app-name">Google Classroom</div>
            <div class="app-desc">Assignments, announcements, and class discussions.</div>
            <div class="app-meta">Education · Single sign‑on</div>
          </a>

          <a
            class="app-card"
            href="https://drive.google.com"
            target="_blank"
            data-name="Google Drive"
          >
            <div class="app-icon bg-blue">D</div>
            <div class="app-name">Google Drive</div>
            <div class="app-desc">Store and share files, docs, slides, and more.</div>
            <div class="app-meta">Storage · Files</div>
          </a>

          <a
            class="app-card"
            href="https://quizlet.com"
            target="_blank"
            data-name="Quizlet"
          >
            <div class="app-icon bg-purple">Q</div>
            <div class="app-name">Quizlet</div>
            <div class="app-desc">Flashcards and study tools to help you review.</div>
            <div class="app-meta">Study · Practice</div>
          </a>

          <a
            class="app-card"
            href="https://kahoot.it"
            target="_blank"
            data-name="Kahoot!"
          >
            <div class="app-icon bg-amber">K</div>
            <div class="app-name">Kahoot!</div>
            <div class="app-desc">Interactive quizzes and games in the classroom.</div>
            <div class="app-meta">Games · Live</div>
          </a>

          <a
            class="app-card"
            href="https://www.khanacademy.org"
            target="_blank"
            data-name="Khan Academy"
          >
            <div class="app-icon bg-blue">K</div>
            <div class="app-name">Khan Academy</div>
            <div class="app-desc">Learn math, science, and more at your own pace.</div>
            <div class="app-meta">Math · Science</div>
          </a>

          <a
            class="app-card"
            href="https://login.i-ready.com"
            target="_blank"
            data-name="i-Ready"
          >
            <div class="app-icon bg-green">i</div>
            <div class="app-name">i‑Ready</div>
            <div class="app-desc">Personalized instruction in reading and math.</div>
            <div class="app-meta">Assessment · Learning</div>
          </a>
        </div>
      </section>
    </main>

    <!-- ====== FOOTER ====== -->
    <footer class="footer">
      © <span id="year"></span> My Clever Portal · Not affiliated with Clever, Inc.
    </footer>
  </div>

  <script>
    // Set current year in footer
    document.getElementById("year").textContent = new Date().getFullYear();

    // Simple app search / filter
    function filterApps() {
      const query = document.getElementById("appSearch").value.toLowerCase();
      const cards = document.querySelectorAll(".app-card");
      let visibleCount = 0;

      cards.forEach((card) => {
        const name = card.dataset.name.toLowerCase();
        const matches = name.includes(query);
        card.style.display = matches ? "flex" : "none";
        if (matches) visibleCount++;
      });

      const appsCount = document.getElementById("appsCount");
      appsCount.textContent = `${visibleCount} app${visibleCount === 1 ? "" : "s"}`;
    }
  </script>
</body>
</html>
