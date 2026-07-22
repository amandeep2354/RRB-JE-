<html lang="hi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>RRB JE Official Preparation Portal - Founder Amandeep</title>
  <style>
    :root {
      --primary: #0d6efd;
      --primary-dark: #0a58ca;
      --bg-color: #f4f7fe;
      --text-color: #2b3674;
      --correct-bg: #d4edda;
      --correct-border: #28a745;
      --correct-text: #155724;
      --wrong-bg: #f8d7da;
      --wrong-border: #dc3545;
      --wrong-text: #721c24;
    }

    * { box-sizing: border-box; font-family: 'Segoe UI', system-ui, -apple-system, sans-serif; margin: 0; padding: 0; }
    body { background-color: var(--bg-color); color: var(--text-color); display: flex; flex-direction: column; min-height: 100vh; }

    /* Auth Modal */
    #auth-overlay {
      position: fixed; top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(13, 27, 62, 0.85); backdrop-filter: blur(8px);
      display: flex; justify-content: center; align-items: center; z-index: 9999;
    }
    .auth-card {
      background: white; padding: 35px; border-radius: 16px; width: 90%; max-width: 400px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.2); text-align: center;
    }
    .auth-card h2 { margin-bottom: 8px; color: var(--primary); }
    .auth-card p { color: #666; margin-bottom: 20px; font-size: 14px; }
    .form-group { margin-bottom: 15px; text-align: left; }
    .form-group label { display: block; margin-bottom: 5px; font-weight: 600; font-size: 13px; color: #444; }
    .form-group input {
      width: 100%; padding: 12px; border: 1px solid #ccc; border-radius: 8px; font-size: 14px; outline: none;
    }
    .form-group input:focus { border-color: var(--primary); box-shadow: 0 0 0 3px rgba(13,110,253,0.15); }
    .btn {
      width: 100%; padding: 12px; border: none; border-radius: 8px; background: var(--primary);
      color: white; font-size: 15px; font-weight: 600; cursor: pointer; transition: 0.2s;
    }
    .btn:hover { background: var(--primary-dark); }
    .btn-danger { background: #dc3545; }
    .btn-danger:hover { background: #bb2d3b; }
    .btn-sm { padding: 6px 12px; font-size: 12px; width: auto; }

    /* Main Dashboard Layout */
    #app-container { display: none; flex-direction: column; min-height: 100vh; }
    header {
      background: white; border-bottom: 1px solid #e0e0e0; padding: 15px 30px;
      display: flex; justify-content: space-between; align-items: center; position: sticky; top: 0; z-index: 100;
    }
    .logo-area { display: flex; align-items: center; gap: 10px; }
    .logo-badge { background: var(--primary); color: white; padding: 6px 12px; border-radius: 6px; font-weight: bold; }
    
    nav { background: white; border-bottom: 1px solid #e0e0e0; display: flex; justify-content: center; gap: 15px; padding: 0 20px; overflow-x: auto; }
    .nav-tab {
      padding: 15px 20px; border: none; background: none; font-weight: 600; color: #666;
      cursor: pointer; border-bottom: 3px solid transparent; transition: 0.2s; font-size: 14px; white-space: nowrap;
    }
    .nav-tab.active { color: var(--primary); border-bottom-color: var(--primary); }

    main { max-width: 1100px; width: 100%; margin: 25px auto; padding: 0 20px; flex: 1; }
    .tab-content { display: none; }
    .tab-content.active { display: block; }

    /* Cards Grid */
    .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; }
    .card {
      background: white; border-radius: 12px; padding: 20px; border: 1px solid #e2e8f0;
      box-shadow: 0 4px 12px rgba(0,0,0,0.03); transition: transform 0.2s;
    }
    .card:hover { transform: translateY(-3px); }
    .badge { display: inline-block; padding: 4px 8px; border-radius: 4px; font-size: 11px; font-weight: bold; margin-bottom: 10px; margin-right: 5px; }
    .badge-shift { background: #e0f2fe; color: #0369a1; }
    .badge-easy { background: #dcfce7; color: #15803d; }
    .badge-medium { background: #fef9c3; color: #a16207; }
    .badge-hard { background: #fee2e2; color: #b91c1c; }

    /* Profile Section Custom Styling */
    .profile-card {
      background: linear-gradient(135deg, #ffffff 0%, #f8fafc 100%);
      border-radius: 16px; padding: 30px; border: 1px solid #cbd5e1;
      box-shadow: 0 10px 25px rgba(0,0,0,0.05); margin-bottom: 25px;
      display: flex; flex-wrap: wrap; gap: 30px; align-items: center;
    }
    .profile-img-box {
      width: 170px; height: 200px; border-radius: 14px; overflow: hidden;
      border: 4px solid var(--primary); box-shadow: 0 8px 20px rgba(13,110,253,0.25); flex-shrink: 0;
    }
    .profile-img-box img { width: 100%; height: 100%; object-fit: cover; }
    .profile-info { flex: 1; min-width: 280px; }
    .profile-info h2 { font-size: 28px; color: #0f172a; margin-bottom: 6px; }
    .profile-tagline { font-size: 15px; color: var(--primary); font-weight: 600; margin-bottom: 15px; }
    .info-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 12px; margin-top: 15px; }
    .info-item { background: #f1f5f9; padding: 10px 14px; border-radius: 8px; font-size: 14px; border-left: 3px solid var(--primary); }

    /* Test View */
    .test-header {
      background: white; padding: 15px 20px; border-radius: 10px; display: flex;
      justify-content: space-between; align-items: center; margin-bottom: 20px; border: 1px solid #ddd;
    }
    .timer { font-size: 18px; font-weight: bold; color: #dc3545; background: #fff5f5; padding: 6px 14px; border-radius: 6px; border: 1px solid #fecaca; }
    .q-card { background: white; padding: 20px; border-radius: 10px; margin-bottom: 15px; border: 1px solid #e0e0e0; }
    .options label {
      display: block; padding: 12px 15px; margin: 8px 0; background: #f8fafc; border: 1px solid #cbd5e1;
      border-radius: 8px; cursor: pointer; transition: 0.2s; font-size: 14px;
    }
    .options label:hover { background: #f1f5f9; border-color: var(--primary); }

    /* Result Highlights */
    .correct-ans { background-color: var(--correct-bg) !important; border-color: var(--correct-border) !important; color: var(--correct-text) !important; font-weight: bold; }
    .wrong-ans { background-color: var(--wrong-bg) !important; border-color: var(--wrong-border) !important; color: var(--wrong-text) !important; font-weight: bold; }

    /* Result Scorecard */
    .result-box { background: white; padding: 25px; border-radius: 12px; border: 2px solid var(--primary); margin-top: 25px; }
    .result-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 15px; margin: 20px 0; }
    .result-item { background: #f8fafc; padding: 15px; border-radius: 8px; text-align: center; border: 1px solid #e2e8f0; }
    .result-item span { display: block; font-size: 20px; font-weight: bold; margin-top: 5px; color: var(--primary); }

    /* Tables */
    table { width: 100%; border-collapse: collapse; background: white; border-radius: 8px; overflow: hidden; margin-top: 15px; }
    th, td { padding: 12px 15px; text-align: left; border-bottom: 1px solid #e2e8f0; font-size: 14px; }
    th { background: #f8fafc; font-weight: 600; color: #475569; }

    /* Footer */
    .live-status { background: #1e293b; color: white; padding: 15px 30px; text-align: center; font-size: 13px; margin-top: auto; }
  </style>
</head>
<body>

  <!-- LOGIN OVERLAY -->
  <div id="auth-overlay">
    <div class="auth-card">
      <h2>RRB JE Login Portal</h2>
      <p>Enter your credentials to access test series & PDFs</p>
      <form id="login-form" onsubmit="handleLogin(event)">
        <div class="form-group">
          <label>Username / Phone Number</label>
          <input type="text" id="login-phone" placeholder="9518290278" required>
        </div>
        <div class="form-group">
          <label>Password</label>
          <input type="password" id="login-pass" placeholder="12345678" required>
        </div>
        <button type="submit" class="btn">Login to Portal</button>
      </form>
    </div>
  </div>

  <!-- MAIN CONTAINER -->
  <div id="app-container">
    <header>
      <div class="logo-area">
        <span class="logo-badge">RRB JE</span>
        <h3 style="font-size: 16px;">Previous Shift & Mock Portal</h3>
      </div>
      <div>
        <span id="user-display" style="font-size: 14px; font-weight: 600; margin-right: 15px;">👤 User</span>
        <button class="btn btn-sm btn-danger" onclick="logout()">Logout</button>
      </div>
    </header>

    <nav>
      <button class="nav-tab active" onclick="switchTab('home')">📄 Shift PDFs (Home)</button>
      <button class="nav-tab" onclick="switchTab('tests')">📝 RRB JE Test Series</button>
      <button class="nav-tab" onclick="switchTab('history')">📊 Scorecard & History</button>
      <button class="nav-tab" onclick="switchTab('about')">👨‍💻 About Creator</button>
      <button class="nav-tab" onclick="switchTab('settings')">⚙️ Account Settings</button>
    </nav>

    <main>
      <!-- TAB 1: HOME (PDFs) -->
      <div id="tab-home" class="tab-content active">
        <h2>RRB JE Previous Year Question Papers (Shift Wise)</h2>
        <p style="color: #64748b; margin-top: 5px;">Download official previous shift papers in PDF format.</p>
        <div class="grid">
          <div class="card">
            <span class="badge badge-shift">2024 CBT-1 Official</span>
            <h3>RRB JE 2024 - Shift 1 (All Subjects)</h3>
            <p>100 Questions | CBT-1 Official Shift Questions with Key solutions.</p>
            <button class="btn btn-sm" onclick="downloadPDF('RRB_JE_2024_Shift1.pdf')">📥 Download PDF</button>
          </div>
          <div class="card">
            <span class="badge badge-shift">2024 CBT-1 Official</span>
            <h3>RRB JE 2024 - Shift 2 (All Subjects)</h3>
            <p>100 Questions | Mechanical & Electrical General Science focus.</p>
            <button class="btn btn-sm" onclick="downloadPDF('RRB_JE_2024_Shift2.pdf')">📥 Download PDF</button>
          </div>
        </div>
      </div>

      <!-- TAB 2: TEST SERIES -->
      <div id="tab-tests" class="tab-content">
        <div id="test-list-view">
          <h2>RRB JE CBT-1 Active Shift Tests</h2>
          <p style="color: #64748b; margin-top: 5px;">Adaptive Tests: Questions arranged from Easy ➔ Medium ➔ Hardest level.</p>
          <div class="grid">
            <div class="card">
              <span class="badge badge-easy">Progressive Level</span>
              <span class="badge badge-shift">Shift 1 - 2024 Special</span>
              <h3>RRB JE CBT-1 Full Shift Test 1</h3>
              <p>Maths, Reasoning, GA, Science. Total 12 Questions arranged by difficulty.</p>
              <button class="btn" onclick="startTest(0)">Start Live Test</button>
            </div>
          </div>
        </div>

        <!-- LIVE TEST VIEW -->
        <div id="test-active-view" style="display: none;">
          <div class="test-header">
            <div>
              <h3 id="active-test-title">RRB JE Live Exam</h3>
              <small id="active-test-info" style="color: #666;">Progressive Order: Easy -> Medium -> Hard</small>
            </div>
            <div class="timer" id="test-timer">Time: 10:00</div>
          </div>

          <form id="active-test-form">
            <div id="questions-container"></div>
            <button type="button" class="btn" id="submit-test-btn" onclick="submitActiveTest()" style="margin-top: 20px;">Submit Exam</button>
          </form>

          <!-- RESULT SCORECARD -->
          <div id="test-result-box" class="result-box" style="display: none;">
            <h2 style="color: var(--primary); text-align: center;">🎉 Test Completed - Performance Summary</h2>
            <div class="result-grid">
              <div class="result-item">Total Questions<span id="res-total">0</span></div>
              <div class="result-item">Attempted<span id="res-attempted" style="color: blue;">0</span></div>
              <div class="result-item">Correct<span id="res-correct" style="color: green;">0</span></div>
              <div class="result-item">Incorrect<span id="res-incorrect" style="color: red;">0</span></div>
              <div class="result-item">Final Score<span id="res-score">0</span></div>
              <div class="result-item">Percentage<span id="res-percentage">0%</span></div>
              <div class="result-item">All India Rank (Est)<span id="res-rank" style="color: purple;">AIR #0</span></div>
            </div>
            <div style="text-align: center; margin-top: 15px;">
              <button class="btn btn-sm" onclick="exitTest()">Return to Tests List</button>
            </div>
          </div>
        </div>
      </div>

      <!-- TAB 3: HISTORY -->
      <div id="tab-history" class="tab-content">
        <h2>Your Test History & Performance Scorecard</h2>
        <div id="history-container">
          <table>
            <thead>
              <tr>
                <th>Date & Time</th>
                <th>Test Name</th>
                <th>Score</th>
                <th>Percentage</th>
                <th>Estimated Rank</th>
                <th>Action</th>
              </tr>
            </thead>
            <tbody id="history-tbody"></tbody>
          </table>
        </div>
      </div>

      <!-- TAB 4: ABOUT CREATOR -->
      <div id="tab-about" class="tab-content">
        <div class="profile-card">
          <div class="profile-img-box">
            <!-- EMBEDDED PHOTO -->
            <img src="your_image_base64_or_path_here" alt="Amandeep - Founder & Developer">
          </div>
          <div class="profile-info">
            <h2>Amandeep</h2>
            <div class="profile-tagline">Founder, Portal Developer & RRB JE Aspirant</div>
            <div>
              <span class="badge badge-easy">Web Developer</span>
              <span class="badge badge-shift">RRB JE Portal Founder</span>
              <span class="badge badge-hard">Kelnian, Sirsa</span>
            </div>
            
            <div class="info-grid">
              <div class="info-item">👤 <strong>Name:</strong> Amandeep</div>
              <div class="info-item">🎂 <strong>Age:</strong> 22 Years</div>
              <div class="info-item">📞 <strong>Phone:</strong> 95182 90278</div>
              <div class="info-item">📧 <strong>Email:</strong> amandeep83403@gmail.com</div>
              <div class="info-item" style="grid-column: span 2;">📍 <strong>Address:</strong> Kelnian, Sirsa (Haryana)</div>
            </div>
          </div>
        </div>

        <div class="card" style="margin-top: 20px;">
          <h3 style="color: var(--primary); margin-bottom: 10px;">🌟 About Amandeep & Portal Mission</h3>
          <p style="font-size: 14px; line-height: 1.7; color: #334155;">
            Mera naam <strong>Amandeep</strong> hai aur main <strong>Kelnian (Sirsa, Haryana)</strong> ka rehne wala hoon. Maine yeh RRB JE Exam Preparation Web Portal khaas taur par railway competitive exams ki taiyari kar rahe sabhi students ke liye design aur develop kiya hai.
          </p>
        </div>
      </div>

      <!-- TAB 5: SETTINGS -->
      <div id="tab-settings" class="tab-content">
        <h2>Account Settings</h2>
        <div class="card" style="max-width: 500px; margin-top: 20px;">
          <form onsubmit="updateProfile(event)">
            <div class="form-group">
              <label>Username / Phone Number</label>
              <input type="text" id="setting-phone" required>
            </div>
            <div class="form-group">
              <label>New Password</label>
              <input type="password" id="setting-pass" required>
            </div>
            <button type="submit" class="btn">Update Credentials</button>
          </form>
        </div>
      </div>
    </main>

    <div class="live-status">
      RRB JE Exam Preparation System | Developed by Amandeep (Sirsa, Haryana)
    </div>
  </div>
</body>
</html>
