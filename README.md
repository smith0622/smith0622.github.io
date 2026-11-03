# smith0622.github.io
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Nexus RTM · Kyvex</title>
  <style>
:root{
  --bg:#0b1220;--panel:#121a2b;--line:#22304a;--text:#e6edf7;--muted:#8a9bb8;
  --accent:#2dd4bf;--critico:#ef4444;--alto:#f97316;--medio:#eab308;--bajo:#22c55e;
}
*{box-sizing:border-box}
body{margin:0;font-family:system-ui,Segoe UI,Roboto,sans-serif;background:var(--bg);color:var(--text)}
.hidden{display:none!important}
h1,h2,h3{margin:0 0 .6rem}
h3{font-size:1rem;color:var(--muted);font-weight:600}
.muted{color:var(--muted)}
.error{color:#fca5a5;min-height:1.2em;margin:.5rem 0;font-size:.9rem}
.hint{color:var(--muted);font-size:.8rem}

label{display:block;margin-bottom:.8rem;font-size:.85rem;color:var(--muted)}
label.check{display:flex;gap:.5rem;align-items:center}
input,select,textarea{width:100%;margin-top:.3rem;padding:.6rem .7rem;background:#0d1626;color:var(--text);
  border:1px solid var(--line);border-radius:8px;font:inherit}
input[type=checkbox]{width:auto;margin:0}
input:focus,select:focus,textarea:focus{outline:2px solid var(--accent);outline-offset:1px}
input.bad{border-color:var(--critico)}

.btn{padding:.65rem 1.1rem;border:1px solid var(--line);border-radius:8px;background:transparent;
  color:var(--text);cursor:pointer;font:inherit}
.btn.primary{background:var(--accent);color:#04201c;border-color:var(--accent);font-weight:600}
.btn:disabled{opacity:.5;cursor:not-allowed}
.link{background:none;border:0;color:var(--muted);cursor:pointer;padding:.3rem 0;text-align:left;font:inherit;font-size:.85rem}
.link:hover{color:var(--text)}

/* Login */
#login{min-height:100vh;display:grid;place-items:center;padding:1rem}
.login-card{width:min(380px,100%);background:var(--panel);border:1px solid var(--line);border-radius:14px;padding:2rem}
.login-card h1{color:var(--accent)}

/* Layout */
#app{display:grid;grid-template-columns:230px 1fr;min-height:100vh}
.side{background:var(--panel);border-right:1px solid var(--line);padding:1.2rem;display:flex;flex-direction:column;gap:1rem}
.brand{font-size:1.3rem;font-weight:700;color:var(--accent)}
.brand small{display:block;color:var(--muted);font-weight:400;font-size:.75rem}
nav{display:flex;flex-direction:column;gap:.3rem}
nav button{background:none;border:0;color:var(--muted);text-align:left;padding:.6rem .8rem;border-radius:8px;cursor:pointer;font:inherit}
nav button:hover{background:#18243b;color:var(--text)}
nav button.active{background:#18243b;color:var(--accent)}
.side-foot{margin-top:auto;display:flex;flex-direction:column;font-size:.8rem;color:var(--muted)}
.content{padding:1.5rem 2rem;overflow:auto}

.card{background:var(--panel);border:1px solid var(--line);border-radius:12px;padding:1.1rem;margin-bottom:1rem}
.grid2{display:grid;grid-template-columns:1fr 1fr;gap:1rem}
.grid2.wide-left{grid-template-columns:1.4fr 1fr}
.toolbar{max-width:240px}

/* KPIs */
.kpis{display:grid;grid-template-columns:repeat(4,1fr);gap:1rem;margin-bottom:1rem}
.kpi{background:var(--panel);border:1px solid var(--line);border-radius:12px;padding:1rem}
.kpi b{display:block;font-size:2rem}
.kpi span{color:var(--muted);font-size:.85rem}
.kpi.red b{color:var(--critico)}

/* Gráfica de barras */
.bar-row{display:grid;grid-template-columns:70px 1fr 30px;gap:.6rem;align-items:center;margin:.6rem 0;font-size:.85rem}
.bar-track{background:#0d1626;border-radius:6px;height:14px;overflow:hidden}
.bar-fill{height:100%;transition:width .5s}

/* Feed */
.live{color:var(--bajo);font-size:.75rem;margin-left:.4rem;animation:pulse 1.5s infinite}
@keyframes pulse{50%{opacity:.35}}
.feed{list-style:none;margin:0;padding:0;font-size:.85rem;font-family:ui-monospace,Consolas,monospace}
.feed li{padding:.35rem 0;border-bottom:1px solid var(--line)}
.feed time{color:var(--muted);margin-right:.5rem}

/* Tablas */
table{width:100%;border-collapse:collapse;font-size:.88rem}
th,td{padding:.6rem .5rem;text-align:left;border-bottom:1px solid var(--line)}
th{color:var(--muted);font-weight:600}
tr[data-id]{cursor:pointer}
tr[data-id]:hover,tr.sel{background:#18243b}

/* Badges */
.badge{display:inline-block;padding:.15rem .6rem;border-radius:999px;font-size:.75rem;font-weight:600;color:#0b1220}
.badge.critico{background:var(--critico)}.badge.alto{background:var(--alto)}
.badge.medio{background:var(--medio)}.badge.bajo{background:var(--bajo)}
.badge.completado{background:var(--bajo)}.badge.fallido{background:var(--critico)}

/* Progreso */
.progress{height:12px;background:#0d1626;border-radius:6px;overflow:hidden;margin:1rem 0 .5rem}
#scan-bar{height:100%;width:0;background:var(--accent);transition:width .25s}

/* Reporte */
.report h3{color:var(--text)}
.report-actions{display:flex;gap:.6rem;margin-top:1rem}

/* Toasts */
#toasts{position:fixed;right:1rem;bottom:1rem;display:flex;flex-direction:column;gap:.5rem;z-index:10}
.toast{background:var(--panel);border:1px solid var(--accent);padding:.7rem 1rem;border-radius:8px;box-shadow:0 4px 20px #0008}
.toast.err{border-color:var(--critico)}

@media(max-width:800px){
  #app{grid-template-columns:1fr}
  .side{flex-direction:row;flex-wrap:wrap;align-items:center}
  nav{flex-direction:row;flex-wrap:wrap}
  .side-foot{margin:0}
  .kpis{grid-template-columns:1fr 1fr}
  .grid2,.grid2.wide-left{grid-template-columns:1fr}
  .content{padding:1rem}
}
@media print{
  .side,.toolbar,.report-actions,#toasts{display:none!important}
  body{background:#fff;color:#000}.card{border:0}
}

</style>
</head>
<body>

<!-- ============ LOGIN + MFA (RF-01) ============ -->
<main id="login">
  <div class="login-card">
    <h1>Nexus RTM</h1>
    <p class="muted">Monitoreo de vulnerabilidades en tiempo real · Kyvex</p>

    <form id="form-login" novalidate>
      <label>Usuario <input id="l-user" value="admin" autocomplete="off"></label>
      <label>Contraseña <input id="l-pass" type="password" value="Nexus2026" autocomplete="new-password"></label>
      <button class="btn primary">Continuar</button>
    </form>

    <form id="form-mfa" class="hidden" novalidate>
      <label>Código de verificación (6 dígitos)
        <input id="l-code" inputmode="numeric" maxlength="6" value="123456" autocomplete="off">
      </label>
      <button class="btn primary">Verificar e ingresar</button>
    </form>

    <p id="login-error" class="error" role="alert"></p>
    <p class="hint">Datos de prueba (v3, ya precargados): <b>admin</b> / <b>Nexus2026</b> · código <b>123456</b></p>
  </div>
</main>

<!-- ============ APLICACIÓN ============ -->
<div id="app" class="hidden">
  <aside class="side">
    <div class="brand">Nexus RTM<small>Kyvex</small></div>
    <nav>
      <button data-view="panel">Panel de control</button>
      <button data-view="sistemas">Sistemas</button>
      <button data-view="analisis">Análisis</button>
      <button data-view="vulns">Vulnerabilidades</button>
      <button data-view="reportes">Reportes</button>
    </nav>
    <div class="side-foot">
      <span>Administrador</span>
      <button id="btn-reset" class="link">Restablecer datos</button>
      <button id="btn-logout" class="link">Cerrar sesión</button>
    </div>
  </aside>

  <main class="content">

    <!-- Panel -->
    <section id="view-panel">
      <h2>Panel de control</h2>
      <div id="kpis" class="kpis"></div>
      <div class="grid2">
        <div class="card">
          <h3>Vulnerabilidades por nivel de riesgo</h3>
          <div id="bars"></div>
        </div>
        <div class="card">
          <h3>Eventos en vivo <span class="live">● en vivo</span></h3>
          <ul id="feed" class="feed"></ul>
        </div>
      </div>
    </section>

    <!-- HU-01 Registro de sistemas -->
    <section id="view-sistemas" class="hidden">
      <h2>Registro de sistemas</h2>
      <div class="grid2">
        <form id="form-sys" class="card" novalidate>
          <h3>Nuevo sistema</h3>
          <label>Nombre del sistema <input id="s-nombre"></label>
          <label>Dirección IP <input id="s-ip" placeholder="192.168.1.50"></label>
          <label>Descripción <textarea id="s-desc" rows="3"></textarea></label>
          <p id="s-error" class="error" role="alert"></p>
          <button class="btn primary">Guardar</button>
        </form>
        <div class="card">
          <h3>Sistemas monitoreados</h3>
          <div id="sys-list"></div>
        </div>
      </div>
    </section>

    <!-- HU-02 Análisis -->
    <section id="view-analisis" class="hidden">
      <h2>Análisis de seguridad</h2>
      <div class="grid2">
        <div class="card">
          <h3>Iniciar análisis</h3>
          <label>Sistema <select id="scan-sys"></select></label>
          <label class="check"><input type="checkbox" id="scan-fail"> Simular un fallo (para probar el error)</label>
          <button id="btn-scan" class="btn primary">Iniciar análisis</button>
          <div class="progress" aria-hidden="true"><div id="scan-bar"></div></div>
          <p id="scan-status" class="muted" role="status">Sin análisis en ejecución.</p>
        </div>
        <div class="card">
          <h3>Historial de análisis</h3>
          <div id="scan-list"></div>
        </div>
      </div>
    </section>

    <!-- HU-03 / HU-04 Vulnerabilidades y riesgo -->
    <section id="view-vulns" class="hidden">
      <h2>Vulnerabilidades</h2>
      <div class="toolbar">
        <label>Nivel de riesgo
          <select id="v-filter">
            <option value="">Todos</option>
            <option value="critico">Crítico</option>
            <option value="alto">Alto</option>
            <option value="medio">Medio</option>
            <option value="bajo">Bajo</option>
          </select>
        </label>
      </div>
      <div class="grid2 wide-left">
        <div class="card" id="v-list"></div>
        <div class="card" id="v-detail"><p class="muted">Selecciona una vulnerabilidad para ver su detalle.</p></div>
      </div>
    </section>

    <!-- HU-05 Reportes -->
    <section id="view-reportes" class="hidden">
      <h2>Reportes de seguridad</h2>
      <div class="card">
        <label>Análisis completado <select id="r-scan"></select></label>
        <button id="btn-report" class="btn primary">Generar reporte</button>
      </div>
      <div id="report" class="card report hidden"></div>
    </section>

  </main>
</div>

<div id="toasts" aria-live="polite"></div>
<script>
/* Nexus RTM · Maqueta funcional (datos simulados, sin backend) */
(() => {
  const $ = s => document.querySelector(s);
  const $$ = s => [...document.querySelectorAll(s)];
  const KEY = 'nexus_rtm_v1';
  const USER = 'admin', PASS = 'Nexus2026', CODE = '123456';

  const RISK = { critico: 'Crítico', alto: 'Alto', medio: 'Medio', bajo: 'Bajo' };
  const RANGO = { critico: '9.0 – 10', alto: '7.0 – 8.9', medio: '4.0 – 6.9', bajo: '0.1 – 3.9' };
  const riskOf = s => (s >= 9 ? 'critico' : s >= 7 ? 'alto' : s >= 4 ? 'medio' : 'bajo');

  // Catálogo simulado (basado en los objetivos específicos del PPI)
  const CAT = [
    { n: 'Contraseñas inseguras', d: 'Se detectaron credenciales débiles o por defecto.', s: 7.5, r: 'Aplicar política de contraseñas robustas y activar MFA.' },
    { n: 'Software desactualizado', d: 'Versión con vulnerabilidades públicas conocidas.', s: 9.1, r: 'Actualizar el software a la última versión estable.' },
    { n: 'Configuración incorrecta', d: 'Servicio expuesto con una configuración insegura.', s: 5.3, r: 'Corregir la configuración siguiendo guías de hardening.' },
    { n: 'Puerto abierto innecesario', d: 'Puerto accesible desde internet sin necesidad.', s: 3.7, r: 'Cerrar el puerto o restringirlo con el firewall.' },
    { n: 'Falta de cifrado TLS', d: 'Comunicación en tránsito sin cifrar.', s: 6.8, r: 'Habilitar TLS 1.3 en el servicio.' },
    { n: 'Fallo de control de acceso', d: 'Recurso accesible sin autorización adecuada.', s: 8.2, r: 'Revisar roles y permisos del recurso.' }
  ];

  const esc = t => String(t).replace(/[&<>"']/g, c => ({ '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#39;' }[c]));
  const now = () => new Date().toLocaleString('es-CO');
  const sysName = id => (db.sys.find(s => s.id === id) || {}).nombre || '—';

  /* ---------- Datos (localStorage) ---------- */
  let db;
  db = load();
  function load() {
    try { const d = JSON.parse(localStorage.getItem(KEY)); if (d && d.sys) return d; } catch (e) {}
    return seed();
  }
  function save() { try { localStorage.setItem(KEY, JSON.stringify(db)); } catch (e) {} }
  function seed() {
    db = {
      sys: [
        { id: 1, nombre: 'Servidor Web Principal', ip: '192.168.1.10', desc: 'Servidor Apache de la intranet' },
        { id: 2, nombre: 'Base de datos MySQL', ip: '192.168.1.20', desc: 'Base de datos de clientes' }
      ],
      scans: [], vulns: [], n: { s: 3, a: 1, v: 1 }
    };
    addScan(1);
    return db;
  }
  function addScan(sysId) {
    const sc = { id: db.n.a++, sysId, fecha: now(), estado: 'completado', hallazgos: 0 };
    const picks = [...CAT].sort(() => Math.random() - .5).slice(0, 2 + Math.floor(Math.random() * 3));
    picks.forEach(c => db.vulns.push({
      id: db.n.v++, scanId: sc.id, sysId, nombre: c.n, desc: c.d, score: c.s, riesgo: riskOf(c.s), rec: c.r, fecha: sc.fecha
    }));
    sc.hallazgos = picks.length;
    db.scans.push(sc);
    return sc;
  }

  /* ---------- Utilidades UI ---------- */
  function toast(msg, err) {
    const t = document.createElement('div');
    t.className = 'toast' + (err ? ' err' : '');
    t.textContent = msg;
    $('#toasts').appendChild(t);
    setTimeout(() => t.remove(), 3200);
  }
  const badge = k => `<span class="badge ${k}">${RISK[k] || k}</span>`;

  /* ---------- Login con MFA (RF-01) ---------- */
  $('#form-login').addEventListener('submit', e => {
    e.preventDefault();
    const u = $('#l-user').value.trim().toLowerCase(), p = $('#l-pass').value.trim();
    const err = $('#login-error');
    if (!u || !p) return (err.textContent = 'Complete usuario y contraseña.');
    if (u !== USER || p !== PASS) return (err.textContent = 'Credenciales incorrectas.');
    err.textContent = '';
    $('#form-login').classList.add('hidden');
    $('#form-mfa').classList.remove('hidden');
    $('#l-code').focus();
  });
  $('#form-mfa').addEventListener('submit', e => {
    e.preventDefault();
    if ($('#l-code').value.trim() !== CODE) return ($('#login-error').textContent = 'Código de verificación inválido.');
    $('#login-error').textContent = '';
    $('#login').classList.add('hidden');
    $('#app').classList.remove('hidden');
    show('panel');
  });
  $('#btn-logout').addEventListener('click', () => {
    $('#app').classList.add('hidden');
    $('#login').classList.remove('hidden');
    $('#form-mfa').classList.add('hidden');
    $('#form-login').classList.remove('hidden');
    $('#form-login').reset(); $('#form-mfa').reset();
  });
  $('#btn-reset').addEventListener('click', () => {
    if (!confirm('¿Restablecer los datos de demostración?')) return;
    localStorage.removeItem(KEY); seed(); save(); show('panel'); toast('Datos restablecidos.');
  });

  /* ---------- Navegación ---------- */
  const RENDER = { panel: renderPanel, sistemas: renderSys, analisis: renderScan, vulns: renderVulns, reportes: renderReportSel };
  function show(v) {
    ['panel', 'sistemas', 'analisis', 'vulns', 'reportes'].forEach(n => $('#view-' + n).classList.toggle('hidden', n !== v));
    $$('nav button').forEach(b => b.classList.toggle('active', b.dataset.view === v));
    RENDER[v]();
  }
  $$('nav button').forEach(b => b.addEventListener('click', () => show(b.dataset.view)));

  /* ---------- Panel ---------- */
  function renderPanel() {
    const crit = db.vulns.filter(v => v.riesgo === 'critico').length;
    $('#kpis').innerHTML = [
      ['Sistemas monitoreados', db.sys.length, ''], ['Análisis realizados', db.scans.length, ''],
      ['Vulnerabilidades', db.vulns.length, ''], ['Críticas', crit, 'red']
    ].map(k => `<div class="kpi ${k[2]}"><b>${k[1]}</b><span>${k[0]}</span></div>`).join('');
    const total = db.vulns.length;
    $('#bars').innerHTML = total ? Object.keys(RISK).map(k => {
      const c = db.vulns.filter(v => v.riesgo === k).length;
      return `<div class="bar-row"><span>${RISK[k]}</span><div class="bar-track"><div class="bar-fill" style="width:${c / total * 100}%;background:var(--${k})"></div></div><b>${c}</b></div>`;
    }).join('') : '<p class="muted">Sin datos todavía. Ejecute un análisis.</p>';
  }

  // Eventos simulados "en vivo"
  const EVENTS = ['Intento de acceso fallido desde 10.0.0.', 'Escaneo de puertos detectado desde 172.16.4.', 'Nuevo log recibido del firewall', 'Servicio reiniciado correctamente', 'Actualización de reglas aplicada'];
  setInterval(() => {
    const f = $('#feed');
    if (!f || $('#view-panel').classList.contains('hidden')) return;
    const e = EVENTS[Math.floor(Math.random() * EVENTS.length)];
    const extra = e.endsWith('.') ? Math.floor(Math.random() * 250) : '';
    f.insertAdjacentHTML('afterbegin', `<li><time>${new Date().toLocaleTimeString('es-CO')}</time>${e}${extra}</li>`);
    while (f.children.length > 8) f.lastChild.remove();
  }, 3000);

  /* ---------- HU-01: Registro de sistemas ---------- */
  function renderSys() {
    $('#sys-list').innerHTML = db.sys.length ? `<table><thead><tr><th>ID</th><th>Nombre</th><th>IP</th><th>Descripción</th></tr></thead><tbody>${
      db.sys.map(s => `<tr><td>${s.id}</td><td>${esc(s.nombre)}</td><td>${esc(s.ip)}</td><td>${esc(s.desc || '—')}</td></tr>`).join('')}</tbody></table>`
      : '<p class="muted">No hay sistemas registrados.</p>';
  }
  const IPV4 = /^(25[0-5]|2[0-4]\d|1?\d?\d)(\.(25[0-5]|2[0-4]\d|1?\d?\d)){3}$/;
  $('#form-sys').addEventListener('submit', e => {
    e.preventDefault();
    const nombre = $('#s-nombre').value.trim(), ip = $('#s-ip').value.trim(), desc = $('#s-desc').value.trim();
    const err = $('#s-error');
    $('#s-nombre').classList.toggle('bad', !nombre);
    $('#s-ip').classList.toggle('bad', !ip);
    const faltan = [!nombre && 'Nombre del sistema', !ip && 'Dirección IP'].filter(Boolean);
    if (faltan.length) return (err.textContent = 'Debe completar: ' + faltan.join(', ') + '.');
    if (!IPV4.test(ip)) { $('#s-ip').classList.add('bad'); return (err.textContent = 'La dirección IP no es válida.'); }
    err.textContent = '';
    db.sys.push({ id: db.n.s++, nombre, ip, desc });
    save(); e.target.reset(); renderSys();
    toast('Sistema registrado correctamente.');
  });

  /* ---------- HU-02: Detección de vulnerabilidades ---------- */
  function renderScan() {
    const sel = $('#scan-sys'), prev = sel.value;
    sel.innerHTML = db.sys.map(s => `<option value="${s.id}">${esc(s.nombre)} (${esc(s.ip)})</option>`).join('');
    if (prev) sel.value = prev;
    $('#scan-list').innerHTML = db.scans.length ? `<table><thead><tr><th>ID</th><th>Sistema</th><th>Fecha</th><th>Estado</th><th>Hallazgos</th></tr></thead><tbody>${
      [...db.scans].reverse().map(a => `<tr><td>${a.id}</td><td>${esc(sysName(a.sysId))}</td><td>${a.fecha}</td><td>${badge(a.estado)}</td><td>${a.hallazgos}</td></tr>`).join('')}</tbody></table>`
      : '<p class="muted">Aún no hay análisis.</p>';
  }
  $('#btn-scan').addEventListener('click', () => {
    const sysId = parseInt($('#scan-sys').value, 10);
    const st = $('#scan-status'), bar = $('#scan-bar'), btn = $('#btn-scan');
    if (!sysId) return (st.textContent = 'Primero registre un sistema.');
    const fail = $('#scan-fail').checked;
    let p = 0; btn.disabled = true;
    const name = sysName(sysId);
    const timer = setInterval(() => {
      p += 10; bar.style.width = p + '%';
      st.textContent = `Analizando "${name}"… ${p}%`;
      if (fail && p === 60) {
        clearInterval(timer); btn.disabled = false;
        db.scans.push({ id: db.n.a++, sysId, fecha: now(), estado: 'fallido', hallazgos: 0 });
        save(); bar.style.width = '0';
        st.textContent = 'Error: el análisis no pudo completarse. Consulte el estado en el historial.';
        toast('El análisis falló.', true); renderScan();
      } else if (p >= 100) {
        clearInterval(timer); btn.disabled = false;
        const sc = addScan(sysId); save();
        st.textContent = `Análisis #${sc.id} finalizado: ${sc.hallazgos} vulnerabilidades guardadas.`;
        bar.style.width = '0'; toast('Análisis completado.'); renderScan();
      }
    }, 250);
  });

  /* ---------- HU-03 y HU-04: Consulta y clasificación ---------- */
  function renderVulns() {
    const f = $('#v-filter').value;
    const rows = db.vulns.filter(v => !f || v.riesgo === f).sort((a, b) => b.score - a.score);
    $('#v-list').innerHTML = rows.length ? `<table><thead><tr><th>Vulnerabilidad</th><th>Sistema</th><th>Riesgo</th></tr></thead><tbody>${
      rows.map(v => `<tr data-id="${v.id}"><td>${esc(v.nombre)}</td><td>${esc(sysName(v.sysId))}</td><td>${badge(v.riesgo)}</td></tr>`).join('')}</tbody></table>`
      : '<p class="muted">No hay resultados disponibles.</p>';
    $('#v-detail').innerHTML = '<p class="muted">Seleccione una vulnerabilidad para ver su detalle.</p>';
  }
  $('#v-filter').addEventListener('change', renderVulns);
  $('#v-list').addEventListener('click', e => {
    const tr = e.target.closest('tr[data-id]'); if (!tr) return;
    $$('#v-list tr').forEach(r => r.classList.remove('sel')); tr.classList.add('sel');
    const v = db.vulns.find(x => x.id === +tr.dataset.id);
    $('#v-detail').innerHTML = `<h3>${esc(v.nombre)} ${badge(v.riesgo)}</h3>
      <p>${esc(v.desc)}</p>
      <p><b>Sistema afectado:</b> ${esc(sysName(v.sysId))}<br><b>Fecha de detección:</b> ${v.fecha}</p>
      <p><b>Justificación del riesgo:</b> puntaje ${v.score} (rango ${RANGO[v.riesgo]}) → nivel ${RISK[v.riesgo]}.</p>
      <p><b>Recomendación:</b> ${esc(v.rec)}</p>`;
  });

  /* ---------- HU-05: Reportes ---------- */
  function renderReportSel() {
    const ok = db.scans.filter(a => a.estado === 'completado');
    $('#r-scan').innerHTML = ok.length ? ok.map(a => `<option value="${a.id}">#${a.id} · ${esc(sysName(a.sysId))} · ${a.fecha}</option>`).join('')
      : '<option value="">Sin análisis disponibles</option>';
    $('#report').classList.add('hidden');
  }
  $('#btn-report').addEventListener('click', () => {
    const box = $('#report'); box.classList.remove('hidden');
    const sc = db.scans.find(a => a.id === +$('#r-scan').value);
    const vs = sc ? db.vulns.filter(v => v.scanId === sc.id) : [];
    if (!sc || !vs.length) { box.innerHTML = '<p class="muted">No hay información suficiente para generar el reporte.</p>'; return; }
    vs.sort((a, b) => b.score - a.score);
    box.innerHTML = `<h3>Reporte de seguridad · Análisis #${sc.id}</h3>
      <p><b>Sistema:</b> ${esc(sysName(sc.sysId))}<br><b>Fecha:</b> ${sc.fecha}<br><b>Total de hallazgos:</b> ${vs.length}</p>
      <table><thead><tr><th>Vulnerabilidad</th><th>Puntaje</th><th>Riesgo</th><th>Recomendación</th></tr></thead><tbody>${
        vs.map(v => `<tr><td>${esc(v.nombre)}</td><td>${v.score}</td><td>${badge(v.riesgo)}</td><td>${esc(v.rec)}</td></tr>`).join('')}</tbody></table>
      <div class="report-actions"><button id="r-dl" class="btn primary">Descargar .txt</button><button id="r-pr" class="btn">Imprimir</button></div>`;
    $('#r-pr').onclick = () => window.print();
    $('#r-dl').onclick = () => {
      const txt = [`NEXUS RTM - REPORTE DE SEGURIDAD`, `Análisis #${sc.id} | ${sysName(sc.sysId)} | ${sc.fecha}`, '']
        .concat(vs.map(v => `[${RISK[v.riesgo].toUpperCase()}] ${v.nombre} (${v.score}) -> ${v.rec}`)).join('\n');
      const a = document.createElement('a');
      a.href = URL.createObjectURL(new Blob([txt], { type: 'text/plain' }));
      a.download = `reporte-analisis-${sc.id}.txt`; a.click(); URL.revokeObjectURL(a.href);
    };
  });
})();

</script>
</body>
</html>
