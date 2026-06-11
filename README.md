# 2027 Sales Conference Timelines

<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Event Timeline Tracker</title>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@3.9.0/dist/tabler-icons.min.css" />
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #ffffff;
    --bg-secondary: #f5f5f4;
    --bg-tertiary: #f0efed;
    --text: #1a1a18;
    --text-secondary: #5f5e5a;
    --text-tertiary: #8a8a85;
    --border: rgba(0,0,0,0.12);
    --border-md: rgba(0,0,0,0.22);
    --radius-md: 8px;
    --radius-lg: 12px;
    --font: system-ui, -apple-system, 'Segoe UI', sans-serif;
  }

  @media (prefers-color-scheme: dark) {
    :root {
      --bg: #1c1c1a;
      --bg-secondary: #252522;
      --bg-tertiary: #2e2e2b;
      --text: #f0efeb;
      --text-secondary: #a8a8a2;
      --text-tertiary: #6a6a65;
      --border: rgba(255,255,255,0.1);
      --border-md: rgba(255,255,255,0.2);
    }
  }

  body {
    font-family: var(--font);
    background: var(--bg-tertiary);
    color: var(--text);
    min-height: 100vh;
    padding: 2rem 1rem;
  }

  .container { max-width: 1100px; margin: 0 auto; }

  .layout {
    display: grid;
    grid-template-columns: 1fr 280px;
    gap: 1.25rem;
    align-items: start;
  }

  .sidebar { position: sticky; top: 2rem; }

  .guidelines-card {
    background: var(--bg);
    border: 0.5px solid var(--border);
    border-radius: var(--radius-lg);
    padding: 1.25rem;
  }

  .guidelines-card h2 {
    font-size: 14px;
    font-weight: 500;
    margin-bottom: 1rem;
    color: var(--text);
  }

  .guideline-item {
    display: flex;
    gap: 10px;
    padding: 9px 0;
    border-bottom: 0.5px solid var(--border);
  }

  .guideline-item:last-child { border-bottom: none; padding-bottom: 0; }
  .guideline-item:first-of-type { padding-top: 0; }

  .guideline-num {
    font-size: 11px;
    font-weight: 500;
    color: var(--text-tertiary);
    min-width: 16px;
    padding-top: 1px;
  }

  .guideline-text {
    font-size: 13px;
    color: var(--text-secondary);
    line-height: 1.5;
  }

  .guideline-text strong {
    font-weight: 500;
    color: var(--text);
  }

  @media (max-width: 760px) {
    .layout { grid-template-columns: 1fr; }
    .sidebar { position: static; }
  }

  h1 {
    font-size: 22px;
    font-weight: 500;
    margin-bottom: 0.25rem;
    color: var(--text);
  }

  .subtitle {
    font-size: 14px;
    color: var(--text-secondary);
    margin-bottom: 1.5rem;
  }

  .card-panel {
    background: var(--bg);
    border: 0.5px solid var(--border);
    border-radius: var(--radius-lg);
    padding: 1.25rem;
    margin-bottom: 1rem;
  }

  .progress-label {
    font-size: 13px;
    color: var(--text-secondary);
    margin-bottom: 6px;
    display: flex;
    justify-content: space-between;
  }

  .progress-track {
    height: 6px;
    background: var(--bg-secondary);
    border-radius: 3px;
    overflow: hidden;
  }

  .progress-fill {
    height: 100%;
    background: #639922;
    border-radius: 3px;
    transition: width 0.3s ease;
  }

  .toolbar {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    margin-bottom: 1rem;
  }

  input[type="text"], input[type="date"], select, textarea {
    font-family: var(--font);
    font-size: 14px;
    color: var(--text);
    background: var(--bg);
    border: 0.5px solid var(--border-md);
    border-radius: var(--radius-md);
    padding: 0 12px;
    height: 36px;
    outline: none;
    transition: border-color 0.15s;
    -webkit-appearance: none;
    appearance: none;
  }

  input[type="text"]:focus, input[type="date"]:focus, select:focus, textarea:focus {
    border-color: #185FA5;
    box-shadow: 0 0 0 3px rgba(24,95,165,0.12);
  }

  select {
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 24 24' fill='none' stroke='%23888' stroke-width='2'%3E%3Cpolyline points='6 9 12 15 18 9'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: right 10px center;
    padding-right: 30px;
    cursor: pointer;
  }

  textarea {
    height: auto;
    padding: 8px 12px;
    resize: vertical;
  }

  .toolbar input[type="text"] { flex: 1; min-width: 160px; }
  .toolbar input[type="date"] { width: 150px; }
  .toolbar select { width: 140px; }

  button {
    font-family: var(--font);
    font-size: 14px;
    font-weight: 400;
    color: var(--text);
    background: transparent;
    border: 0.5px solid var(--border-md);
    border-radius: var(--radius-md);
    padding: 0 14px;
    height: 36px;
    cursor: pointer;
    display: inline-flex;
    align-items: center;
    gap: 6px;
    transition: background 0.1s, transform 0.1s;
    white-space: nowrap;
  }

  button:hover { background: var(--bg-secondary); }
  button:active { transform: scale(0.98); }

  .filter-bar {
    display: flex;
    gap: 6px;
    flex-wrap: wrap;
    margin-bottom: 1.25rem;
  }

  .filter-chip {
    padding: 4px 12px;
    height: 28px;
    font-size: 13px;
    border-radius: 20px;
    border: 0.5px solid var(--border);
    background: transparent;
    cursor: pointer;
    color: var(--text-secondary);
  }

  .filter-chip.active {
    background: var(--bg-secondary);
    color: var(--text);
    border-color: var(--border-md);
  }

  .timeline { position: relative; padding-left: 32px; }

  .timeline::before {
    content: '';
    position: absolute;
    left: 10px;
    top: 8px;
    bottom: 8px;
    width: 1px;
    background: var(--border);
  }

  .milestone { position: relative; margin-bottom: 10px; }

  .milestone::before {
    content: '';
    position: absolute;
    left: -26px;
    top: 14px;
    width: 10px;
    height: 10px;
    border-radius: 50%;
    border: 2px solid;
    background: var(--bg);
    z-index: 1;
  }

  .milestone.todo::before { border-color: #888780; }
  .milestone.in-progress::before { border-color: #185FA5; background: #B5D4F4; }
  .milestone.done::before { border-color: #3B6D11; background: #97C459; }
  .milestone.at-risk::before { border-color: #BA7517; background: #FAC775; }

  .m-card {
    background: var(--bg);
    border: 0.5px solid var(--border);
    border-radius: var(--radius-lg);
    padding: 11px 14px;
    display: flex;
    align-items: flex-start;
    gap: 10px;
    transition: border-color 0.15s;
  }

  .m-card:hover { border-color: var(--border-md); }

  .m-body { flex: 1; min-width: 0; }

  .m-top {
    display: flex;
    align-items: baseline;
    gap: 8px;
    flex-wrap: wrap;
    margin-bottom: 3px;
  }

  .m-title { font-size: 14px; font-weight: 500; }

  .m-date {
    font-size: 12px;
    color: var(--text-secondary);
  }

  .m-notes {
    font-size: 13px;
    color: var(--text-secondary);
    line-height: 1.5;
    margin-top: 2px;
  }

  .badge {
    font-size: 11px;
    padding: 2px 8px;
    border-radius: 10px;
    font-weight: 500;
  }

  .badge-todo { background: #F1EFE8; color: #5F5E5A; }
  .badge-in-progress { background: #E6F1FB; color: #185FA5; }
  .badge-done { background: #EAF3DE; color: #3B6D11; }
  .badge-at-risk { background: #FAEEDA; color: #854F0B; }

  @media (prefers-color-scheme: dark) {
    .badge-todo { background: #2e2e2b; color: #b4b2a9; }
    .badge-in-progress { background: #0c2a45; color: #85b7eb; }
    .badge-done { background: #152808; color: #97c459; }
    .badge-at-risk { background: #2e1e05; color: #fac775; }
  }

  .m-actions { display: flex; gap: 2px; flex-shrink: 0; }

  .icon-btn {
    background: none;
    border: none;
    cursor: pointer;
    padding: 5px;
    border-radius: 6px;
    color: var(--text-secondary);
    font-size: 16px;
    height: auto;
    width: auto;
  }

  .icon-btn:hover { background: var(--bg-secondary); color: var(--text); }
  .icon-btn:active { transform: scale(0.95); }

  .empty {
    text-align: center;
    padding: 2.5rem 1rem;
    color: var(--text-secondary);
    font-size: 14px;
  }

  .empty i { font-size: 28px; display: block; margin-bottom: 8px; }

  /* Modal */
  .modal-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.35);
    z-index: 100;
    align-items: center;
    justify-content: center;
    padding: 1rem;
  }

  .modal-overlay.open { display: flex; }

  .modal {
    background: var(--bg);
    border: 0.5px solid var(--border-md);
    border-radius: var(--radius-lg);
    padding: 1.5rem;
    width: 380px;
    max-width: 100%;
  }

  .modal h2 {
    font-size: 16px;
    font-weight: 500;
    margin-bottom: 1.1rem;
  }

  .field { margin-bottom: 12px; }

  .field label {
    font-size: 12px;
    color: var(--text-secondary);
    display: block;
    margin-bottom: 4px;
  }

  .field input[type="text"],
  .field input[type="date"],
  .field select,
  .field textarea { width: 100%; }

  .field textarea { height: 80px; }

  .modal-actions {
    display: flex;
    gap: 8px;
    justify-content: flex-end;
    margin-top: 1.25rem;
  }

  .btn-primary {
    background: var(--text);
    color: var(--bg);
    border-color: transparent;
  }

  .btn-primary:hover { background: var(--text-secondary); }

  /* Toast */
  .toast {
    position: fixed;
    bottom: 1.5rem;
    left: 50%;
    transform: translateX(-50%) translateY(20px);
    background: var(--text);
    color: var(--bg);
    font-size: 13px;
    padding: 8px 16px;
    border-radius: 20px;
    opacity: 0;
    transition: opacity 0.2s, transform 0.2s;
    pointer-events: none;
    white-space: nowrap;
    z-index: 200;
  }

  .toast.show { opacity: 1; transform: translateX(-50%) translateY(0); }

  @media (max-width: 520px) {
    .toolbar { gap: 6px; }
    .toolbar input[type="date"] { width: 130px; }
    .toolbar select { width: 120px; }
  }
</style>
</head>
<body>
<div class="container">
  <h1>Event timeline</h1>
  <p class="subtitle">Track milestones and stay on top of what's left to do.</p>

  <div class="layout">
    <div class="main-col">
      <div class="card-panel">
        <div class="progress-label">
          <span id="prog-label">0 of 0 milestones complete</span>
          <span id="prog-pct">0%</span>
        </div>
        <div class="progress-track">
          <div class="progress-fill" id="prog-fill" style="width:0%"></div>
        </div>
      </div>

      <div class="card-panel">
        <div class="toolbar">
          <input type="text" id="new-title" placeholder="New milestone name…" aria-label="Milestone name" />
          <input type="date" id="new-date" aria-label="Due date" />
          <select id="new-status" aria-label="Status">
            <option value="todo">To do</option>
            <option value="in-progress">In progress</option>
            <option value="done">Done</option>
            <option value="at-risk">At risk</option>
          </select>
          <button onclick="addMilestone()">
            <i class="ti ti-plus" aria-hidden="true"></i> Add milestone
          </button>
        </div>

        <div class="filter-bar" role="group" aria-label="Filter by status">
          <button class="filter-chip active" data-filter="all" onclick="setFilter('all', this)">All</button>
          <button class="filter-chip" data-filter="todo" onclick="setFilter('todo', this)">To do</button>
          <button class="filter-chip" data-filter="in-progress" onclick="setFilter('in-progress', this)">In progress</button>
          <button class="filter-chip" data-filter="at-risk" onclick="setFilter('at-risk', this)">At risk</button>
          <button class="filter-chip" data-filter="done" onclick="setFilter('done', this)">Done</button>
        </div>

        <div class="timeline" id="timeline" aria-live="polite"></div>
      </div>
    </div>

    <div class="sidebar">
      <div class="guidelines-card">
        <h2><i class="ti ti-checklist" aria-hidden="true" style="font-size:15px;vertical-align:-2px;margin-right:6px;"></i>Standard guidelines</h2>
        <div class="guideline-item">
          <span class="guideline-num">1</span>
          <span class="guideline-text"><strong>1 presenter per session</strong> — 2 allowed for sessions over 30 min</span>
        </div>
        <div class="guideline-item">
          <span class="guideline-num">2</span>
          <span class="guideline-text"><strong>Avoid workshops</strong> unless Kevin has specifically requested it</span>
        </div>
        <div class="guideline-item">
          <span class="guideline-num">3</span>
          <span class="guideline-text"><strong>Prioritize client speakers</strong> and get them introduced to Marcomm early</span>
        </div>
        <div class="guideline-item">
          <span class="guideline-num">4</span>
          <span class="guideline-text"><strong>Clear and short session titles</strong></span>
        </div>
        <div class="guideline-item">
          <span class="guideline-num">5</span>
          <span class="guideline-text"><strong>Every session needs</strong> next steps / action items</span>
        </div>
        <div class="guideline-item">
          <span class="guideline-num">6</span>
          <span class="guideline-text"><strong>WHY does this matter</strong> — always answer this for every session</span>
        </div>
        <div class="guideline-item">
          <span class="guideline-num">7</span>
          <span class="guideline-text"><strong>Pre-conference reading material</strong> should be referenced in every session</span>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- Edit modal -->
<div class="modal-overlay" id="edit-modal" role="dialog" aria-modal="true" aria-labelledby="modal-title">
  <div class="modal">
    <h2 id="modal-title">Edit milestone</h2>
    <div class="field"><label for="edit-title">Name</label><input type="text" id="edit-title" /></div>
    <div class="field"><label for="edit-date">Date</label><input type="date" id="edit-date" /></div>
    <div class="field">
      <label for="edit-status">Status</label>
      <select id="edit-status">
        <option value="todo">To do</option>
        <option value="in-progress">In progress</option>
        <option value="done">Done</option>
        <option value="at-risk">At risk</option>
      </select>
    </div>
    <div class="field"><label for="edit-notes">Notes</label><textarea id="edit-notes" placeholder="Optional notes…"></textarea></div>
    <div class="modal-actions">
      <button onclick="closeModal()">Cancel</button>
      <button class="btn-primary" onclick="saveEdit()">Save changes</button>
    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
  const BADGE = { todo: 'badge-todo', 'in-progress': 'badge-in-progress', done: 'badge-done', 'at-risk': 'badge-at-risk' };
  const LABELS = { todo: 'To do', 'in-progress': 'In progress', done: 'Done', 'at-risk': 'At risk' };
  const STORE_KEY = 'event-timeline-v1';

  let milestones = [];
  let nextId = 1;
  let activeFilter = 'all';
  let editingId = null;

  function load() {
    try {
      const raw = localStorage.getItem(STORE_KEY);
      if (raw) {
        const d = JSON.parse(raw);
        milestones = d.milestones || [];
        nextId = d.nextId || (milestones.length + 1);
      }
    } catch(e) {}
    if (!milestones.length) {
      milestones = [
        { id: 1,  title: 'Finalize the Theme/Keynote',          date: '', status: 'todo', notes: 'October' },
        { id: 2,  title: 'Call for Abstracts',                   date: '', status: 'todo', notes: 'October' },
        { id: 3,  title: 'Call for Abstracts to SV Leads',       date: '', status: 'todo', notes: 'November' },
        { id: 4,  title: 'SV Leads start working on agenda',     date: '', status: 'todo', notes: 'November' },
        { id: 5,  title: 'SV Leads work on agenda',              date: '', status: 'todo', notes: 'December' },
        { id: 6,  title: 'Finalize 2nd Chance Process',          date: '', status: 'todo', notes: 'January' },
        { id: 7,  title: 'Roster final',                         date: '', status: 'todo', notes: 'January' },
        { id: 8,  title: 'Kevin review of agenda',               date: '', status: 'todo', notes: 'January' },
        { id: 9,  title: 'Kevin review of agenda',               date: '', status: 'todo', notes: 'February' },
        { id: 10, title: 'TED Talk Announcement out',            date: '', status: 'todo', notes: 'February' },
        { id: 11, title: 'Ted Talk Submissions/Winner',          date: '', status: 'todo', notes: 'February' },
        { id: 12, title: 'Book/Podcast Announcement',            date: '', status: 'todo', notes: 'February' },
        { id: 13, title: 'Finalize Client Speakers',             date: '', status: 'todo', notes: 'February' },
        { id: 14, title: 'Agenda sent',                          date: '', status: 'todo', notes: 'March — due by March 15' },
        { id: 15, title: 'Kick off call with Kevin and presenters', date: '', status: 'todo', notes: 'March' },
        { id: 16, title: 'Prep calls with presenters',           date: '', status: 'todo', notes: 'March' },
        { id: 17, title: 'Ask SV Leaders to propose award recipients', date: '', status: 'todo', notes: 'March' },
        { id: 18, title: 'Awards Finalized to Marcomm',          date: '', status: 'todo', notes: 'April' },
        { id: 19, title: 'PPTs due',                             date: '', status: 'todo', notes: 'April — due April 15' },
        { id: 20, title: 'PPT Proofreading',                     date: '', status: 'todo', notes: 'April' },
        { id: 21, title: 'Conference!',                          date: '', status: 'todo', notes: 'May' },
      ];
      nextId = 22;
      save();
    }
  }

  function save() {
    try { localStorage.setItem(STORE_KEY, JSON.stringify({ milestones, nextId })); } catch(e) {}
  }

  function fmt(d) {
    if (!d) return '';
    const p = d.split('-');
    return `${p[1]}/${p[2]}/${p[0]}`;
  }

  function esc(s) {
    return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  function render() {
    const tl = document.getElementById('timeline');
    const visible = activeFilter === 'all' ? milestones : milestones.filter(m => m.status === activeFilter);
    const done = milestones.filter(m => m.status === 'done').length;
    const total = milestones.length;
    const pct = total ? Math.round(done / total * 100) : 0;

    document.getElementById('prog-label').textContent = `${done} of ${total} milestone${total !== 1 ? 's' : ''} complete`;
    document.getElementById('prog-pct').textContent = pct + '%';
    document.getElementById('prog-fill').style.width = pct + '%';

    if (!visible.length) {
      tl.innerHTML = `<div class="empty"><i class="ti ti-calendar-off" aria-hidden="true"></i>No milestones here yet</div>`;
      return;
    }

    tl.innerHTML = visible.map(m => `
      <div class="milestone ${m.status}">
        <div class="m-card">
          <div class="m-body">
            <div class="m-top">
              <span class="m-title">${esc(m.title)}</span>
              ${m.date ? `<span class="m-date"><i class="ti ti-calendar" aria-hidden="true" style="font-size:12px;vertical-align:-1px;margin-right:3px;"></i>${fmt(m.date)}</span>` : ''}
              <span class="badge ${BADGE[m.status]}">${LABELS[m.status]}</span>
            </div>
            ${m.notes ? `<div class="m-notes">${esc(m.notes)}</div>` : ''}
          </div>
          <div class="m-actions">
            <button class="icon-btn" title="Edit" aria-label="Edit ${esc(m.title)}" onclick="openEdit(${m.id})"><i class="ti ti-edit" aria-hidden="true"></i></button>
            <button class="icon-btn" title="Delete" aria-label="Delete ${esc(m.title)}" onclick="remove(${m.id})"><i class="ti ti-trash" aria-hidden="true"></i></button>
          </div>
        </div>
      </div>
    `).join('');
  }

  function addMilestone() {
    const t = document.getElementById('new-title').value.trim();
    if (!t) { document.getElementById('new-title').focus(); return; }
    milestones.push({
      id: nextId++,
      title: t,
      date: document.getElementById('new-date').value,
      status: document.getElementById('new-status').value,
      notes: ''
    });
    document.getElementById('new-title').value = '';
    document.getElementById('new-date').value = '';
    save();
    render();
    toast('Milestone added');
  }

  function remove(id) {
    if (!confirm('Delete this milestone?')) return;
    milestones = milestones.filter(m => m.id !== id);
    save();
    render();
    toast('Milestone deleted');
  }

  function setFilter(f, el) {
    activeFilter = f;
    document.querySelectorAll('.filter-chip').forEach(c => c.classList.remove('active'));
    el.classList.add('active');
    render();
  }

  function openEdit(id) {
    editingId = id;
    const m = milestones.find(x => x.id === id);
    document.getElementById('edit-title').value = m.title;
    document.getElementById('edit-date').value = m.date;
    document.getElementById('edit-status').value = m.status;
    document.getElementById('edit-notes').value = m.notes;
    document.getElementById('edit-modal').classList.add('open');
    document.getElementById('edit-title').focus();
  }

  function closeModal() {
    document.getElementById('edit-modal').classList.remove('open');
  }

  function saveEdit() {
    const m = milestones.find(x => x.id === editingId);
    const t = document.getElementById('edit-title').value.trim();
    m.title = t || m.title;
    m.date = document.getElementById('edit-date').value;
    m.status = document.getElementById('edit-status').value;
    m.notes = document.getElementById('edit-notes').value;
    closeModal();
    save();
    render();
    toast('Changes saved');
  }

  function toast(msg) {
    const el = document.getElementById('toast');
    el.textContent = msg;
    el.classList.add('show');
    setTimeout(() => el.classList.remove('show'), 2000);
  }

  document.getElementById('edit-modal').addEventListener('click', e => {
    if (e.target === e.currentTarget) closeModal();
  });

  document.addEventListener('keydown', e => {
    if (e.key === 'Escape') closeModal();
  });

  document.getElementById('new-title').addEventListener('keydown', e => {
    if (e.key === 'Enter') addMilestone();
  });

  load();
  render();
</script>
</body>
</html>
