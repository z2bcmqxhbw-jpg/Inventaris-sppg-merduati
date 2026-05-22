<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Inventaris SPPG Merduati</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'Inter',sans-serif;background:#f0f4ff;color:#1e293b;min-height:100vh}
:root{--hijau:#059669;--hijau2:#10b981;--merah:#dc2626;--merah2:#ef4444;--biru:#2563eb;--biru2:#3b82f6;--kuning:#d97706;--abu:#f8fafc;--abu2:#e2e8f0;--teks:#1e293b;--teks2:#64748b}

/* HEADER */
.hdr{background:linear-gradient(135deg,#0f172a 0%,#1e3a5f 50%,#1d4ed8 100%);color:white;padding:0;position:sticky;top:0;z-index:200;box-shadow:0 4px 20px rgba(0,0,0,0.3)}
.hdr-in{max-width:1100px;margin:0 auto;padding:16px 20px;display:flex;align-items:center;gap:14px}
.hdr-logo{width:44px;height:44px;background:rgba(255,255,255,0.12);border:1px solid rgba(255,255,255,0.2);border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0}
.hdr-title h1{font-size:15px;font-weight:800;letter-spacing:-0.3px}
.hdr-title p{font-size:10px;opacity:0.65;margin-top:1px;letter-spacing:0.5px}
.hdr-badge{margin-left:auto;background:rgba(255,255,255,0.1);border:1px solid rgba(255,255,255,0.2);border-radius:20px;padding:5px 12px;font-size:11px;font-weight:600;white-space:nowrap}
.hdr-sync{display:flex;align-items:center;gap:6px;background:rgba(16,185,129,0.2);border:1px solid rgba(16,185,129,0.4);border-radius:20px;padding:5px 12px;font-size:11px;font-weight:600;color:#6ee7b7;margin-left:8px;cursor:pointer;white-space:nowrap}
.hdr-sync.loading{background:rgba(245,158,11,0.2);border-color:rgba(245,158,11,0.4);color:#fcd34d}
.hdr-sync.error{background:rgba(239,68,68,0.2);border-color:rgba(239,68,68,0.4);color:#fca5a5}

/* MAIN */
.main{max-width:1100px;margin:0 auto;padding:24px 16px 80px}

/* STATS */
.stats{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-bottom:24px}
.stat{background:white;border-radius:16px;padding:18px 16px;box-shadow:0 1px 8px rgba(0,0,0,0.06);border-left:4px solid;display:flex;flex-direction:column;gap:4px}
.stat.s1{border-color:var(--hijau)}.stat.s2{border-color:var(--merah)}.stat.s3{border-color:var(--biru)}.stat.s4{border-color:var(--kuning)}
.stat-val{font-size:28px;font-weight:800;font-variant-numeric:tabular-nums;line-height:1}
.stat.s1 .stat-val{color:var(--hijau)}.stat.s2 .stat-val{color:var(--merah)}.stat.s3 .stat-val{color:var(--biru)}.stat.s4 .stat-val{color:var(--kuning)}
.stat-lbl{font-size:11px;color:var(--teks2);font-weight:600;text-transform:uppercase;letter-spacing:0.6px}

/* TABS */
.tabs{display:flex;background:white;border-radius:14px;padding:5px;gap:4px;box-shadow:0 1px 8px rgba(0,0,0,0.06);margin-bottom:20px}
.tb{flex:1;padding:11px 8px;border:none;background:transparent;border-radius:10px;font-family:'Inter',sans-serif;font-size:13px;font-weight:600;color:var(--teks2);cursor:pointer;transition:all 0.2s;display:flex;align-items:center;justify-content:center;gap:7px}
.tb.tm{background:var(--hijau);color:white;box-shadow:0 3px 10px rgba(5,150,105,0.3)}
.tb.tk{background:var(--merah);color:white;box-shadow:0 3px 10px rgba(220,38,38,0.3)}
.tb.tr{background:var(--biru);color:white;box-shadow:0 3px 10px rgba(37,99,235,0.3)}
.tb:hover:not(.tm):not(.tk):not(.tr){background:#f1f5f9}

/* PANEL */
.pnl{display:none}.pnl.on{display:block}

/* CARD */
.card{background:white;border-radius:18px;padding:24px;box-shadow:0 1px 8px rgba(0,0,0,0.06);margin-bottom:16px}
.ct{font-size:15px;font-weight:800;margin-bottom:20px;display:flex;align-items:center;gap:10px;padding-bottom:14px;border-bottom:2px solid #f1f5f9}
.ct span{width:5px;height:20px;border-radius:3px;flex-shrink:0}
.ct.h span{background:var(--hijau)}.ct.h{color:var(--hijau)}
.ct.m span{background:var(--merah)}.ct.m{color:var(--merah)}
.ct.b span{background:var(--biru)}.ct.b{color:var(--biru)}

/* FORM */
.fr{display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-bottom:14px}
.fr.f1{grid-template-columns:1fr}.fr.f3{grid-template-columns:1fr 1fr 1fr}
.fl{display:flex;flex-direction:column;gap:6px}
.fl label{font-size:11px;font-weight:700;color:var(--teks2);text-transform:uppercase;letter-spacing:0.5px}
.fl label .r{color:var(--merah)}
.fl input,.fl select,.fl textarea{padding:11px 14px;border:2px solid var(--abu2);border-radius:10px;font-family:'Inter',sans-serif;font-size:14px;color:var(--teks);background:#f8fafc;transition:all 0.2s;outline:none;width:100%}
.fl input:focus,.fl select:focus,.fl textarea:focus{border-color:var(--biru2);background:white;box-shadow:0 0 0 3px rgba(59,130,246,0.1)}
.fl textarea{resize:vertical;min-height:72px}

/* KONDISI */
.kg{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-bottom:14px}
.kb{padding:9px 6px;border:2px solid var(--abu2);border-radius:10px;background:white;font-family:'Inter',sans-serif;font-size:12px;font-weight:600;color:var(--teks2);cursor:pointer;text-align:center;transition:all 0.2s}
.kb.sb{border-color:var(--hijau);background:#ecfdf5;color:var(--hijau)}
.kb.sc{border-color:var(--biru2);background:#eff6ff;color:var(--biru2)}
.kb.sr{border-color:var(--kuning);background:#fffbeb;color:var(--kuning)}
.kb.sk{border-color:var(--merah);background:#fef2f2;color:var(--merah)}

/* DIVIDER */
.dv{display:flex;align-items:center;gap:10px;margin:16px 0;font-size:11px;font-weight:700;color:var(--teks2);text-transform:uppercase;letter-spacing:0.5px}
.dv::after{content:'';flex:1;height:1px;background:var(--abu2)}

/* BUTTONS */
.btn{padding:13px 20px;border:none;border-radius:11px;font-family:'Inter',sans-serif;font-size:14px;font-weight:700;cursor:pointer;transition:all 0.2s;display:flex;align-items:center;justify-content:center;gap:8px}
.btn:hover{transform:translateY(-1px)}
.btn:disabled{opacity:0.55;cursor:not-allowed;transform:none}
.btn-h{background:linear-gradient(135deg,var(--hijau),var(--hijau2));color:white;flex:1;box-shadow:0 3px 12px rgba(5,150,105,0.3)}
.btn-m{background:linear-gradient(135deg,var(--merah),var(--merah2));color:white;flex:1;box-shadow:0 3px 12px rgba(220,38,38,0.3)}
.btn-sec{background:#f1f5f9;color:var(--teks2);border:1px solid var(--abu2)}
.btn-sm{padding:7px 14px;font-size:12px;border-radius:8px;background:#f1f5f9;color:var(--teks2);border:1px solid var(--abu2)}

/* INFO BOX */
.ib{border-radius:10px;padding:11px 14px;font-size:13px;font-weight:600;margin-bottom:12px;display:none}
.ib.info{background:#eff6ff;border:1.5px solid #bfdbfe;color:#1e40af}
.ib.warn{background:#fef2f2;border:1.5px solid #fca5a5;color:#dc2626}

/* TABLE */
.tw{overflow-x:auto;border-radius:12px;border:2px solid var(--abu2);margin-top:10px}
.tbl{width:100%;border-collapse:collapse;font-size:13px}
.tbl th{padding:11px 13px;text-align:left;font-weight:700;font-size:10px;text-transform:uppercase;letter-spacing:0.5px;white-space:nowrap;color:white}
.th-h{background:var(--hijau)}.th-m{background:var(--merah)}.th-b{background:var(--biru)}
.tbl td{padding:11px 13px;border-bottom:1px solid #f1f5f9;vertical-align:middle}
.tbl tr:last-child td{border-bottom:none}
.tbl tr:hover td{background:#f8fafc}
.badge{display:inline-block;padding:3px 10px;border-radius:20px;font-size:11px;font-weight:700}
.bg-b{background:#ecfdf5;color:var(--hijau)}.bg-c{background:#eff6ff;color:var(--biru2)}
.bg-r{background:#fffbeb;color:var(--kuning)}.bg-k{background:#fef2f2;color:var(--merah)}

/* EMPTY */
.empty{text-align:center;padding:36px 20px;color:var(--teks2)}
.empty .ei{font-size:40px;margin-bottom:10px}

/* TOAST */
.toast{position:fixed;bottom:20px;right:20px;color:white;padding:13px 18px;border-radius:12px;font-size:13px;font-weight:600;box-shadow:0 8px 24px rgba(0,0,0,0.2);transform:translateY(60px);opacity:0;transition:all 0.3s;z-index:999;max-width:300px}
.toast.on{transform:translateY(0);opacity:1}
.t-ok{background:var(--hijau)}.t-err{background:var(--merah)}.t-ld{background:var(--kuning)}

/* STOK WARNING */
.stok-low{color:var(--merah);font-weight:800}

@media(max-width:640px){
  .stats{grid-template-columns:1fr 1fr}
  .fr{grid-template-columns:1fr}
  .fr.f3{grid-template-columns:1fr 1fr}
  .kg{grid-template-columns:1fr 1fr}
  .hdr-sync{display:none}
}
</style>
</head>
<body>

<div class="hdr">
  <div class="hdr-in">
    <div class="hdr-logo">📦</div>
    <div class="hdr-title">
      <h1>Sistem Inventaris Barang</h1>
      <p>SPPG MERDUATI · KUTA RAJA · BANDA ACEH</p>
    </div>
    <div class="hdr-sync loading" id="sync-btn" onclick="loadData()">
      <span id="sync-icon">⟳</span>
      <span id="sync-txt">Memuat...</span>
    </div>
    <div class="hdr-badge">📅 2026</div>
  </div>
</div>

<div class="main">

  <!-- STATS -->
  <div class="stats">
    <div class="stat s1"><div class="stat-val" id="st-masuk">0</div><div class="stat-lbl">📥 Total Masuk</div></div>
    <div class="stat s2"><div class="stat-val" id="st-keluar">0</div><div class="stat-lbl">📤 Total Keluar</div></div>
    <div class="stat s3"><div class="stat-val" id="st-stok">0</div><div class="stat-lbl">📦 Jenis Barang</div></div>
    <div class="stat s4"><div class="stat-val" id="st-transaksi">0</div><div class="stat-lbl">🔄 Transaksi</div></div>
  </div>

  <!-- TABS -->
  <div class="tabs">
    <button class="tb tm" onclick="goTab('masuk')" id="t-masuk">📥 Barang Masuk</button>
    <button class="tb" onclick="goTab('keluar')" id="t-keluar">📤 Barang Keluar</button>
    <button class="tb" onclick="goTab('rekap')" id="t-rekap">📊 Rekap & Stok</button>
  </div>

  <!-- PANEL MASUK -->
  <div class="pnl on" id="p-masuk">
    <div class="card">
      <div class="ct h"><span></span>Form Input Barang Masuk</div>
      <div class="fr">
        <div class="fl"><label>Nama Barang <span class="r">*</span></label><input type="text" id="m-nama" placeholder="cth: Beras, Minyak, ATK..."></div>
        <div class="fl"><label>Tanggal Masuk <span class="r">*</span></label><input type="date" id="m-tgl"></div>
      </div>
      <div class="fr f3">
        <div class="fl"><label>Jumlah <span class="r">*</span></label><input type="number" id="m-jml" min="1" placeholder="0"></div>
        <div class="fl">
          <label>Satuan <span class="r">*</span></label>
          <select id="m-sat">
            <option value="">-- Pilih --</option>
            <option>kg</option><option>gram</option><option>liter</option><option>ml</option>
            <option>pcs</option><option>dus</option><option>karung</option><option>botol</option>
            <option>kaleng</option><option>pak</option><option>lusin</option><option>unit</option><option>buah</option>
          </select>
        </div>
        <div class="fl"><label>Sumber / Pengirim</label><input type="text" id="m-src" placeholder="cth: Supplier A"></div>
      </div>
      <div class="dv"><span>Kondisi Barang</span></div>
      <div class="kg" id="kg-m">
        <button class="kb sb" onclick="setK('m','Baik',this)">✅ Baik</button>
        <button class="kb" onclick="setK('m','Cukup',this)">🔵 Cukup</button>
        <button class="kb" onclick="setK('m','Rusak',this)">⚠️ Rusak</button>
        <button class="kb" onclick="setK('m','Kritis',this)">🔴 Kritis</button>
      </div>
      <input type="hidden" id="m-knd" value="Baik">
      <div class="fr f1"><div class="fl"><label>Catatan</label><textarea id="m-cat" placeholder="Keterangan tambahan, nomor batch, dll..."></textarea></div></div>
      <div style="display:flex;gap:10px;margin-top:4px">
        <button class="btn btn-sec" onclick="reset('m')" style="width:100px">🔄 Reset</button>
        <button class="btn btn-h" id="b-masuk" onclick="submit('masuk')">📥 Simpan Barang Masuk</button>
      </div>
    </div>
  </div>

  <!-- PANEL KELUAR -->
  <div class="pnl" id="p-keluar">
    <div class="card">
      <div class="ct m"><span></span>Form Input Barang Keluar</div>
      <div class="fr">
        <div class="fl">
          <label>Pilih Barang <span class="r">*</span></label>
          <select id="k-nama" onchange="fillKeluar()">
            <option value="">-- Pilih Barang dari Stok --</option>
          </select>
        </div>
        <div class="fl"><label>Tanggal Keluar <span class="r">*</span></label><input type="date" id="k-tgl"></div>
      </div>
      <div class="ib info" id="k-info"></div>
      <div class="ib warn" id="k-warn">⚠️ Jumlah melebihi stok yang tersedia!</div>
      <div class="fr f3">
        <div class="fl"><label>Jumlah <span class="r">*</span></label><input type="number" id="k-jml" min="1" placeholder="0" oninput="cekStok()"></div>
        <div class="fl"><label>Satuan</label><input type="text" id="k-sat" readonly style="background:#f0f9ff;color:var(--biru);font-weight:600"></div>
        <div class="fl"><label>Tujuan / Penerima</label><input type="text" id="k-tuj" placeholder="cth: Dapur, Posyandu..."></div>
      </div>
      <div class="dv"><span>Kondisi Barang Saat Keluar</span></div>
      <div class="kg" id="kg-k">
        <button class="kb sb" onclick="setK('k','Baik',this)">✅ Baik</button>
        <button class="kb" onclick="setK('k','Cukup',this)">🔵 Cukup</button>
        <button class="kb" onclick="setK('k','Rusak',this)">⚠️ Rusak</button>
        <button class="kb" onclick="setK('k','Kritis',this)">🔴 Kritis</button>
      </div>
      <input type="hidden" id="k-knd" value="Baik">
      <div class="fr f1"><div class="fl"><label>Catatan</label><textarea id="k-cat" placeholder="Keterangan tambahan..."></textarea></div></div>
      <div style="display:flex;gap:10px;margin-top:4px">
        <button class="btn btn-sec" onclick="reset('k')" style="width:100px">🔄 Reset</button>
        <button class="btn btn-m" id="b-keluar" onclick="submit('keluar')">📤 Simpan Barang Keluar</button>
      </div>
    </div>
  </div>

  <!-- PANEL REKAP -->
  <div class="pnl" id="p-rekap">

    <!-- STOK -->
    <div class="card">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:14px;padding-bottom:14px;border-bottom:2px solid #f1f5f9">
        <div class="ct b" style="margin-bottom:0;padding-bottom:0;border:none"><span></span>Stok Barang Saat Ini</div>
        <div style="display:flex;gap:8px">
          <button class="btn btn-sm" onclick="loadData()">🔄 Refresh</button>
          <button class="btn btn-sm" onclick="csv('stok')">📥 CSV</button>
        </div>
      </div>
      <div class="tw">
        <table class="tbl"><thead><tr>
          <th class="th-b">No</th><th class="th-b">Nama Barang</th><th class="th-b">Satuan</th>
          <th class="th-b">Stok</th><th class="th-b">Total Masuk</th><th class="th-b">Total Keluar</th>
        </tr></thead><tbody id="tb-stok">
          <tr><td colspan="6"><div class="empty"><div class="ei">📦</div><p>Memuat data...</p></div></td></tr>
        </tbody></table>
      </div>
    </div>

    <!-- RIWAYAT MASUK -->
    <div class="card">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:14px;padding-bottom:14px;border-bottom:2px solid #f1f5f9">
        <div class="ct h" style="margin-bottom:0;padding-bottom:0;border:none"><span></span>Riwayat Barang Masuk</div>
        <button class="btn btn-sm" onclick="csv('masuk')">📥 CSV</button>
      </div>
      <div class="tw">
        <table class="tbl"><thead><tr>
          <th class="th-h">No</th><th class="th-h">Timestamp</th><th class="th-h">Nama Barang</th>
          <th class="th-h">Jumlah</th><th class="th-h">Satuan</th><th class="th-h">Kondisi</th>
          <th class="th-h">Sumber</th><th class="th-h">Catatan</th>
        </tr></thead><tbody id="tb-masuk">
          <tr><td colspan="8"><div class="empty"><div class="ei">📥</div><p>Memuat data...</p></div></td></tr>
        </tbody></table>
      </div>
    </div>

    <!-- RIWAYAT KELUAR -->
    <div class="card">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:14px;padding-bottom:14px;border-bottom:2px solid #f1f5f9">
        <div class="ct m" style="margin-bottom:0;padding-bottom:0;border:none"><span></span>Riwayat Barang Keluar</div>
        <button class="btn btn-sm" onclick="csv('keluar')">📥 CSV</button>
      </div>
      <div class="tw">
        <table class="tbl"><thead><tr>
          <th class="th-m">No</th><th class="th-m">Timestamp</th><th class="th-m">Nama Barang</th>
          <th class="th-m">Jumlah</th><th class="th-m">Satuan</th><th class="th-m">Kondisi</th>
          <th class="th-m">Tujuan</th><th class="th-m">Catatan</th>
        </tr></thead><tbody id="tb-keluar">
          <tr><td colspan="8"><div class="empty"><div class="ei">📤</div><p>Memuat data...</p></div></td></tr>
        </tbody></table>
      </div>
    </div>
  </div>

</div>
<div class="toast" id="toast"></div>

<script>
const URL = "https://script.google.com/macros/s/AKfycbyGj5HNuOoz2CMSRrNrlY6DusAYSiSyhuymk7U_JE6_KCwCfDaRoD3K80rKqHrp4rzJTA/exec";

let D = { stok:{}, masuk:[], keluar:[] };

// INIT
window.onload = () => {
  const t = new Date().toISOString().split('T')[0];
  document.getElementById('m-tgl').value = t;
  document.getElementById('k-tgl').value = t;
  loadData();
};

// LOAD DATA DARI SHEETS
async function loadData() {
  setSyncBar('loading','⟳','Memuat...');
  try {
    const res = await fetch(URL, {
      method:'POST',
      body: JSON.stringify({tipe:'getAll'}),
      headers:{'Content-Type':'text/plain'}
    });
    const json = await res.json();
    if (json.status === 'ok') {
      D.stok = {};
      json.stok.forEach(s => D.stok[s.nama] = {satuan:s.satuan, stok:Number(s.stok), masuk:Number(s.masuk), keluar:Number(s.keluar)});
      D.masuk = json.masuk;
      D.keluar = json.keluar;
      updateStats();
      updateDropdown();
      setSyncBar('ok','✓','Tersinkron');
    }
  } catch(e) {
    setSyncBar('error','✗','Gagal sync');
    showToast('Gagal memuat data. Cek koneksi internet.','t-err');
  }
}

function setSyncBar(state, icon, txt) {
  const el = document.getElementById('sync-btn');
  document.getElementById('sync-icon').textContent = icon;
  document.getElementById('sync-txt').textContent = txt;
  el.className = 'hdr-sync' + (state==='loading'?' loading':state==='error'?' error':'');
}

// TABS
function goTab(tab) {
  ['masuk','keluar','rekap'].forEach(t => {
    document.getElementById('p-'+t).classList.remove('on');
    document.getElementById('t-'+t).className = 'tb';
  });
  document.getElementById('p-'+tab).classList.add('on');
  const cls = tab==='masuk'?'tm':tab==='keluar'?'tk':'tr';
  document.getElementById('t-'+tab).className = 'tb '+cls;
  if (tab==='rekap') renderRekap();
}

// KONDISI
function setK(p, val, el) {
  const map = {Baik:'sb',Cukup:'sc',Rusak:'sr',Kritis:'sk'};
  el.closest('.kg').querySelectorAll('.kb').forEach(b => b.className = 'kb');
  el.className = 'kb ' + map[val];
  document.getElementById(p+'-knd').value = val;
}

// FILL KELUAR
function fillKeluar() {
  const nama = document.getElementById('k-nama').value;
  const info = document.getElementById('k-info');
  if (nama && D.stok[nama]) {
    const s = D.stok[nama];
    document.getElementById('k-sat').value = s.satuan;
    info.style.display = 'block';
    info.textContent = '📦 Stok tersedia: ' + s.stok + ' ' + s.satuan;
    info.className = 'ib info';
  } else {
    info.style.display = 'none';
    document.getElementById('k-sat').value = '';
  }
  document.getElementById('k-warn').style.display = 'none';
}

function cekStok() {
  const nama = document.getElementById('k-nama').value;
  const jml = +document.getElementById('k-jml').value || 0;
  const warn = document.getElementById('k-warn');
  if (nama && D.stok[nama]) {
    warn.style.display = jml > D.stok[nama].stok ? 'block' : 'none';
  }
}

function updateDropdown() {
  const sel = document.getElementById('k-nama');
  const cur = sel.value;
  sel.innerHTML = '<option value="">-- Pilih Barang dari Stok --</option>';
  Object.entries(D.stok).forEach(([n,s]) => {
    const o = document.createElement('option');
    o.value = n;
    o.textContent = n + ' — Stok: ' + s.stok + ' ' + s.satuan;
    if (s.stok <= 0) o.textContent += ' ⚠️';
    sel.appendChild(o);
  });
  if (cur) sel.value = cur;
}

function updateStats() {
  const tm = Object.values(D.stok).reduce((a,b)=>a+b.masuk,0);
  const tk = Object.values(D.stok).reduce((a,b)=>a+b.keluar,0);
  document.getElementById('st-masuk').textContent = tm;
  document.getElementById('st-keluar').textContent = tk;
  document.getElementById('st-stok').textContent = Object.keys(D.stok).length;
  document.getElementById('st-transaksi').textContent = D.masuk.length + D.keluar.length;
}

// SUBMIT
async function submit(tipe) {
  const iM = tipe==='masuk';
  const p = iM?'m':'k';
  const nama = iM ? document.getElementById('m-nama').value.trim() : document.getElementById('k-nama').value;
  const jml = +(document.getElementById(p+'-jml').value)||0;
  const sat = document.getElementById(p+'-sat').value;
  const tgl = document.getElementById(p+'-tgl').value;
  const knd = document.getElementById(p+'-knd').value;
  const cat = document.getElementById(p+'-cat').value;
  const ext = iM ? document.getElementById('m-src').value : document.getElementById('k-tuj').value;

  if (!nama) { showToast('⚠️ Pilih/isi nama barang!','t-err'); return; }
  if (!jml||jml<=0) { showToast('⚠️ Isi jumlah barang!','t-err'); return; }
  if (!sat) { showToast('⚠️ Pilih satuan!','t-err'); return; }
  if (!iM && D.stok[nama] && jml > D.stok[nama].stok) { showToast('⚠️ Stok tidak mencukupi!','t-err'); return; }

  const btn = document.getElementById('b-'+(iM?'masuk':'keluar'));
  btn.disabled = true; btn.textContent = '⏳ Menyimpan...';
  showToast('⏳ Menyimpan ke Google Sheets...','t-ld');

  const payload = {tipe, nama, jumlah:jml, satuan:sat, kondisi:knd, catatan:cat};
  if (iM) payload.sumber = ext; else payload.tujuan = ext;

  // Update lokal langsung
  if (!D.stok[nama]) D.stok[nama] = {satuan:sat, stok:0, masuk:0, keluar:0};
  if (iM) {
    D.stok[nama].stok += jml;
    D.stok[nama].masuk += jml;
    D.masuk.push({ts:new Date().toLocaleString('id-ID'), nama, jumlah:jml, satuan:sat, kondisi:knd, sumber:ext, catatan:cat});
  } else {
    D.stok[nama].stok -= jml;
    D.stok[nama].keluar += jml;
    D.keluar.push({ts:new Date().toLocaleString('id-ID'), nama, jumlah:jml, satuan:sat, kondisi:knd, tujuan:ext, catatan:cat});
  }
  updateStats();
  updateDropdown();

  // Kirim ke Sheets
  try {
    await fetch(URL, {
      method:'POST',
      body: JSON.stringify(payload),
      headers:{'Content-Type':'text/plain'}
    });
    showToast(iM?'✅ Barang masuk tersimpan!':'✅ Barang keluar tersimpan!','t-ok');
    setSyncBar('ok','✓','Tersinkron');
  } catch(e) {
    showToast('⚠️ Tersimpan lokal. Sync gagal.','t-err');
    setSyncBar('error','✗','Gagal sync');
  }

  btn.disabled = false;
  btn.innerHTML = iM ? '📥 Simpan Barang Masuk' : '📤 Simpan Barang Keluar';
  reset(p);
}

function reset(p) {
  if (p==='m') {
    ['m-nama','m-jml','m-src','m-cat'].forEach(id=>document.getElementById(id).value='');
    document.getElementById('m-sat').value='';
    document.getElementById('m-knd').value='Baik';
    document.querySelectorAll('#kg-m .kb').forEach((b,i)=>b.className='kb'+(i===0?' sb':''));
  } else {
    ['k-nama','k-jml','k-tuj','k-cat'].forEach(id=>document.getElementById(id).value='');
    document.getElementById('k-sat').value='';
    document.getElementById('k-knd').value='Baik';
    document.getElementById('k-info').style.display='none';
    document.getElementById('k-warn').style.display='none';
    document.querySelectorAll('#kg-k .kb').forEach((b,i)=>b.className='kb'+(i===0?' sb':''));
  }
}

// RENDER REKAP
function renderRekap() {
  // Stok
  const tbs = document.getElementById('tb-stok');
  const arr = Object.entries(D.stok);
  tbs.innerHTML = arr.length===0
    ? '<tr><td colspan="6"><div class="empty"><div class="ei">📦</div><p>Belum ada data stok.</p></div></td></tr>'
    : arr.map(([n,s],i)=>`<tr>
        <td>${i+1}</td><td><strong>${n}</strong></td><td>${s.satuan}</td>
        <td class="${s.stok<=0?'stok-low':''}" style="font-weight:700">${s.stok}${s.stok<=0?' ⚠️':''}</td>
        <td style="color:var(--hijau);font-weight:600">${s.masuk}</td>
        <td style="color:var(--merah);font-weight:600">${s.keluar}</td>
      </tr>`).join('');

  // Masuk
  const tbm = document.getElementById('tb-masuk');
  tbm.innerHTML = D.masuk.length===0
    ? '<tr><td colspan="8"><div class="empty"><div class="ei">📥</div><p>Belum ada data.</p></div></td></tr>'
    : [...D.masuk].reverse().map((d,i)=>`<tr>
        <td>${D.masuk.length-i}</td>
        <td style="font-size:11px;white-space:nowrap">${d.ts||d.timestamp||'-'}</td>
        <td><strong>${d.nama}</strong></td>
        <td><strong>${d.jumlah}</strong></td><td>${d.satuan}</td>
        <td><span class="badge bg-${(d.kondisi||'').toLowerCase().charAt(0)}">${d.kondisi||'-'}</span></td>
        <td style="font-size:12px">${d.sumber||'-'}</td>
        <td style="font-size:12px">${d.catatan||'-'}</td>
      </tr>`).join('');

  // Keluar
  const tbk = document.getElementById('tb-keluar');
  tbk.innerHTML = D.keluar.length===0
    ? '<tr><td colspan="8"><div class="empty"><div class="ei">📤</div><p>Belum ada data.</p></div></td></tr>'
    : [...D.keluar].reverse().map((d,i)=>`<tr>
        <td>${D.keluar.length-i}</td>
        <td style="font-size:11px;white-space:nowrap">${d.ts||d.timestamp||'-'}</td>
        <td><strong>${d.nama}</strong></td>
        <td><strong>${d.jumlah}</strong></td><td>${d.satuan}</td>
        <td><span class="badge bg-${(d.kondisi||'').toLowerCase().charAt(0)}">${d.kondisi||'-'}</span></td>
        <td style="font-size:12px">${d.tujuan||'-'}</td>
        <td style="font-size:12px">${d.catatan||'-'}</td>
      </tr>`).join('');
}

// CSV EXPORT
function csv(tipe) {
  let c='',fn='';
  if (tipe==='stok') {
    c='Nama Barang,Satuan,Stok,Total Masuk,Total Keluar\n';
    Object.entries(D.stok).forEach(([n,s])=>c+=`"${n}",${s.satuan},${s.stok},${s.masuk},${s.keluar}\n`);
    fn='Stok_Barang.csv';
  } else if (tipe==='masuk') {
    c='No,Timestamp,Nama Barang,Jumlah,Satuan,Kondisi,Sumber,Catatan\n';
    D.masuk.forEach((d,i)=>c+=`${i+1},"${d.ts||d.timestamp||''}","${d.nama}",${d.jumlah},${d.satuan},"${d.kondisi||''}","${d.sumber||''}","${d.catatan||''}"\n`);
    fn='Barang_Masuk.csv';
  } else {
    c='No,Timestamp,Nama Barang,Jumlah,Satuan,Kondisi,Tujuan,Catatan\n';
    D.keluar.forEach((d,i)=>c+=`${i+1},"${d.ts||d.timestamp||''}","${d.nama}",${d.jumlah},${d.satuan},"${d.kondisi||''}","${d.tujuan||''}","${d.catatan||''}"\n`);
    fn='Barang_Keluar.csv';
  }
  if (!c.split('\n')[1]) { showToast('Belum ada data!','t-err'); return; }
  const a=document.createElement('a');
  a.href=URL.createObjectURL(new Blob(['\uFEFF'+c],{type:'text/csv;charset=utf-8;'}));
  a.download=fn; a.click();
}

// TOAST
function showToast(msg, cls='t-ok') {
  const t=document.getElementById('toast');
  t.textContent=msg; t.className='toast on '+cls;
  if (cls!=='t-ld') setTimeout(()=>t.className='toast',3500);
}
</script>
</body>
</html>
