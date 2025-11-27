<html lang="th">
<head>
  <meta charset="UTF-8" />
  <title>BR Morning Navigator v2</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <!-- ฟอนต์ -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link
    href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;600&display=swap"
    rel="stylesheet"
  />

  <style>
    * {
      box-sizing: border-box;
      font-family: "Kanit", system-ui, -apple-system, BlinkMacSystemFont,
        "Segoe UI", sans-serif;
    }

    body {
      margin: 0;
      padding: 0;
      background: radial-gradient(circle at top, #fff3e0, #e3f2fd 45%, #ede7f6);
      min-height: 100vh;
      color: #222;
    }

    .app {
      max-width: 1000px;
      margin: 0 auto;
      padding: 16px 16px 24px;
    }

    header {
      background: #ffffffee;
      backdrop-filter: blur(12px);
      border-radius: 24px;
      padding: 16px 18px;
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      gap: 16px;
      box-shadow: 0 12px 24px rgba(0, 0, 0, 0.06);
      position: sticky;
      top: 0;
      z-index: 10;
    }

    .logo-circle {
      width: 60px;
      height: 60px;
      border-radius: 50%;
      background: radial-gradient(circle at 30% 20%, #ffe082, #ffb74d);
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: 700;
      color: #4e342e;
      font-size: 20px;
      box-shadow: 0 5px 14px rgba(255, 183, 77, 0.7);
      flex-shrink: 0;
    }

    header h1 {
      margin: 0;
      font-size: 22px;
      font-weight: 600;
    }

    header p {
      margin: 2px 0 0;
      font-size: 13px;
      color: #555;
    }

    @media (max-width: 640px) {
      header {
        flex-direction: row;
        align-items: flex-start;
      }
    }

    /* แถบเมนู */
    .tab-bar {
      margin-top: 8px;
      display: inline-flex;
      background: #f3f5ff;
      border-radius: 999px;
      padding: 3px;
      gap: 4px;
    }

    .tab-btn {
      border: none;
      border-radius: 999px;
      padding: 6px 14px;
      font-size: 12px;
      cursor: pointer;
      background: transparent;
      color: #555;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      transition: background 0.2s, color 0.2s, box-shadow 0.2s;
    }

    .tab-btn.active {
      background: #ffffff;
      color: #1e88e5;
      box-shadow: 0 2px 8px rgba(30, 136, 229, 0.2);
    }

    .tab-btn span.icon {
      font-size: 14px;
    }

    main {
      margin-top: 14px;
    }

    .view {
      display: none;
      animation: fadeIn 0.25s ease-out;
    }

    .view.active {
      display: block;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(4px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .card {
      background: #ffffffee;
      backdrop-filter: blur(10px);
      border-radius: 22px;
      padding: 16px 18px 18px;
      box-shadow: 0 10px 22px rgba(0, 0, 0, 0.06);
      margin-bottom: 14px;
    }

    .card h2 {
      margin: 0 0 8px;
      font-size: 18px;
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .card p.lead {
      font-size: 13px;
      color: #666;
      margin: 0 0 6px;
    }

    .pill {
      display: inline-flex;
      align-items: center;
      gap: 4px;
      padding: 3px 8px;
      border-radius: 999px;
      font-size: 11px;
      background: #e3f2fd;
      color: #1565c0;
      margin-bottom: 4px;
    }

    label {
      display: block;
      font-size: 13px;
      margin-bottom: 3px;
    }

    input[type="time"],
    input[type="number"],
    select {
      width: 100%;
      padding: 8px 10px;
      border-radius: 12px;
      border: 1px solid #d0d7e2;
      font-size: 13px;
      outline: none;
      background: #fafbff;
      transition: border-color 0.2s, box-shadow 0.2s, background 0.2s;
    }

    input[type="time"]:focus,
    input[type="number"]:focus,
    select:focus {
      border-color: #42a5f5;
      background: #ffffff;
      box-shadow: 0 0 0 3px rgba(66, 165, 245, 0.16);
    }

    .form-row {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 10px;
      margin-bottom: 10px;
    }

    .form-row-3 {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 10px;
      margin-bottom: 10px;
    }

    @media (max-width: 720px) {
      .form-row,
      .form-row-3 {
        grid-template-columns: minmax(0, 1fr);
      }
    }

    button.primary {
      border: none;
      border-radius: 999px;
      padding: 9px 18px;
      font-size: 14px;
      cursor: pointer;
      background: linear-gradient(135deg, #42a5f5, #7e57c2);
      color: #fff;
      font-weight: 600;
      box-shadow: 0 7px 18px rgba(66, 165, 245, 0.55);
      display: inline-flex;
      align-items: center;
      gap: 6px;
      margin-top: 4px;
    }

    button.primary:active {
      transform: translateY(1px);
      box-shadow: 0 4px 12px rgba(66, 165, 245, 0.55);
    }

    button.secondary {
      border: none;
      border-radius: 999px;
      padding: 7px 14px;
      font-size: 12px;
      cursor: pointer;
      background: #f3f5ff;
      color: #3949ab;
      font-weight: 500;
      margin-top: 8px;
    }

    .result-time {
      font-size: 24px;
      font-weight: 600;
      margin: 4px 0;
    }

    .subnote {
      font-size: 11px;
      color: #777;
    }

    .chip {
      display: inline-flex;
      align-items: center;
      gap: 4px;
      padding: 4px 8px;
      border-radius: 999px;
      background: #e3f2fd;
      color: #1565c0;
      font-size: 11px;
      font-weight: 500;
      margin-right: 4px;
      margin-bottom: 4px;
    }

    .chip.late {
      background: #ffebee;
      color: #c62828;
    }

    .chip.good {
      background: #e8f5e9;
      color: #2e7d32;
    }

    .score-bar-wrap {
      margin-top: 8px;
    }

    .score-label {
      font-size: 13px;
      margin-bottom: 4px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .score-bar {
      width: 100%;
      height: 10px;
      border-radius: 999px;
      background: #e0e0e0;
      overflow: hidden;
    }

    .score-fill {
      height: 100%;
      width: 0%;
      border-radius: 999px;
      background: linear-gradient(90deg, #66bb6a, #ffca28, #ef5350);
      transition: width 0.35s ease-out;
    }

    .message {
      font-size: 13px;
      margin-top: 8px;
    }

    .message strong {
      font-weight: 600;
    }

    .mission-box {
      margin-top: 8px;
      padding: 10px 12px;
      border-radius: 14px;
      background: #fff3e0;
      font-size: 13px;
    }

    .badge-list {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-top: 6px;
    }

    .badge {
      padding: 4px 8px;
      border-radius: 999px;
      font-size: 11px;
      background: #ede7f6;
      color: #5e35b1;
      display: inline-flex;
      align-items: center;
      gap: 4px;
    }

    .badge.locked {
      opacity: 0.4;
    }

    /* สถิติ */
    .stat-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 10px;
      margin-top: 8px;
      margin-bottom: 10px;
    }

    @media (max-width: 720px) {
      .stat-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }
    }

    @media (max-width: 480px) {
      .stat-grid {
        grid-template-columns: minmax(0, 1fr);
      }
    }

    .stat-card {
      border-radius: 16px;
      padding: 10px 12px;
      background: #f3f5ff;
      font-size: 12px;
    }

    .stat-label {
      color: #5c6bc0;
      font-size: 11px;
    }

    .stat-value {
      font-size: 18px;
      font-weight: 600;
      margin-top: 2px;
    }

    .history-list {
      margin-top: 8px;
      max-height: 220px;
      overflow-y: auto;
      border-radius: 12px;
      border: 1px solid #e0e0e0;
      background: #fafafa;
    }

    .history-item {
      padding: 8px 10px;
      border-bottom: 1px solid #e0e0e0;
      font-size: 12px;
      display: flex;
      justify-content: space-between;
      gap: 8px;
    }

    .history-item:last-child {
      border-bottom: none;
    }

    .history-date {
      font-weight: 500;
      color: #3949ab;
    }

    .history-meta {
      text-align: right;
      white-space: nowrap;
      color: #555;
    }

    .history-meta span {
      display: block;
    }

    .tag-late {
      color: #c62828;
      font-weight: 600;
      font-size: 11px;
    }

    .tag-on-time {
      color: #2e7d32;
      font-weight: 600;
      font-size: 11px;
    }

    /* หน้า Info */
    .info-list {
      margin-top: 6px;
      padding-left: 18px;
      font-size: 13px;
    }

    footer {
      text-align: center;
      font-size: 11px;
      color: #777;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <div class="app">
    <header>
      <div class="logo-circle">BR</div>
      <div>
        <h1>BR Morning Navigator</h1>
        <p>
          นวัตกรรมเว็บแอพช่วยวางแผนเวลาไปโรงเรียน &amp; เกมสร้างนิสัยไม่มาสาย
          สำหรับนักเรียนเบญจมราชาลัย
        </p>
        <div class="tab-bar" id="tabBar">
          <button class="tab-btn active" data-view="todayView">
            <span class="icon">🌤</span> วันนี้
          </button>
          <button class="tab-btn" data-view="statsView">
            <span class="icon">📊</span> สถิติ &amp; พฤติกรรม
          </button>
          <button class="tab-btn" data-view="badgesView">
            <span class="icon">🏅</span> แบดจ์ &amp; ภารกิจ
          </button>
          <button class="tab-btn" data-view="infoView">
            <span class="icon">💡</span> เกี่ยวกับนวัตกรรม
          </button>
        </div>
      </div>
    </header>

    <main>
      <!-- View: วันนี้ -->
      <section class="view active" id="todayView">
        <div class="card">
          <h2>🕒 ตั้งค่าการเดินทางของวันนี้</h2>
          <p class="lead">
            ระบบจะช่วยคำนวณเวลาออกจากบ้านที่เหมาะสม ประเมินความเสี่ยงมาสาย และให้คะแนนวินัยประจำวัน
          </p>
          <span class="pill">วันนี้: <span id="todayDate"></span></span>

          <h3 style="margin:10px 0 6px;">1) ข้อมูลพื้นฐาน</h3>
          <div class="form-row">
            <div>
              <label for="arrivalTime">ต้องถึงโรงเรียนไม่เกินเวลา</label>
              <input type="time" id="arrivalTime" value="07:40" />
              <span class="subnote">เช่น เวลาเข้าแถว หรือเวลาเคารพธงชาติ</span>
            </div>
            <div>
              <label for="baseTravel">เวลาเดินทางปกติ (นาที)</label>
              <input type="number" id="baseTravel" min="5" max="180" value="45" />
              <span class="subnote">เวลาจากบ้านถึงโรงเรียนในวันที่รถไม่ติด</span>
            </div>
          </div>

          <h3 style="margin:10px 0 6px;">2) สภาพการเดินทางวันนี้</h3>
          <div class="form-row-3">
            <div>
              <label for="trafficLevel">ระดับรถติด</label>
              <select id="trafficLevel">
                <option value="0">ปกติ</option>
                <option value="0.15">ติดเล็กน้อย</option>
                <option value="0.3">ติดมาก</option>
              </select>
            </div>
            <div>
              <label for="weather">สภาพอากาศ</label>
              <select id="weather">
                <option value="0">ปกติ</option>
                <option value="0.1">ฝนปรอย ๆ</option>
                <option value="0.2">ฝนตกหนัก</option>
              </select>
            </div>
            <div>
              <label for="buffer">เผื่อเวลาเพิ่ม (นาที)</label>
              <input type="number" id="buffer" min="0" max="60" value="10" />
            </div>
          </div>

          <h3 style="margin:10px 0 6px;">3) พฤติกรรมตอนเช้า</h3>
          <div class="form-row">
            <div>
              <label for="wakeTime">เวลาที่ตื่นจริงวันนี้</label>
              <input type="time" id="wakeTime" value="06:00" />
            </div>
            <div>
              <label for="prepMinutes">เวลาเตรียมตัวตอนเช้า (นาที)</label>
              <input type="number" id="prepMinutes" min="10" max="120" value="30" />
            </div>
          </div>

          <button class="primary" id="calcBtn">
            🧮 คำนวณเวลาออกจากบ้านที่เหมาะสม
          </button>
        </div>

        <div class="card">
          <h2>🌤 ผลการวางแผนวันนี้</h2>
          <div>
            <label style="font-size:13px;">ควรออกจากบ้านไม่เกินเวลา</label>
            <div class="result-time" id="recommendedLeave">—:—</div>
            <div class="subnote">คำนวณจากสภาพการจราจร อากาศ และพฤติกรรมของวันนี้</div>
            <div style="margin-top:6px;">
              <span class="chip" id="etaChip" style="display:none;"></span>
              <span class="chip" id="riskChip" style="display:none;"></span>
            </div>
          </div>

          <div class="score-bar-wrap">
            <div class="score-label">
              <span>คะแนนวินัยวันนี้</span>
              <span id="scoreText">0 / 100</span>
            </div>
            <div class="score-bar">
              <div class="score-fill" id="scoreFill"></div>
            </div>
          </div>

          <div class="message" id="messageBox">
            ใส่ข้อมูลด้านบนแล้วกดปุ่มคำนวณ เพื่อดูคำแนะนำของวันนี้ค่ะ 💡
          </div>

          <div class="mission-box" id="missionBox">
            🎮 <strong>ภารกิจวันนี้:</strong> —
          </div>

          <button class="secondary" id="saveDayBtn">
            💾 บันทึกข้อมูลวันนี้ (เก็บไว้ดูสถิติ)
          </button>
        </div>
      </section>

      <!-- View: สถิติ -->
      <section class="view" id="statsView">
        <div class="card">
          <h2>📊 สถิติ &amp; พฤติกรรมการตื่นเช้า</h2>
          <p class="lead">
            ระบบจะรวบรวมข้อมูลวันที่คุณกดบันทึก เพื่อติดตามการเปลี่ยนแปลงพฤติกรรมการมาสาย / มาเช้า
          </p>

          <div class="stat-grid">
            <div class="stat-card">
              <div class="stat-label">จำนวนวันที่บันทึก</div>
              <div class="stat-value" id="statDays">0</div>
              <div class="subnote">ยิ่งบันทึกบ่อย ยิ่งเห็นพัฒนาการชัดเจน</div>
            </div>
            <div class="stat-card">
              <div class="stat-label">คะแนนเฉลี่ย</div>
              <div class="stat-value" id="statAvgScore">0</div>
              <div class="subnote">จากคะแนนวินัยเต็ม 100</div>
            </div>
            <div class="stat-card">
              <div class="stat-label">อัตรามาตรงเวลา</div>
              <div class="stat-value" id="statOnTimeRate">0%</div>
              <div class="subnote">มาถึงก่อน/ตรงเวลาตามเป้าหมาย</div>
            </div>
          </div>

          <h3 style="margin:8px 0 6px;">บันทึกย้อนหลัง (ล่าสุด)</h3>
          <div class="history-list" id="historyList">
            <div class="history-item">
              <div>ยังไม่มีข้อมูล กรุณาลองคำนวณและกด "บันทึกข้อมูลวันนี้" ก่อนค่ะ</div>
            </div>
          </div>
        </div>
      </section>

      <!-- View: แบดจ์ -->
      <section class="view" id="badgesView">
        <div class="card">
          <h2>🏅 แบดจ์นิสัยไม่มาสาย</h2>
          <p class="lead">
            เมื่อบันทึกข้อมูลหลายวัน ระบบจะช่วยดูว่าคุณเข้าเงื่อนไขแบดจ์ไหนแล้วบ้าง (เช่น คะแนนดีต่อเนื่อง หรือไม่มาสาย)
          </p>
          <div class="badge-list" id="badgeList">
            <div class="badge locked" data-badge="early">
              🌅 Early Bird — มาเช้าอย่างน้อย 3 วัน จากวันที่บันทึก
            </div>
            <div class="badge locked" data-badge="perfectWeek">
              🚀 Zero Late Week — ไม่มาสายเลย 5 วันติดกัน
            </div>
            <div class="badge locked" data-badge="improve">
              🌈 Improvement Hero — คะแนนเฉลี่ยสัปดาห์หลัง สูงกว่าสัปดาห์แรก ≥ 15 คะแนน
            </div>
          </div>

          <button class="secondary" id="refreshBadgesBtn">
            🔄 อัปเดตสถานะแบดจ์จากข้อมูลล่าสุด
          </button>
        </div>

        <div class="card">
          <h2>🎮 ไอเดียใช้ในห้องเรียน</h2>
          <ul class="info-list">
            <li>ครูให้คะแนนพฤติกรรมเพิ่มเมื่อนักเรียนปลดล็อกแบดจ์บางประเภท</li>
            <li>แข่งระดับห้อง: ห้องที่มีอัตรามาตรงเวลารวมสูงสุดในเดือนนั้น ได้รับสิทธิ์พิเศษ</li>
            <li>ใช้ข้อมูลจริงในการสะท้อนคิด (Reflection) เรื่องนิสัยการจัดการเวลา</li>
          </ul>
        </div>
      </section>

      <!-- View: เกี่ยวกับนวัตกรรม -->
      <section class="view" id="infoView">
        <div class="card">
          <h2>💡 เกี่ยวกับ BR Morning Navigator</h2>
          <p class="lead">
            นวัตกรรมนี้ออกแบบมาเพื่อแก้ปัญหานักเรียนมาสาย ด้วยแนวคิด
            <strong>Personalized Planning + Gamification + Data for Reflection</strong>
          </p>
          <ul class="info-list">
            <li><strong>ระดับปัญหา:</strong> นักเรียนจำนวนหนึ่งมาสายซ้ำ ๆ เพราะไม่เห็นผลกระทบจริง และไม่รู้วิธีจัดการเวลา</li>
            <li><strong>แนวคิดหลัก:</strong> ให้ผู้เรียนเห็นเวลาเดินทางที่ “เหมาะสมสำหรับตัวเอง” ในแต่ละวัน พร้อมเกม/คะแนนที่สะท้อนพฤติกรรม</li>
            <li><strong>จุดเด่น:</strong> ไม่ใช่ระบบลงโทษ แต่เป็นเครื่องมือช่วยวางแผน + สะท้อนคิด + เสริมแรงเชิงบวก</li>
            <li><strong>เทคโนโลยี:</strong> HTML/CSS/JavaScript (สามารถต่อยอดเชื่อม API, AppSheet หรือ Firebase ได้)</li>
            <li><strong>การใช้จริงในโรงเรียน:</strong> ใช้ในรายวิชาทักษะชีวิต, ห้องแนะแนว, HR Room หรือโฮมรูมเช้า</li>
          </ul>
        </div>
      </section>
    </main>

    <footer>
      Prototype UI &amp; Logic โดย HTML / CSS / JavaScript — สามารถต่อยอดเป็นเว็บแอพเต็มรูปแบบหรือเชื่อมฐานข้อมูลได้จริง
    </footer>
  </div>

  <script>
    // ----- Helper -----
    function timeToMinutes(timeStr) {
      if (!timeStr) return null;
      const [h, m] = timeStr.split(":").map(Number);
      return h * 60 + m;
    }

    function minutesToTime(minutes) {
      let m = Math.round(minutes);
      if (m < 0) m = (24 * 60 + m) % (24 * 60);
      const h = Math.floor(m / 60) % 24;
      const min = m % 60;
      return String(h).padStart(2, "0") + ":" + String(min).padStart(2, "0");
    }

    function formatThaiDate(d = new Date()) {
      return d.toLocaleDateString("th-TH", {
        year: "numeric",
        month: "short",
        day: "numeric",
      });
    }

    function todayKey() {
      const d = new Date();
      const y = d.getFullYear();
      const m = String(d.getMonth() + 1).padStart(2, "0");
      const day = String(d.getDate()).padStart(2, "0");
      return `${y}-${m}-${day}`;
    }

    // ----- Set today text -----
    document.getElementById("todayDate").textContent = formatThaiDate();

    // ----- Tab switching -----
    const tabBar = document.getElementById("tabBar");
    const views = document.querySelectorAll(".view");
    tabBar.addEventListener("click", (e) => {
      const btn = e.target.closest(".tab-btn");
      if (!btn) return;
      const targetId = btn.dataset.view;
      document
        .querySelectorAll(".tab-btn")
        .forEach((b) => b.classList.remove("active"));
      btn.classList.add("active");
      views.forEach((v) => {
        if (v.id === targetId) v.classList.add("active");
        else v.classList.remove("active");
      });
    });

    // ----- Calculation logic -----
    const calcBtn = document.getElementById("calcBtn");
    const recommendedLeaveEl = document.getElementById("recommendedLeave");
    const etaChip = document.getElementById("etaChip");
    const riskChip = document.getElementById("riskChip");
    const scoreFill = document.getElementById("scoreFill");
    const scoreText = document.getElementById("scoreText");
    const messageBox = document.getElementById("messageBox");
    const missionBox = document.getElementById("missionBox");

    let lastCalcResult = null; // เก็บผลล่าสุดสำหรับใช้ตอนกดบันทึก

    calcBtn.addEventListener("click", () => {
      const arrivalTimeStr = document.getElementById("arrivalTime").value;
      const baseTravel = Number(document.getElementById("baseTravel").value);
      const trafficFactor = Number(
        document.getElementById("trafficLevel").value
      );
      const weatherFactor = Number(document.getElementById("weather").value);
      const buffer = Number(document.getElementById("buffer").value);
      const wakeTimeStr = document.getElementById("wakeTime").value;
      const prepMinutes = Number(
        document.getElementById("prepMinutes").value
      );

      if (!arrivalTimeStr || !wakeTimeStr || !baseTravel || !prepMinutes) {
        messageBox.innerHTML =
          "⚠️ กรุณาใส่ข้อมูลให้ครบก่อนนะคะ (เวลาไปโรงเรียน, เวลาเดินทาง, เวลาตื่น, เวลาเตรียมตัว)";
        return;
      }

      const arrivalTimeMin = timeToMinutes(arrivalTimeStr);
      const wakeTimeMin = timeToMinutes(wakeTimeStr);

      const travelWithFactors =
        baseTravel * (1 + trafficFactor + weatherFactor) + buffer;

      const recommendedLeaveMin = arrivalTimeMin - travelWithFactors;
      const actualLeaveMin = wakeTimeMin + prepMinutes;

      recommendedLeaveEl.textContent = minutesToTime(recommendedLeaveMin);

      // ประเมินเวลาไปถึงถ้าออกตามเวลาที่เตรียมตัวเสร็จ
      const etaIfLeaveNow = actualLeaveMin + travelWithFactors;
      const etaTimeStr = minutesToTime(etaIfLeaveNow);
      const lateMinutes = etaIfLeaveNow - arrivalTimeMin;

      etaChip.style.display = "inline-flex";
      etaChip.textContent = `ถ้าออกหลังเตรียมตัวเสร็จจะถึงประมาณ ${etaTimeStr} น.`;

      riskChip.style.display = "inline-flex";
      if (lateMinutes <= -10) {
        riskChip.className = "chip good";
        riskChip.textContent = "ปลอดภัยสบาย ๆ มาเช้าทันแน่นอน 🎉";
      } else if (lateMinutes <= 0) {
        riskChip.className = "chip";
        riskChip.textContent = "ทันแบบเฉียด ๆ ต้องไม่แวะที่ไหนเพิ่มนะคะ 😅";
      } else if (lateMinutes <= 15) {
        riskChip.className = "chip late";
        riskChip.textContent = `เสี่ยงมาสายประมาณ ${lateMinutes.toFixed(
          0
        )} นาที ⚠️`;
      } else {
        riskChip.className = "chip late";
        riskChip.textContent = "ถ้ายังออกเวลานี้ มีโอกาสมาสายเยอะเลยค่ะ ❗";
      }

      // คะแนนวินัยวันนี้
      let score = 50;
      if (actualLeaveMin <= recommendedLeaveMin + 5) {
        score += 20;
      }
      if (buffer >= 10) {
        score += 10;
      }
      if (trafficFactor >= 0.15 || weatherFactor >= 0.1) {
        score += 10;
      }
      if (lateMinutes <= 0) {
        score += 10;
      }
      if (score > 100) score = 100;
      if (score < 0) score = 0;

      scoreFill.style.width = score + "%";
      scoreText.textContent = score.toFixed(0) + " / 100";

      let msg = "";
      if (lateMinutes <= 0) {
        msg +=
          "✅ แผนของวันนี้ถือว่าดีมาก มีโอกาสมาทันเวลา หรือมาเช้าด้วยค่ะ<br/>";
      } else {
        msg +=
          "⚠️ แผนวันนี้ยังเสี่ยงมาสายนิดหน่อย ลองขยับเวลาออกจากบ้านให้เร็วขึ้นอีกสัก 10–15 นาทีดูนะคะ<br/>";
      }
      msg += `• ใช้เวลาเดินทางโดยประมาณ <strong>${Math.round(
        travelWithFactors
      )}</strong> นาที รวมเผื่อรถติด/ฝนแล้ว<br/>`;
      msg += `• ถ้าตื่นเวลา <strong>${wakeTimeStr}</strong> และใช้เวลาเตรียมตัว <strong>${prepMinutes} นาที</strong> ควรออกจากบ้านไม่เกิน <strong>${minutesToTime(
        recommendedLeaveMin
      )}</strong>`;
      messageBox.innerHTML = msg;

      let mission = "";
      if (score >= 85) {
        mission =
          "โหมดโปร: ลองมาถึงโรงเรียนให้ได้ก่อนเวลาเข้าแถว 15 นาที เพื่อเก็บ Badge 🌅 Early Bird!";
      } else if (score >= 60) {
        mission =
          "ภารกิจ: พรุ่งนี้ลองขยับเวลาออกจากบ้านให้เร็วขึ้น 10 นาที ถ้าทำได้ 3 วันติด จะได้ Badge 🚀 Improvement Hero!";
      } else {
        mission =
          "ภารกิจเริ่มต้น: คืนนี้เตรียมกระเป๋าและชุดนักเรียนให้เรียบร้อยก่อนนอน แล้วตั้งปลุกเร็วขึ้น 15 นาที ลองดู 1 วันก่อนนะคะ 💪";
      }
      missionBox.innerHTML = "🎮 <strong>ภารกิจวันนี้:</strong> " + mission;

      // เก็บผลล่าสุดไว้ใช้ตอนบันทึก
      lastCalcResult = {
        dateKey: todayKey(),
        dateLabel: formatThaiDate(),
        arrivalTime: arrivalTimeStr,
        recommendedLeave: minutesToTime(recommendedLeaveMin),
        etaIfLeaveNow: etaTimeStr,
        lateMinutes: lateMinutes,
        score: Math.round(score),
      };
    });

    // ----- บันทึกข้อมูลวันนี้ -----
    const saveBtn = document.getElementById("saveDayBtn");

    function loadRecords() {
      try {
        const raw = localStorage.getItem("brmn_records");
        if (!raw) return [];
        const arr = JSON.parse(raw);
        return Array.isArray(arr) ? arr : [];
      } catch (e) {
        return [];
      }
    }

    function saveRecords(records) {
      localStorage.setItem("brmn_records", JSON.stringify(records));
    }

    function updateStatsView() {
      const listEl = document.getElementById("historyList");
      const statDaysEl = document.getElementById("statDays");
      const statAvgScoreEl = document.getElementById("statAvgScore");
      const statOnTimeRateEl = document.getElementById("statOnTimeRate");

      const records = loadRecords();
      const count = records.length;
      statDaysEl.textContent = count;

      if (count === 0) {
        listEl.innerHTML =
          '<div class="history-item"><div>ยังไม่มีข้อมูล กรุณาลองคำนวณและกด "บันทึกข้อมูลวันนี้" ก่อนค่ะ</div></div>';
        statAvgScoreEl.textContent = "0";
        statOnTimeRateEl.textContent = "0%";
        return;
      }

      // จำกัดแสดงล่าสุด 30 รายการ
      const showRecords = records.slice(-30).reverse();

      let html = "";
      let sumScore = 0;
      let onTimeCount = 0;
      showRecords.forEach((rec) => {
        sumScore += rec.score || 0;
        if (rec.lateMinutes <= 0) onTimeCount++;
        html += `
          <div class="history-item">
            <div>
              <div class="history-date">${rec.dateLabel}</div>
              <div style="font-size:11px;">
                แนะนำให้ออก: <strong>${rec.recommendedLeave}</strong>
                | คาดว่าจะถึง: ${rec.etaIfLeaveNow}
              </div>
            </div>
            <div class="history-meta">
              <span>คะแนน: <strong>${rec.score}</strong></span>
              <span>${
                rec.lateMinutes <= 0
                  ? '<span class="tag-on-time">ไม่สาย</span>'
                  : '<span class="tag-late">สาย ~' +
                    Math.round(rec.lateMinutes) +
                    " นาที</span>"
              }</span>
            </div>
          </div>
        `;
      });
      listEl.innerHTML = html;

      const avgScore = sumScore / records.length;
      const onTimeRate = (onTimeCount / records.length) * 100;
      statAvgScoreEl.textContent = avgScore.toFixed(0);
      statOnTimeRateEl.textContent = onTimeRate.toFixed(0) + "%";
    }

    saveBtn.addEventListener("click", () => {
      if (!lastCalcResult) {
        alert("กรุณากดคำนวณก่อน แล้วค่อยบันทึกข้อมูลวันนี้ค่ะ");
        return;
      }

      const records = loadRecords();
      const existingIndex = records.findIndex(
        (r) => r.dateKey === lastCalcResult.dateKey
      );
      if (existingIndex >= 0) {
        records[existingIndex] = lastCalcResult;
      } else {
        records.push(lastCalcResult);
      }
      // จำกัดไม่เกิน 90 วันล่าสุด
      if (records.length > 90) {
        records.splice(0, records.length - 90);
      }
      saveRecords(records);
      updateStatsView();
      alert("บันทึกข้อมูลของวันนี้เรียบร้อยแล้ว 🎉");
    });

    // ----- Badges -----
    const refreshBadgesBtn = document.getElementById("refreshBadgesBtn");
    const badgeList = document.getElementById("badgeList");

    function updateBadges() {
      const records = loadRecords();
      const badges = {
        early: false,
        perfectWeek: false,
        improve: false,
      };
      if (records.length === 0) {
        // ไม่มีข้อมูล
      } else {
        // เงื่อนไข Early Bird: ไม่มาสาย อย่างน้อย 3 วัน
        const onTimeDays = records.filter((r) => r.lateMinutes <= 0).length;
        if (onTimeDays >= 3) badges.early = true;

        // เงื่อนไข Zero Late Week: ล่าสุด 5 วัน ไม่มีสายเลย
        if (records.length >= 5) {
          const last5 = records.slice(-5);
          if (last5.every((r) => r.lateMinutes <= 0)) badges.perfectWeek = true;
        }

        // เงื่อนไข Improvement Hero:
        // เฉลี่ยครึ่งหลัง มากกว่าครึ่งแรก >= 15 คะแนน
        if (records.length >= 6) {
          const mid = Math.floor(records.length / 2);
          const first = records.slice(0, mid);
          const second = records.slice(mid);
          const avgFirst =
            first.reduce((sum, r) => sum + (r.score || 0), 0) / first.length;
          const avgSecond =
            second.reduce((sum, r) => sum + (r.score || 0), 0) / second.length;
          if (avgSecond - avgFirst >= 15) badges.improve = true;
        }
      }

      badgeList
        .querySelectorAll(".badge")
        .forEach((el) => el.classList.add("locked"));

      if (badges.early) {
        badgeList.querySelector('[data-badge="early"]').classList.remove(
          "locked"
        );
      }
      if (badges.perfectWeek) {
        badgeList
          .querySelector('[data-badge="perfectWeek"]')
          .classList.remove("locked");
      }
      if (badges.improve) {
        badgeList
          .querySelector('[data-badge="improve"]')
          .classList.remove("locked");
      }
    }

    refreshBadgesBtn.addEventListener("click", () => {
      updateStatsView();
      updateBadges();
      alert("อัปเดตสถานะแบดจ์เรียบร้อยแล้ว ✨");
    });

    // โหลดสถิติ + แบดจ์ครั้งแรก
    updateStatsView();
    updateBadges();
  </script>
</body>
</html>
