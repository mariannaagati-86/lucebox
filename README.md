[Uploading index.html.html…]()
<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8" />
  <title>LuceBox Chiara 8 – Musica & Galaxy</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta name="theme-color" content="#050816" />
  <link rel="manifest" href="manifest.webmanifest" />


  <style>
    :root {
      /* Tema chiaro (default) */
      --bg: #eef2ff;
      --bg2: #fdf2ff;
      --bg-card: #ffffff;
      --accent1: #6366f1;
      --accent2: #ec4899;
      --accent3: #f97316;
      --text: #111827;
      --text-soft: #6b7280;
      --border-soft: rgba(209,213,219,0.9);
      --shadow: 0 12px 30px rgba(148, 163, 184, 0.4);
    }

    body.dark {
      /* Tema DARK GALAXY */
      --bg: #050816;
      --bg2: #0b1020;
      --bg-card: #111827;
      --accent1: #4f46e5;
      --accent2: #db2777;
      --accent3: #f97316;
      --text: #e5e7eb;
      --text-soft: #9ca3af;
      --border-soft: rgba(55,65,81,0.9);
      --shadow: 0 16px 40px rgba(15,23,42,0.9);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    body {
      min-height: 100vh;
      display: flex;
      justify-content: center;
      padding: 12px;
      background:
        radial-gradient(circle at top left, rgba(236,72,153,0.18) 0, transparent 55%),
        radial-gradient(circle at bottom right, rgba(56,189,248,0.18) 0, transparent 60%),
        linear-gradient(145deg, var(--bg), var(--bg2));
      color: var(--text);
      transition: background 0.25s ease, color 0.25s ease;
    }

    .app {
      width: 100%;
      max-width: 480px;
      background: rgba(255,255,255,0.9);
      border-radius: 26px;
      box-shadow: var(--shadow);
      border: 1px solid var(--border-soft);
      display: flex;
      flex-direction: column;
      overflow: hidden;
      backdrop-filter: blur(14px);
      position: relative;
      transition: background 0.25s ease, border-color 0.25s ease;
    }

    body.dark .app {
      background: rgba(15,23,42,0.9);
    }

    .app-header {
      padding: 14px 16px;
      border-bottom: 1px solid var(--border-soft);
      display: flex;
      justify-content:space-between;
      align-items:center;
      background: linear-gradient(135deg, rgba(129,140,248,0.18), rgba(236,72,153,0.15));
    }

    .app-title-block {
      display:flex;
      flex-direction:column;
      gap:4px;
    }

    .app-title {
      font-size: 1.3rem;
      font-weight: 900;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      background: linear-gradient(120deg, var(--accent1), var(--accent2));
      -webkit-background-clip: text;
      color: transparent;
    }

    .app-subtitle {
      font-size:0.8rem;
      color:var(--text-soft);
    }

    .theme-toggle {
      padding: 6px 10px;
      border-radius: 999px;
      border: 1px solid var(--border-soft);
      background: rgba(255,255,255,0.8);
      font-size: 0.75rem;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 6px;
      transition: background 0.2s, transform 0.1s;
    }

    body.dark .theme-toggle {
      background: rgba(15,23,42,0.9);
      color: var(--text-soft);
    }

    .theme-toggle:active {
      transform: scale(0.97);
    }

    .main {
      padding: 14px;
      flex: 1;
      overflow-y: auto;
    }

    .section {
      display: none;
    }

    .section.active {
      display: block;
      animation: fadeIn 0.18s ease-out;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(6px);}
      to { opacity: 1; transform: translateY(0);}
    }

    .card {
      background: var(--bg-card);
      border-radius: 18px;
      padding: 14px;
      margin-bottom: 12px;
      border: 1px solid var(--border-soft);
      box-shadow: 0 6px 18px rgba(15,23,42,0.25);
      transition: background 0.25s, border-color 0.25s;
    }

    .card-title {
      font-size: 0.95rem;
      font-weight: 600;
      margin-bottom: 4px;
    }

    .card-subtitle {
      font-size: 0.8rem;
      color: var(--text-soft);
      margin-bottom: 6px;
    }

    .item-meta {
      font-size: 0.8rem;
      color: var(--text-soft);
    }

    label.hint {
      font-size: 0.78rem;
      color: var(--text-soft);
      margin-top: 8px;
      display: block;
    }

    input, textarea, select {
      width: 100%;
      padding: 8px;
      margin-top: 4px;
      border-radius: 12px;
      border: 1px solid var(--border-soft);
      background: rgba(249,250,251,0.9);
      font-size: 0.83rem;
      color: var(--text);
      outline: none;
      transition: border-color 0.15s, background 0.15s;
    }

    body.dark input,
    body.dark textarea,
    body.dark select {
      background: #020617;
      color: var(--text);
    }

    input:focus, textarea:focus, select:focus {
      border-color: var(--accent1);
      box-shadow: 0 0 0 1px rgba(129,140,248,0.7);
      background: #ffffff;
    }

    body.dark input:focus,
    body.dark textarea:focus,
    body.dark select:focus {
      background: #020617;
    }

    textarea { resize: vertical; }

    .btn-main {
      width: 100%;
      margin-top: 10px;
      padding: 10px;
      border-radius: 999px;
      border: none;
      background: linear-gradient(135deg, var(--accent1), var(--accent2));
      color: #f9fafb;
      font-weight: 700;
      font-size: 0.9rem;
      cursor: pointer;
      box-shadow: 0 10px 22px rgba(236,72,153,0.4);
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
    }

    .btn-main:active {
      transform: translateY(1px) scale(0.99);
      box-shadow: 0 6px 16px rgba(236,72,153,0.4);
    }

    .btn-secondary {
      border: 1px solid var(--border-soft);
      background: rgba(249,250,251,0.9);
      padding: 6px 10px;
      border-radius: 999px;
      cursor: pointer;
      font-size: 0.75rem;
      color: var(--text-soft);
    }

    body.dark .btn-secondary {
      background: #020617;
    }

    .idea-list, .file-list, .photo-list, .diary-list, .songs-list {
      margin-top: 10px;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    .item {
      padding: 8px 10px;
      border-radius: 14px;
      background: rgba(249,250,251,0.9);
      border: 1px solid var(--border-soft);
      display: flex;
      flex-direction: column;
      gap: 4px;
      font-size: 0.8rem;
    }

    body.dark .item {
      background: #020617;
    }

    .item-title {
      font-weight: 500;
      color: var(--text);
    }

    .item-tag {
      padding: 2px 7px;
      border-radius: 999px;
      background: #eef2ff;
      border: 1px solid #c7d2fe;
      font-size: 0.7rem;
      color: #4338ca;
    }

    body.dark .item-tag {
      background: rgba(30,64,175,0.6);
      border-color: rgba(129,140,248,0.9);
      color: #e5e7eb;
    }

    .hashtag-list {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-top: 6px;
    }

    .tag-pill {
      padding: 4px 10px;
      border-radius: 999px;
      background: rgba(229,231,235,0.9);
      color: #374151;
      font-size: 0.75rem;
      border: 1px solid #d1d5db;
      cursor: pointer;
      transition: 0.15s;
    }

    body.dark .tag-pill {
      background: #020617;
      color: #e5e7eb;
      border-color: #1f2937;
    }

    .tag-pill.active {
      background: linear-gradient(135deg, var(--accent1), var(--accent2), var(--accent3));
      color: white;
      border-color: transparent;
      font-weight: 600;
      box-shadow: 0 4px 12px rgba(236,72,153,0.5);
    }

    /* DIARIO – mood buttons */
    .mood-list {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-top: 6px;
    }

    .mood-pill {
      padding: 4px 8px;
      border-radius: 999px;
      border: 1px solid var(--border-soft);
      background: rgba(249,250,251,0.9);
      font-size: 0.9rem;
      cursor: pointer;
      transition: 0.15s;
    }

    body.dark .mood-pill {
      background: #020617;
    }

    .mood-pill.active {
      background: linear-gradient(135deg, #22c55e, #eab308, #ef4444);
      color: #111827;
      border-color: transparent;
      font-weight: 700;
      box-shadow: 0 4px 12px rgba(34,197,94,0.45);
    }

    .photo-preview {
      margin-top: 10px;
      width: 100%;
      border-radius: 12px;
      border: 1px solid var(--border-soft);
      object-fit: cover;
      max-height: 200px;
      display: none;
    }

    .photo-item {
      display: flex;
      gap: 10px;
      align-items: center;
      padding: 8px;
      background: rgba(249,250,251,0.9);
      border-radius: 12px;
      border: 1px solid var(--border-soft);
    }

    body.dark .photo-item {
      background: #020617;
    }

    .photo-thumb {
      width: 60px;
      height: 60px;
      object-fit: cover;
      border-radius: 8px;
      border: 1px solid var(--border-soft);
      flex-shrink: 0;
    }

    .file-item {
      padding: 10px;
      border-radius: 12px;
      background: rgba(249,250,251,0.9);
      border: 1px solid var(--border-soft);
      margin-bottom: 6px;
    }

    body.dark .file-item {
      background: #020617;
    }

    .bottom-nav {
      border-top: 1px solid var(--border-soft);
      background: #e0e7ff;
      padding: 6px;
    }

    body.dark .bottom-nav {
      background: #020617;
    }

    .nav-bar {
      display: grid;
      grid-template-columns: repeat(6, 1fr);
      gap: 6px;
    }

    .nav-btn {
      padding: 5px;
      background: transparent;
      border: none;
      text-align: center;
      font-size: 0.75rem;
      color: var(--text-soft);
      border-radius: 12px;
      cursor: pointer;
    }

    .nav-btn span {
      font-size: 1.1rem;
      display: block;
    }

    .nav-btn.active {
      background: #f97316;
      color: #111827;
      box-shadow: 0 4px 10px rgba(249,115,22,0.5);
    }

    body.dark .nav-btn.active {
      background: linear-gradient(135deg, var(--accent1), var(--accent2));
      color: #f9fafb;
    }

    .empty-text {
      font-size: 0.8rem;
      color: var(--text-soft);
    }
  </style>
</head>
<body>
  <div class="app">
    <header class="app-header">
      <div class="app-title-block">
        <div class="app-title">LuceBox 8</div>
        <div class="app-subtitle">Idee • Diario • Musica • Foto • File • Galaxy 🌌</div>
      </div>
      <button id="theme-toggle" class="theme-toggle">
        🌤️ Tema chiaro
      </button>
    </header>

    <main class="main">

      <!-- HOME -->
      <section id="section-home" class="section active">
        <div class="card">
          <div class="card-title">🌞 Benvenuta, Marianna</div>
          <div class="card-subtitle">
            Tutto il tuo mondo creativo e mentale, in un'unica app.
          </div>
        </div>

        <div class="card">
          <div class="card-title">📊 Riassunto veloce</div>
          <div class="idea-list">
            <div class="item">
              <div class="item-title">Idee salvate</div>
              <div class="item-meta" id="ideas-count">0 idee</div>
            </div>
            <div class="item">
              <div class="item-title">Giorni di diario</div>
              <div class="item-meta" id="diary-count">0 giorni</div>
            </div>
            <div class="item">
              <div class="item-title">Brani / testi</div>
              <div class="item-meta" id="songs-count">0 brani</div>
            </div>
            <div class="item">
              <div class="item-title">Foto salvate</div>
              <div class="item-meta" id="photos-count">0 foto</div>
            </div>
            <div class="item">
              <div class="item-title">File salvati</div>
              <div class="item-meta" id="files-count">0 file</div>
            </div>
          </div>
        </div>
      </section>

      <!-- IDEE -->
      <section id="section-ideas" class="section">
        <div class="card">
          <div class="card-title">💭 Idee & pensieri</div>
          <div class="card-subtitle">
            Categorie + hashtag cliccabili con effetto galaxy 🌈
          </div>

          <label class="hint">Categoria</label>
          <select id="idea-category">
            <option>Musica</option>
            <option>Testi</option>
            <option>Idee</option>
            <option>Casa</option>
            <option>Cucina</option>
            <option>Studiare</option>
            <option>Vacanze</option>
            <option>Appuntamenti</option>
            <option>Medicina</option>
            <option>Libri</option>
            <option>Prompt</option>
            <option>Altro</option>
            <option>Film</option>
          </select>

          <label class="hint">Titolo</label>
          <input type="text" id="idea-title" placeholder="Titolo idea..." />

          <label class="hint">Contenuto</label>
          <textarea id="idea-text" rows="4" placeholder="Scrivi la tua idea..."></textarea>

          <label class="hint">Hashtag veloci</label>
          <div class="hashtag-list">
            <div class="tag-pill">#strofa</div>
            <div class="tag-pill">#ritornello</div>
            <div class="tag-pill">#sunoprompt</div>
            <div class="tag-pill">#video</div>
            <div class="tag-pill">#pixverse</div>
            <div class="tag-pill">#ispirazione</div>
            <div class="tag-pill">#studio</div>
            <div class="tag-pill">#mappaconcettuale</div>
            <div class="tag-pill">#ricetta</div>
            <div class="tag-pill">#pensieri</div>
            <div class="tag-pill">#psichedelico</div>
            <div class="tag-pill">#medicina</div>
            <div class="tag-pill">#importante</div>
            <div class="tag-pill">#viaggio</div>
            <div class="tag-pill">#idee</div>
          </div>

          <label class="hint">Hashtag manuali (se vuoi)</label>
          <input type="text" id="manual-tags" placeholder="#ReggioCity #Sicilia ..." />

          <button class="btn-main" onclick="addIdea()">➕ Salva idea</button>
        </div>

        <div class="card">
          <div style="display:flex;justify-content:space-between;align-items:center;">
            <div class="card-title">📜 Idee salvate</div>
            <div style="display:flex;gap:6px;">
              <button class="btn-secondary" onclick="exportIdeas()">Esporta txt</button>
              <button class="btn-secondary" onclick="clearIdeas()">Svuota</button>
            </div>
          </div>
          <div id="ideas-list" class="idea-list">
            <div class="empty-text">Nessuna idea salvata.</div>
          </div>
        </div>
      </section>

      <!-- DIARIO -->
      <section id="section-diary" class="section">
        <div class="card">
          <div class="card-title">📅 Diario & Emozioni</div>
          <div class="card-subtitle">
            Scrivi come stai, giorno per giorno.
          </div>

          <label class="hint">Data</label>
          <input type="date" id="diary-date" />

          <label class="hint">Umore</label>
          <div class="mood-list">
            <button class="mood-pill">😁</button>
            <button class="mood-pill">🙂</button>
            <button class="mood-pill">😐</button>
            <button class="mood-pill">😔</button>
            <button class="mood-pill">😡</button>
            <button class="mood-pill">🥺</button>
            <button class="mood-pill">😵‍💫</button>
            <button class="mood-pill">😴</button>
          </div>

          <label class="hint">Pensiero del giorno</label>
          <textarea id="diary-text" rows="5" placeholder="Scrivi come ti senti oggi..."></textarea>

          <button class="btn-main" onclick="saveDiaryEntry()">💾 Salva giorno</button>
        </div>

        <div class="card">
          <div style="display:flex;justify-content:space-between;align-items:center;">
            <div class="card-title">📖 Diario salvato</div>
            <button class="btn-secondary" onclick="clearDiary()">Svuota diario</button>
          </div>
          <div id="diary-list" class="diary-list">
            <div class="empty-text">Ancora nessun giorno scritto.</div>
          </div>
        </div>
      </section>

      <!-- MUSICA & TESTI -->
      <section id="section-music" class="section">
        <div class="card">
          <div class="card-title">🎤 Musica & Testi</div>
          <div class="card-subtitle">
            Qui salvi le parti dei brani, il mood, il BPM e i prompt per Suno e i video.
          </div>

          <label class="hint">Titolo brano</label>
          <input id="music-title" type="text" placeholder="Es. Erba buona & gente cattiva..." />

          <label class="hint">Parte</label>
          <select id="music-part">
            <option>Strofa</option>
            <option>Ritornello</option>
            <option>Bridge</option>
            <option>Intro</option>
            <option>Outro</option>
          </select>

          <label class="hint">Mood</label>
          <input id="music-mood" type="text" placeholder="Es. ironica, incazzata, nostalgica, psichedelica..." />

          <label class="hint">BPM (opzionale)</label>
          <input id="music-bpm" type="number" min="60" max="200" placeholder="Es. 90, 120, 140..." />

          <label class="hint">Testo della parte</label>
          <textarea id="music-lyrics" rows="5" placeholder="Incolla o scrivi qui la strofa / il ritornello..."></textarea>

          <label class="hint">Prompt per Suno</label>
          <textarea id="music-suno" rows="3" placeholder="Prompt per generare la musica su Suno..."></textarea>

          <label class="hint">Idee video (PixVerse, Sora, ecc.)</label>
          <textarea id="music-video" rows="3" placeholder="Descrivi le scene del video, le atmosfere, i dettagli..."></textarea>

          <button class="btn-main" onclick="addSong()">💾 Salva brano / parte</button>
        </div>

        <div class="card">
          <div style="display:flex;justify-content:space-between;align-items:center;">
            <div class="card-title">🎧 Brani & parti salvate</div>
            <div style="display:flex;gap:6px;">
              <button class="btn-secondary" onclick="exportSongs()">Esporta txt</button>
              <button class="btn-secondary" onclick="clearSongs()">Svuota</button>
            </div>
          </div>
          <div id="songs-list" class="songs-list">
            <div class="empty-text">Ancora nessun brano o parte salvata.</div>
          </div>
        </div>
      </section>

      <!-- FOTO -->
      <section id="section-photos" class="section">
        <div class="card">
          <div class="card-title">📸 Aggiungi foto</div>
          <div class="card-subtitle">Anteprima + salvataggio nel browser (privato).</div>

          <label class="hint">Titolo foto</label>
          <input id="photo-title" type="text" placeholder="Es. Foto PixVerse, ricordo, appunto..." />

          <label class="hint">Note</label>
          <textarea id="photo-note" rows="3" placeholder="Scrivi una descrizione..."></textarea>

          <label class="hint">Carica immagine</label>
          <input id="photo-file" type="file" accept="image/*" />

          <img id="photo-preview" class="photo-preview" />

          <button class="btn-main" onclick="savePhoto()">💾 Salva foto</button>
        </div>

        <div class="card">
          <div style="display:flex;justify-content:space-between;align-items:center;">
            <div class="card-title">📚 Foto salvate</div>
            <button class="btn-secondary" onclick="clearPhotos()">Svuota tutte</button>
          </div>
          <div id="photos-list" class="photo-list">
            <div class="empty-text">Nessuna foto salvata.</div>
          </div>
        </div>
      </section>

      <!-- FILE -->
      <section id="section-files" class="section">
        <div class="card">
          <div class="card-title">📎 Aggiungi file</div>
          <div class="card-subtitle">PDF, documenti, appunti importanti.</div>

          <label class="hint">Titolo file</label>
          <input id="file-title" type="text" placeholder="Es. PDF sociologia, canzone, documento..." />

          <label class="hint">Note</label>
          <textarea id="file-note" rows="3" placeholder="Scrivi una nota..."></textarea>

          <label class="hint">Carica file</label>
          <input id="file-upload" type="file" />

          <button class="btn-main" onclick="saveFile()">💾 Salva file</button>
        </div>

        <div class="card">
          <div style="display:flex;justify-content:space-between;align-items:center;">
            <div class="card-title">📂 File salvati</div>
            <button class="btn-secondary" onclick="clearFiles()">Svuota tutti</button>
          </div>
          <div id="files-list" class="file-list">
            <div class="empty-text">Nessun file salvato.</div>
          </div>
        </div>
      </section>

    </main>

    <footer class="bottom-nav">
      <div class="nav-bar">
        <button class="nav-btn active" onclick="switchSection('home', this)">
          <span>🏠</span>Home
        </button>
        <button class="nav-btn" onclick="switchSection('ideas', this)">
          <span>💭</span>Idee
        </button>
        <button class="nav-btn" onclick="switchSection('diary', this)">
          <span>📅</span>Diario
        </button>
        <button class="nav-btn" onclick="switchSection('music', this)">
          <span>🎤</span>Musica
        </button>
        <button class="nav-btn" onclick="switchSection('photos', this)">
          <span>📸</span>Foto
        </button>
        <button class="nav-btn" onclick="switchSection('files', this)">
          <span>📎</span>File
        </button>
      </div>
    </footer>
  </div>

  <script>
    /* ------------ NAVIGAZIONE ------------ */
    function switchSection(section, btn) {
      document.querySelectorAll(".section").forEach(s => s.classList.remove("active"));
      document.getElementById("section-" + section).classList.add("active");

      document.querySelectorAll(".nav-btn").forEach(b => b.classList.remove("active"));
      btn.classList.add("active");
    }

    /* ------------ TEMA CHIARO / DARK ------------ */
    const THEME_KEY = "lucebox_theme";
    const body = document.body;
    const themeBtn = document.getElementById("theme-toggle");

    function applyTheme(theme) {
      if (theme === "dark") {
        body.classList.add("dark");
        themeBtn.textContent = "🌙 Tema galaxy";
      } else {
        body.classList.remove("dark");
        themeBtn.textContent = "🌤️ Tema chiaro";
      }
    }

    function loadTheme() {
      const saved = localStorage.getItem(THEME_KEY) || "light";
      applyTheme(saved);
    }

    themeBtn.addEventListener("click", () => {
      const isDark = body.classList.contains("dark");
      const newTheme = isDark ? "light" : "dark";
      localStorage.setItem(THEME_KEY, newTheme);
      applyTheme(newTheme);
    });

    /* ------------ IDEE ------------ */
    let ideas = [];
    const IDEAS_KEY = "lucebox_v6_ideas"; // manteniamo la chiave per non perdere dati
    let activeTags = [];

    function setupHashtags() {
      document.querySelectorAll(".tag-pill").forEach(pill => {
        pill.addEventListener("click", () => {
          const tag = pill.textContent.trim();
          if (pill.classList.contains("active")) {
            pill.classList.remove("active");
            activeTags = activeTags.filter(t => t !== tag);
          } else {
            pill.classList.add("active");
            activeTags.push(tag);
          }
        });
      });
    }

    function loadIdeas() {
      const raw = localStorage.getItem(IDEAS_KEY);
      ideas = raw ? JSON.parse(raw) : [];
      renderIdeas();
    }

    function saveIdeas() {
      localStorage.setItem(IDEAS_KEY, JSON.stringify(ideas));
      updateSummaryCounts();
    }

    function addIdea() {
      const title = document.getElementById("idea-title").value.trim();
      const text = document.getElementById("idea-text").value.trim();
      const manual = document.getElementById("manual-tags").value.trim();
      const category = document.getElementById("idea-category").value;

      if (!title && !text) return;

      const now = new Date();
      const dateStr = now.toLocaleString("it-IT", {
        day: "2-digit",
        month: "2-digit",
        hour: "2-digit",
        minute: "2-digit"
      });

      const tagsFinal = [...activeTags];
      if (manual) {
        manual.split(" ").forEach(t => {
          if (t.trim()) tagsFinal.push(t.trim());
        });
      }

      ideas.push({
        title,
        text,
        category,
        tags: tagsFinal,
        date: dateStr
      });

      saveIdeas();
      renderIdeas();

      document.getElementById("idea-title").value = "";
      document.getElementById("idea-text").value = "";
      document.getElementById("manual-tags").value = "";
      document.querySelectorAll(".tag-pill").forEach(p => p.classList.remove("active"));
      activeTags = [];
    }

    function renderIdeas() {
      const list = document.getElementById("ideas-list");
      if (!ideas.length) {
        list.innerHTML = '<div class="empty-text">Nessuna idea salvata.</div>';
        updateSummaryCounts();
        return;
      }
      list.innerHTML = "";
      ideas.slice().reverse().forEach(idea => {
        const div = document.createElement("div");
        div.className = "item";
        div.innerHTML = `
          <div class="item-title">${idea.title || "(senza titolo)"}</div>
          <div>${idea.text}</div>
          <div class="item-meta">
            <span>${idea.category}</span>
            <span>${idea.date}</span>
          </div>
          <div style="margin-top:5px;display:flex;flex-wrap:wrap;gap:4px;">
            ${idea.tags.map(t => `<span class="item-tag">${t}</span>`).join("")}
          </div>
        `;
        list.appendChild(div);
      });
      updateSummaryCounts();
    }

    function clearIdeas() {
      if (!confirm("Vuoi davvero cancellare tutte le idee?")) return;
      ideas = [];
      saveIdeas();
      renderIdeas();
    }

    function exportIdeas() {
      if (!ideas.length) {
        alert("Non ci sono idee da esportare.");
        return;
      }
      let content = "LUCEBOX IDEE – Versione 8\n\n";
      ideas.forEach((idea, i) => {
        content += `#${i+1}\n`;
        content += `Titolo: ${idea.title}\n`;
        content += `Categoria: ${idea.category}\n`;
        content += `Data: ${idea.date}\n`;
        content += `Tag: ${idea.tags.join(", ")}\n`;
        content += `Testo:\n${idea.text}\n`;
        content += "-------------------------\n\n";
      });
      const blob = new Blob([content], {type: "text/plain;charset=utf-8"});
      const url = URL.createObjectURL(blob);
      const a = document.createElement("a");
      a.href = url;
      a.download = "lucebox_idee_v8.txt";
      a.click();
      URL.revokeObjectURL(url);
    }

    /* ------------ DIARIO ------------ */
    let diaryEntries = [];
    const DIARY_KEY = "lucebox_v7_diary";
    let selectedMood = "";

    function setupMoodButtons() {
      document.querySelectorAll(".mood-pill").forEach(btn => {
        btn.addEventListener("click", () => {
          document.querySelectorAll(".mood-pill").forEach(b => b.classList.remove("active"));
          btn.classList.add("active");
          selectedMood = btn.textContent.trim();
        });
      });
    }

    function setTodayInDiary() {
      const input = document.getElementById("diary-date");
      const today = new Date();
      const yyyy = today.getFullYear();
      const mm = String(today.getMonth() + 1).padStart(2, "0");
      const dd = String(today.getDate()).padStart(2, "0");
      input.value = `${yyyy}-${mm}-${dd}`;
    }

    function loadDiary() {
      const raw = localStorage.getItem(DIARY_KEY);
      diaryEntries = raw ? JSON.parse(raw) : [];
      renderDiary();
    }

    function saveDiaryEntry() {
      const dateInput = document.getElementById("diary-date").value;
      const text = document.getElementById("diary-text").value.trim();

      if (!dateInput && !text && !selectedMood) return;
      if (!dateInput) {
        alert("Scegli una data per questo giorno di diario.");
        return;
      }

      const existingIndex = diaryEntries.findIndex(e => e.date === dateInput);
      const now = new Date();
      const savedAt = now.toLocaleString("it-IT");

      const entry = {
        date: dateInput,
        mood: selectedMood || "",
        text,
        savedAt
      };

      if (existingIndex >= 0) {
        diaryEntries[existingIndex] = entry;
      } else {
        diaryEntries.push(entry);
      }

      localStorage.setItem(DIARY_KEY, JSON.stringify(diaryEntries));
      renderDiary();
      updateSummaryCounts();

      document.getElementById("diary-text").value = "";
    }

    function renderDiary() {
      const list = document.getElementById("diary-list");
      const count = document.getElementById("diary-count");

      if (!diaryEntries.length) {
        list.innerHTML = '<div class="empty-text">Ancora nessun giorno scritto.</div>';
        if (count) count.textContent = "0 giorni";
        return;
      }

      list.innerHTML = "";
      const sorted = diaryEntries.slice().sort((a,b) => (a.date < b.date ? 1 : -1));

      sorted.forEach(entry => {
        const div = document.createElement("div");
        div.className = "item";
        const niceDate = formatItalianDate(entry.date);
        div.innerHTML = `
          <div class="item-title">
            ${entry.mood ? entry.mood + " " : ""}${niceDate}
          </div>
          <div>${entry.text || "(nessun testo)"}</div>
          <div class="item-meta">Salvato: ${entry.savedAt || ""}</div>
        `;
        list.appendChild(div);
      });

      if (count) {
        count.textContent = diaryEntries.length + (diaryEntries.length === 1 ? " giorno" : " giorni");
      }
    }

    function clearDiary() {
      if (!confirm("Vuoi davvero cancellare tutto il diario?")) return;
      diaryEntries = [];
      localStorage.setItem(DIARY_KEY, JSON.stringify([]));
      renderDiary();
      updateSummaryCounts();
    }

    function formatItalianDate(iso) {
      if (!iso) return "";
      const [y,m,d] = iso.split("-");
      return `${d}/${m}/${y}`;
    }

    /* ------------ MUSICA & TESTI ------------ */
    let songs = [];
    const SONGS_KEY = "lucebox_v8_songs";

    function loadSongs() {
      const raw = localStorage.getItem(SONGS_KEY);
      songs = raw ? JSON.parse(raw) : [];
      renderSongs();
    }

    function addSong() {
      const title = document.getElementById("music-title").value.trim();
      const part = document.getElementById("music-part").value;
      const mood = document.getElementById("music-mood").value.trim();
      const bpm = document.getElementById("music-bpm").value.trim();
      const lyrics = document.getElementById("music-lyrics").value.trim();
      const suno = document.getElementById("music-suno").value.trim();
      const video = document.getElementById("music-video").value.trim();

      if (!title && !lyrics && !suno && !video) return;

      const now = new Date();
      const dateStr = now.toLocaleString("it-IT", {
        day: "2-digit",
        month: "2-digit",
        hour: "2-digit",
        minute: "2-digit"
      });

      songs.push({
        title,
        part,
        mood,
        bpm,
        lyrics,
        suno,
        video,
        date: dateStr
      });

      localStorage.setItem(SONGS_KEY, JSON.stringify(songs));
      renderSongs();
      updateSummaryCounts();

      document.getElementById("music-title").value = "";
      document.getElementById("music-mood").value = "";
      document.getElementById("music-bpm").value = "";
      document.getElementById("music-lyrics").value = "";
      document.getElementById("music-suno").value = "";
      document.getElementById("music-video").value = "";
    }

    function renderSongs() {
      const list = document.getElementById("songs-list");
      const count = document.getElementById("songs-count");

      if (!songs.length) {
        list.innerHTML = '<div class="empty-text">Ancora nessun brano o parte salvata.</div>';
        if (count) count.textContent = "0 brani";
        return;
      }

      list.innerHTML = "";
      songs.slice().reverse().forEach(song => {
        const div = document.createElement("div");
        div.className = "item";
        div.innerHTML = `
          <div class="item-title">${song.title || "(senza titolo)"} – <span style="font-size:0.8rem;">${song.part}</span></div>
          <div style="font-size:0.78rem;color:var(--text-soft);">
            ${song.mood ? "Mood: " + song.mood + " • " : ""}${song.bpm ? "BPM: " + song.bpm : ""}
          </div>
          <div style="margin-top:4px;"><b>Testo:</b><br>${(song.lyrics || "").replace(/\n/g,"<br>")}</div>
          ${song.suno ? `<div style="margin-top:4px;"><b>Prompt Suno:</b><br>${song.suno.replace(/\n/g,"<br>")}</div>` : ""}
          ${song.video ? `<div style="margin-top:4px;"><b>Idee video:</b><br>${song.video.replace(/\n/g,"<br>")}</div>` : ""}
          <div class="item-meta" style="margin-top:4px;">Salvato: ${song.date}</div>
        `;
        list.appendChild(div);
      });

      if (count) {
        count.textContent = songs.length + (songs.length === 1 ? " brano" : " brani");
      }
    }

    function clearSongs() {
      if (!confirm("Vuoi davvero cancellare tutti i brani / testi?")) return;
      songs = [];
      localStorage.setItem(SONGS_KEY, JSON.stringify([]));
      renderSongs();
      updateSummaryCounts();
    }

    function exportSongs() {
      if (!songs.length) {
        alert("Non ci sono brani da esportare.");
        return;
      }
      let content = "LUCEBOX MUSICA & TESTI – Versione 8\n\n";
      songs.forEach((song, i) => {
        content += `#${i+1}\n`;
        content += `Titolo: ${song.title}\n`;
        content += `Parte: ${song.part}\n`;
        content += `Mood: ${song.mood}\n`;
        content += `BPM: ${song.bpm}\n`;
        content += `Data: ${song.date}\n\n`;
        content += `TESTO:\n${song.lyrics}\n\n`;
        content += `PROMPT SUNO:\n${song.suno}\n\n`;
        content += `IDEE VIDEO:\n${song.video}\n`;
        content += "-------------------------\n\n";
      });
      const blob = new Blob([content], {type: "text/plain;charset=utf-8"});
      const url = URL.createObjectURL(blob);
      const a = document.createElement("a");
      a.href = url;
      a.download = "lucebox_musica_v8.txt";
      a.click();
      URL.revokeObjectURL(url);
    }

    /* ------------ FOTO ------------ */
    let photos = [];
    const PHOTOS_KEY = "lucebox_v6_photos";

    function loadPhotos() {
      const raw = localStorage.getItem(PHOTOS_KEY);
      photos = raw ? JSON.parse(raw) : [];
      renderPhotos();
    }

    function setupPhotoPreview() {
      const fileInput = document.getElementById("photo-file");
      const preview = document.getElementById("photo-preview");
      fileInput.addEventListener("change", function () {
        const file = this.files[0];
        if (!file) {
          preview.style.display = "none";
          return;
        }
        const reader = new FileReader();
        reader.onload = function(e) {
          preview.src = e.target.result;
          preview.style.display = "block";
        };
        reader.readAsDataURL(file);
      });
    }

    function savePhoto() {
      const title = document.getElementById("photo-title").value.trim();
      const note = document.getElementById("photo-note").value.trim();
      const fileInput = document.getElementById("photo-file");
      const preview = document.getElementById("photo-preview");

      if (!fileInput.files[0]) {
        alert("Carica un'immagine!");
        return;
      }

      const imageBase64 = preview.src;
      const now = new Date();
      const dateStr = now.toLocaleString("it-IT");

      photos.push({
        title,
        note,
        image: imageBase64,
        date: dateStr
      });

      localStorage.setItem(PHOTOS_KEY, JSON.stringify(photos));
      document.getElementById("photo-title").value = "";
      document.getElementById("photo-note").value = "";
      fileInput.value = "";
      preview.style.display = "none";

      renderPhotos();
    }

    function renderPhotos() {
      const list = document.getElementById("photos-list");
      const count = document.getElementById("photos-count");

      if (!photos.length) {
        list.innerHTML = '<div class="empty-text">Nessuna foto salvata.</div>';
      } else {
        list.innerHTML = "";
        photos.slice().reverse().forEach(p => {
          const div = document.createElement("div");
          div.className = "photo-item";
          div.innerHTML = `
            <img src="${p.image}" class="photo-thumb" />
            <div style="flex:1;">
              <div class="item-title">${p.title || "(senza titolo)"}</div>
              <div style="font-size:0.78rem;color:var(--text-soft);">${p.note || ""}</div>
              <div style="font-size:0.7rem;color:var(--text-soft);">${p.date}</div>
            </div>
            <button class="btn-secondary" onclick="openPhoto('${p.image}')">Apri</button>
          `;
          list.appendChild(div);
        });
      }
      if (count) count.textContent = photos.length + (photos.length === 1 ? " foto" : " foto");
      updateSummaryCounts();
    }

    function openPhoto(src) {
      const w = window.open();
      w.document.write('<img src="' + src + '" style="max-width:100%;height:auto;"/>');
    }

    function clearPhotos() {
      if (!confirm("Vuoi davvero cancellare tutte le foto?")) return;
      photos = [];
      localStorage.setItem(PHOTOS_KEY, JSON.stringify([]));
      renderPhotos();
      updateSummaryCounts();
    }

    /* ------------ FILE ------------ */
    let files = [];
    const FILES_KEY = "lucebox_v6_files";

    function loadFiles() {
      const raw = localStorage.getItem(FILES_KEY);
      files = raw ? JSON.parse(raw) : [];
      renderFiles();
    }

    function saveFile() {
      const title = document.getElementById("file-title").value.trim();
      const note = document.getElementById("file-note").value.trim();
      const fileInput = document.getElementById("file-upload");

      if (!fileInput.files[0]) {
        alert("Carica un file!");
        return;
      }

      const file = fileInput.files[0];
      const reader = new FileReader();
      reader.onload = function(e) {
        const base64 = e.target.result;
        const now = new Date();
        const dateStr = now.toLocaleString("it-IT");
        files.push({
          title,
          note,
          name: file.name,
          data: base64,
          date: dateStr
        });
        localStorage.setItem(FILES_KEY, JSON.stringify(files));
        renderFiles();
      };
      reader.readAsDataURL(file);

      document.getElementById("file-title").value = "";
      document.getElementById("file-note").value = "";
      fileInput.value = "";
    }

    function renderFiles() {
      const list = document.getElementById("files-list");
      const count = document.getElementById("files-count");

      if (!files.length) {
        list.innerHTML = '<div class="empty-text">Nessun file salvato.</div>';
      } else {
        list.innerHTML = "";
        files.slice().reverse().forEach(f => {
          const div = document.createElement("div");
          div.className = "file-item";
          div.innerHTML = `
            <div class="item-title">${f.title || "(senza titolo)"}</div>
            <div style="font-size:0.78rem;color:var(--text-soft);">${f.note || ""}</div>
            <div style="font-size:0.75rem;color:var(--text-soft);">${f.name}</div>
            <div style="font-size:0.7rem;color:var(--text-soft);">${f.date}</div>
            <button class="btn-secondary" onclick="openFile('${f.data}', '${f.name}')">Apri</button>
          `;
          list.appendChild(div);
        });
      }
      if (count) count.textContent = files.length + (files.length === 1 ? " file" : " file");
      updateSummaryCounts();
    }

    function openFile(data, name) {
      const a = document.createElement("a");
      a.href = data;
      a.download = name;
      a.click();
    }

    function clearFiles() {
      if (!confirm("Vuoi davvero cancellare tutti i file?")) return;
      files = [];
      localStorage.setItem(FILES_KEY, JSON.stringify([]));
      renderFiles();
      updateSummaryCounts();
    }

    /* ------------ SUMMARY HOME ------------ */
    function updateSummaryCounts() {
      const ideasEl = document.getElementById("ideas-count");
      const photosEl = document.getElementById("photos-count");
      const filesEl = document.getElementById("files-count");
      const diaryEl = document.getElementById("diary-count");
      const songsEl = document.getElementById("songs-count");

      if (ideasEl) ideasEl.textContent = ideas.length + (ideas.length === 1 ? " idea" : " idee");
      if (photosEl) photosEl.textContent = photos.length + (photos.length === 1 ? " foto" : " foto");
      if (filesEl) filesEl.textContent = files.length + (files.length === 1 ? " file" : " file");
      if (diaryEl) diaryEl.textContent = diaryEntries.length + (diaryEntries.length === 1 ? " giorno" : " giorni");
      if (songsEl) songsEl.textContent = songs.length + (songs.length === 1 ? " brano" : " brani");
    }

    /* ------------ AVVIO ------------ */
    window.addEventListener("DOMContentLoaded", () => {
      loadTheme();
      setupHashtags();
      setupMoodButtons();
      setTodayInDiary();
      loadIdeas();
      loadDiary();
      loadSongs();
      loadPhotos();
      loadFiles();
      setupPhotoPreview();
      updateSummaryCounts();
    });
  </script>
  <script>
    // Registrazione del service worker per la modalità "app"
    if ("serviceWorker" in navigator) {
      window.addEventListener("load", () => {
        navigator.serviceWorker
          .register("./service-worker.js")
          .catch(err => console.log("SW error", err));
      });
    }
  </script>

</body>
</html>
