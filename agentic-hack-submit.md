# Agentic Hack Rome: Submission Assistant

> **For the AI reading this:** This skill prepares the Agentic Hack Rome submission for the hacker.
> Trigger: whenever the hacker says "help me prepare the submission", "/submit", "prepara la submission", or any equivalent phrasing.
> Follow the steps below in order. Do not skip steps.

---

## Step 1: Scan the project

Read the following files if they exist. Extract what you find.

**README.md**
- Project name: first H1 heading (`# Project Name`)
- One-line description: subtitle or first sentence after the H1
- What the project does: first paragraph or "About" section
- Technologies mentioned: any frameworks, APIs, AI models, tools listed

**package.json** (if present)
- Project name: `name` field
- Technologies: keys in `dependencies` and `devDependencies`

**pyproject.toml** (if present)
- Project name: `[project] name` field
- Technologies: `[project] dependencies`

**Cargo.toml** (if present)
- Project name: `[package] name` field
- Technologies: `[dependencies]` section

**Git remote URL**
Run: `git remote -v`
Extract the GitHub repo URL from the output (look for `origin fetch` line, convert SSH to HTTPS if needed: `git@github.com:user/repo.git` → `https://github.com/user/repo`).
- If the remote is already HTTPS, strip the trailing `.git` suffix if present (e.g. `https://github.com/user/repo.git` → `https://github.com/user/repo`).
- For non-GitHub remotes, use the URL as-is.

After scanning, make a note of what you found and what is still missing.

---

## Step 2: Ask for missing fields

Ask for the fields you could not auto-detect. Ask one question at a time. Do not bundle multiple questions into one message.

**Always ask (cannot be auto-detected):**

1. Team lead name: "What is your name?" (team lead)
2. Team lead email: "What is your email?"
3. Other team members: "Are there other team members? If yes, list their name, email, and optionally GitHub or LinkedIn (one per line). If not, just say no."
4. Video demo link: "Do you have a video demo link? (YouTube, Loom, Drive, etc.) If not recorded yet, say 'not yet'."

**Ask only if not found during scan:**
- Project name
- One-line description (max 100 characters)
- What the project does (2-3 sentences: problem + solution)
- Key technologies and agentic tools used

After collecting all fields, confirm the full submission with the hacker before generating the HTML:

> "Here is your complete submission. Does everything look correct?
> - Project name: [value]
> - Team lead: [name] ([email])
> - Other members: [value or "none"]
> - One-line description: [value]
> - What it does: [value]
> - GitHub repo: [value]
> - Video demo: [value or "not yet recorded"]
> - Technologies: [value]"

Wait for confirmation. If they request changes, update the relevant fields and confirm again.

---

## Step 3: Generate the HTML

Once the hacker confirms the submission, generate the file below.

Replace every `{{PLACEHOLDER}}` with the actual collected value:
- `{{PROJECT_NAME}}` → project name
- `{{TEAM_LEAD_NAME}}` → team lead name
- `{{TEAM_LEAD_EMAIL}}` → team lead email
- `{{OTHER_MEMBERS}}` → other members (or "—" if none)
- `{{ONE_LINE}}` → one-line description
- `{{WHAT_IT_DOES}}` → 2-3 sentence description
- `{{GITHUB_URL}}` → GitHub repo URL
- `{{VIDEO_URL}}` → video demo link (or leave blank if not yet recorded -- skip the copy button for this field if the value is blank)
- `{{TECHNOLOGIES}}` → key technologies and agentic tools
- `{{FORM_URL}}` → https://forms.gle/6KJuyYJm8FfwEKpY6

Write the following HTML to `/tmp/agentic-hack-submit.html`:

---

```html
<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Agentic Hack Rome — Submission del progetto</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700;900&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
    :root {
      --pink: #CC2B5E; --purple: #753A88;
      --gradient: linear-gradient(135deg, #CC2B5E 0%, #753A88 100%);
      --bg: #F8F6EE; --card: #FFFFFF; --border: #E2DDD4;
      --text: #3a3a3a; --muted: #6B7280;
    }
    body { font-family: 'Poppins', sans-serif; background: var(--bg); color: var(--text); min-height: 100vh; padding: 48px 24px; }
    .container { max-width: 640px; margin: 0 auto; }
    .header { text-align: center; margin-bottom: 40px; }
    .badge { display: inline-block; background: var(--gradient); color: white; font-size: 0.75rem; font-weight: 600; letter-spacing: 0.08em; text-transform: uppercase; padding: 4px 14px; border-radius: 99px; margin-bottom: 16px; }
    .header h1 { font-size: 1.75rem; font-weight: 900; color: #000; margin-bottom: 6px; }
    .header p { color: var(--muted); font-size: 0.9rem; }
    .deadline { display: inline-block; margin-top: 10px; background: #fff3cd; border: 1px solid #f0c040; color: #7a5700; font-size: 0.82rem; font-weight: 600; padding: 5px 14px; border-radius: 8px; }
    .form-btn { display: block; width: 100%; background: var(--gradient); color: white; text-align: center; font-weight: 700; font-size: 1rem; padding: 14px; border-radius: 10px; text-decoration: none; margin-bottom: 32px; transition: opacity 0.2s; }
    .form-btn:hover { opacity: 0.88; }
    .fields { display: flex; flex-direction: column; gap: 12px; margin-bottom: 32px; }
    .field { background: var(--card); border: 1px solid var(--border); border-radius: 10px; padding: 14px 16px; }
    .field-label { font-size: 0.72rem; font-weight: 600; text-transform: uppercase; letter-spacing: 0.06em; color: var(--muted); margin-bottom: 4px; }
    .field-row { display: flex; align-items: flex-start; gap: 10px; }
    .field-value { flex: 1; font-size: 0.92rem; color: var(--text); line-height: 1.5; word-break: break-word; white-space: pre-wrap; }
    .copy-btn { flex-shrink: 0; background: none; border: 1px solid var(--border); border-radius: 6px; padding: 4px 12px; font-size: 0.78rem; font-family: 'Poppins', sans-serif; font-weight: 500; color: var(--muted); cursor: pointer; transition: all 0.15s; white-space: nowrap; }
    .copy-btn:hover { border-color: var(--pink); color: var(--pink); }
    .copy-btn.copied { border-color: #16a34a; color: #16a34a; }
    .check-card { background: var(--card); border: 1px solid var(--border); border-radius: 10px; overflow: hidden; }
    .check-header { padding: 14px 16px; font-weight: 600; font-size: 0.9rem; cursor: pointer; display: flex; justify-content: space-between; align-items: center; user-select: none; }
    .check-header:hover { background: #f5f3ed; }
    .check-body { display: none; padding: 0 16px 16px; border-top: 1px solid var(--border); }
    .check-body.open { display: block; }
    .pillar { margin-top: 14px; }
    .pillar-title { font-size: 0.8rem; font-weight: 600; color: var(--pink); margin-bottom: 6px; }
    .pillar ul { padding-left: 16px; }
    .pillar li { font-size: 0.82rem; color: var(--text); margin-bottom: 3px; }
    .footer-note { text-align: center; color: var(--muted); font-size: 0.78rem; margin-top: 28px; }
  </style>
</head>
<body>
<div class="container">
  <div class="header">
    <div class="badge">Agentic Hack Rome</div>
    <h1>Invia il tuo progetto</h1>
    <p>Copia ogni campo e incollalo nel form.</p>
    <div class="deadline">Deadline: 16:00, 11 aprile</div>
  </div>
  <a class="form-btn" href="https://forms.gle/6KJuyYJm8FfwEKpY6" target="_blank">Apri il form di submission &rarr;</a>
  <div class="fields">
    <div class="field">
      <div class="field-label">Nome del progetto</div>
      <div class="field-row">
        <div class="field-value">{{PROJECT_NAME}}</div>
        <button class="copy-btn" data-copy="{{PROJECT_NAME}}" onclick="copyField(this)">Copia</button>
      </div>
    </div>
    <div class="field">
      <div class="field-label">Nome del team lead</div>
      <div class="field-row">
        <div class="field-value">{{TEAM_LEAD_NAME}}</div>
        <button class="copy-btn" data-copy="{{TEAM_LEAD_NAME}}" onclick="copyField(this)">Copia</button>
      </div>
    </div>
    <div class="field">
      <div class="field-label">Email del team lead</div>
      <div class="field-row">
        <div class="field-value">{{TEAM_LEAD_EMAIL}}</div>
        <button class="copy-btn" data-copy="{{TEAM_LEAD_EMAIL}}" onclick="copyField(this)">Copia</button>
      </div>
    </div>
    <div class="field">
      <div class="field-label">Altri membri del team (opzionale)</div>
      <div class="field-row">
        <div class="field-value">{{OTHER_MEMBERS}}</div>
        <button class="copy-btn" data-copy="{{OTHER_MEMBERS}}" onclick="copyField(this)">Copia</button>
      </div>
    </div>
    <div class="field">
      <div class="field-label">Descrizione in una riga</div>
      <div class="field-row">
        <div class="field-value">{{ONE_LINE}}</div>
        <button class="copy-btn" data-copy="{{ONE_LINE}}" onclick="copyField(this)">Copia</button>
      </div>
    </div>
    <div class="field">
      <div class="field-label">Cosa fa il vostro progetto?</div>
      <div class="field-row">
        <div class="field-value">{{WHAT_IT_DOES}}</div>
        <button class="copy-btn" data-copy="{{WHAT_IT_DOES}}" onclick="copyField(this)">Copia</button>
      </div>
    </div>
    <div class="field">
      <div class="field-label">URL della repo GitHub</div>
      <div class="field-row">
        <div class="field-value">{{GITHUB_URL}}</div>
        <button class="copy-btn" data-copy="{{GITHUB_URL}}" onclick="copyField(this)">Copia</button>
      </div>
    </div>
    <div class="field">
      <div class="field-label">Link alla video demo</div>
      <div class="field-row">
        <div class="field-value">{{VIDEO_URL}}</div>
        <button class="copy-btn" data-copy="{{VIDEO_URL}}" onclick="copyField(this)">Copia</button>
      </div>
    </div>
    <div class="field">
      <div class="field-label">Tecnologie chiave e tool agentici utilizzati</div>
      <div class="field-row">
        <div class="field-value">{{TECHNOLOGIES}}</div>
        <button class="copy-btn" data-copy="{{TECHNOLOGIES}}" onclick="copyField(this)">Copia</button>
      </div>
    </div>
  </div>
  <div class="check-card">
    <div class="check-header" onclick="toggleCheck()">
      <span>Check rapido prima di inviare</span>
      <span id="arrow">&#9660;</span>
    </div>
    <div class="check-body" id="checkBody">
      <div class="pillar">
        <div class="pillar-title">Idea e Impatto (33%)</div>
        <ul>
          <li>È davvero utile per le persone che vivono a Roma?</li>
          <li>Il problema è specifico e concreto?</li>
          <li>Qualcuno lo userebbe nella vita reale?</li>
        </ul>
      </div>
      <div class="pillar">
        <div class="pillar-title">Esecuzione Tecnica (33%)</div>
        <ul>
          <li>Stai usando agenti AI o tool agentici?</li>
          <li>L'architettura ha senso per il problema?</li>
          <li>Stai integrando API o dataset rilevanti?</li>
        </ul>
      </div>
      <div class="pillar">
        <div class="pillar-title">Demo-readiness (33%)</div>
        <ul>
          <li>Riesci a fare una demo end-to-end funzionante?</li>
          <li>Il video è sotto i 2 minuti e chiaro?</li>
          <li>Funziona senza crashare?</li>
        </ul>
      </div>
    </div>
  </div>
  <p class="footer-note">Generato dal tuo assistente AI. Agentic Hack Rome, 11 aprile 2026.</p>
</div>
<script>
  function copyField(btn) {
    navigator.clipboard.writeText(btn.dataset.copy).then(() => {
      btn.textContent = 'Copiato!';
      btn.classList.add('copied');
      setTimeout(() => { btn.textContent = 'Copia'; btn.classList.remove('copied'); }, 1800);
    });
  }
  function toggleCheck() {
    const body = document.getElementById('checkBody');
    const arrow = document.getElementById('arrow');
    body.classList.toggle('open');
    arrow.innerHTML = body.classList.contains('open') ? '&#9650;' : '&#9660;';
  }
</script>
</body>
</html>
```

---

## Step 4: Open the HTML in the browser

After writing the file, open it immediately:

Detect the OS from the system environment or ask the hacker if unsure. On macOS use `open`, on Linux use `xdg-open`, on Windows use `start`.

- macOS: `open /tmp/agentic-hack-submit.html`
- Linux: `xdg-open /tmp/agentic-hack-submit.html`
- Windows: `start /tmp/agentic-hack-submit.html`

Then tell the hacker:
> "Your submission page is ready and open in your browser. Click 'Apri il form di submission' to go to the form, then copy each field one by one. The form also has a consent checkbox at the end: 'Acconsento che questo progetto possa essere pubblicato sui social media e i canali di Urbe Hub.' Tick it if you agree. Good luck!"

---

*End of skill instructions.*
