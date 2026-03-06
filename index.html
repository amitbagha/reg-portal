import { useState, useRef } from "react";

const defaultRecords = [
  { id: "01-106", name: "AMIT GHALE", purpose: "admission", added: "2026-03-06" },
  { id: "01-105", name: "SHAH AZIM", purpose: "admission", added: "2026-03-06" },
  { id: "01-102", name: "MOSAB H. M", purpose: "admission", added: "2026-03-06" },
  { id: "01-101", name: "HARPREET KAUR", purpose: "admission", added: "2026-03-05" },
  { id: "01-100", name: "MD DELOWAR HOSSAIN", purpose: "admission", added: "2026-03-05" },
  { id: "01-99", name: "MD MEHEDI HASAN", purpose: "admission", added: "2026-03-05" },
  { id: "01-98", name: "ALEX TURNER", purpose: "transcript", added: "2026-03-04" },
  { id: "01-97", name: "PRIYA SHARMA", purpose: "enrollment", added: "2026-03-04" },
  { id: "01-96", name: "JOHN BAPTISTE", purpose: "admission", added: "2026-03-03" },
  { id: "01-95", name: "FATIMA AL-RASHID", purpose: "transcript", added: "2026-03-03" },
  { id: "01-94", name: "CARLOS MENDEZ", purpose: "admission", added: "2026-03-02" },
  { id: "01-93", name: "YUN ZHANG", purpose: "enrollment", added: "2026-03-02" },
  { id: "01-92", name: "AMINATA DIALLO", purpose: "admission", added: "2026-03-01" },
  { id: "01-91", name: "ROHAN KAPOOR", purpose: "transcript", added: "2026-03-01" },
  { id: "01-90", name: "SARA JOHNSON", purpose: "admission", added: "2026-02-28" },
];

function formatDate(s) {
  const d = new Date(s);
  return `${d.getMonth()+1}/${d.getDate()}/${d.getFullYear()}`;
}

function getNextId(records) {
  if (!records.length) return "01-001";
  const max = Math.max(...records.map(r => parseInt(r.id.split("-").pop()) || 0));
  return `01-${String(max + 1).padStart(3, "0")}`;
}

function sortedRecs(arr, key, dir) {
  return [...arr].sort((a, b) => {
    let av = a[key], bv = b[key];
    if (key === "id") { av = parseInt(av.split("-").pop()); bv = parseInt(bv.split("-").pop()); }
    return av < bv ? (dir === "asc" ? -1 : 1) : av > bv ? (dir === "asc" ? 1 : -1) : 0;
  });
}

export default function App() {
  const [records, setRecords] = useState(defaultRecords);
  const [form, setForm] = useState({ id: "", name: "", purpose: "" });
  const [regError, setRegError] = useState("");
  const [search, setSearch] = useState("");
  const [selected, setSelected] = useState(new Set());
  const [sort, setSort] = useState({ key: "id", dir: "desc" });
  const [editingId, setEditingId] = useState(null);
  const [editForm, setEditForm] = useState({});
  const [toast, setToast] = useState(null);
  const [backupModal, setBackupModal] = useState(false);
  const [confirmDelete, setConfirmDelete] = useState(null);
  const fileRef = useRef();

  const showToast = (msg, type = "success") => {
    setToast({ msg, type });
    setTimeout(() => setToast(null), 3500);
  };

  const latestId = records.length
    ? records.reduce((a, b) => parseInt(a.id.split("-").pop()) > parseInt(b.id.split("-").pop()) ? a : b).id
    : "—";

  const filtered = sortedRecs(
    records.filter(r =>
      r.name.toLowerCase().includes(search.toLowerCase()) ||
      r.id.toLowerCase().includes(search.toLowerCase()) ||
      r.purpose.toLowerCase().includes(search.toLowerCase())
    ),
    sort.key, sort.dir
  );

  const handleRegIdChange = (val) => {
    setForm(f => ({ ...f, id: val }));
    if (val.trim() && records.find(r => r.id.toLowerCase() === val.trim().toLowerCase())) {
      setRegError("This Registration No. is already in use");
    } else {
      setRegError("");
    }
  };

  const handleAdd = () => {
    if (!form.id.trim() || !form.name.trim() || !form.purpose.trim()) {
      showToast("Please fill in all fields", "error"); return;
    }
    if (regError) { showToast(regError, "error"); return; }
    const newRec = {
      id: form.id.trim(),
      name: form.name.trim().toUpperCase(),
      purpose: form.purpose.trim().toLowerCase(),
      added: new Date().toISOString().split("T")[0],
    };
    setRecords(prev => [newRec, ...prev]);
    setForm({ id: "", name: "", purpose: "" });
    setRegError("");
    showToast(`Record ${newRec.id} added`);
  };

  const handleDelete = (id) => {
    setRecords(prev => prev.filter(r => r.id !== id));
    setSelected(prev => { const n = new Set(prev); n.delete(id); return n; });
    showToast(`Record ${id} deleted`);
    setConfirmDelete(null);
  };

  const handleBulkDelete = () => {
    const count = selected.size;
    setRecords(prev => prev.filter(r => !selected.has(r.id)));
    setSelected(new Set());
    showToast(`${count} records deleted`);
  };

  const handleEditSave = () => {
    const conflict = records.find(r => r.id.toLowerCase() === editForm.id.trim().toLowerCase() && r.id !== editingId);
    if (conflict) { showToast(`"${editForm.id.trim()}" already used by ${conflict.name}`, "error"); return; }
    setRecords(prev => prev.map(r => r.id === editingId ? { ...editForm, name: editForm.name.toUpperCase() } : r));
    setEditingId(null);
    showToast("Record updated");
  };

  const toggleSelect = (id) => setSelected(prev => { const n = new Set(prev); n.has(id) ? n.delete(id) : n.add(id); return n; });
  const toggleAll = () => setSelected(selected.size === filtered.length && filtered.length > 0 ? new Set() : new Set(filtered.map(r => r.id)));
  const handleSort = (key) => setSort(prev => ({ key, dir: prev.key === key && prev.dir === "asc" ? "desc" : "asc" }));

  const exportCSV = () => {
    const rows = ["REG. NO.,FULL NAME,PURPOSE,ADDED", ...records.map(r => `${r.id},"${r.name}",${r.purpose},${r.added}`)];
    const a = document.createElement("a");
    a.href = URL.createObjectURL(new Blob([rows.join("\n")], { type: "text/csv" }));
    a.download = "aiu-registry.csv"; a.click();
    showToast("CSV exported");
  };

  const exportJSON = () => {
    const a = document.createElement("a");
    a.href = URL.createObjectURL(new Blob([JSON.stringify(records, null, 2)], { type: "application/json" }));
    a.download = "aiu-registry.json"; a.click();
    showToast("JSON exported");
  };

  const exportBackup = () => {
    const backup = { version: "1.0", exportedAt: new Date().toISOString(), totalRecords: records.length, records };
    const a = document.createElement("a");
    a.href = URL.createObjectURL(new Blob([JSON.stringify(backup, null, 2)], { type: "application/json" }));
    a.download = `aiu-registry-backup-${new Date().toISOString().split("T")[0]}.json`;
    a.click();
    showToast("Backup downloaded");
    setBackupModal(false);
  };

  const handleRestore = async (e) => {
    const file = e.target.files[0];
    if (!file) return;
    try {
      const text = await file.text();
      if (!text.trim()) throw new Error("File is empty");
      let parsed;
      try { parsed = JSON.parse(text); } catch { throw new Error("Not valid JSON — please check the file"); }
      const recs = Array.isArray(parsed) ? parsed
        : Array.isArray(parsed.records) ? parsed.records
        : Array.isArray(parsed.data) ? parsed.data
        : null;
      if (!recs) throw new Error("No records array found in file");
      if (recs.length === 0) throw new Error("Backup file contains 0 records");
      const bad = recs.filter(r => !r.id || !r.name);
      if (bad.length) throw new Error(`${bad.length} record(s) missing required id or name`);
      const normalised = recs.map(r => ({
        id: String(r.id).trim(),
        name: String(r.name).trim().toUpperCase(),
        purpose: r.purpose ? String(r.purpose).trim().toLowerCase() : "admission",
        added: r.added || new Date().toISOString().split("T")[0],
      }));
      setRecords(normalised);
      setSelected(new Set());
      showToast(`Restored ${normalised.length} records`);
      setBackupModal(false);
    } catch (err) {
      showToast(err.message, "error");
    }
    e.target.value = "";
  };

  const SortArrow = ({ col }) => (
    <span style={{ marginLeft: 3, opacity: sort.key === col ? 1 : 0.25, fontSize: 9 }}>
      {sort.key === col && sort.dir === "asc" ? "▲" : "▼"}
    </span>
  );

  const thS = {
    padding: "11px 16px", textAlign: "left", fontSize: 11,
    fontWeight: 600, color: "#9ca3af", letterSpacing: "0.07em",
    cursor: "pointer", userSelect: "none", whiteSpace: "nowrap",
    borderBottom: "1px solid #f0f0f0",
  };

  return (
    <div style={{ minHeight: "100vh", background: "#f0f4ff", fontFamily: "'Segoe UI', system-ui, sans-serif" }}>
      <style>{`
        * { box-sizing: border-box; margin: 0; padding: 0; }
        @keyframes slideDown { from { transform: translateY(-8px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        .tr-h:hover { background: #f8faff !important; }
        .th-h:hover { background: #f1f5f9; }
        input:focus { outline: 2px solid #1a56db; outline-offset: -1px; border-color: transparent !important; }
      `}</style>

      {/* Toast */}
      {toast && (
        <div style={{
          position: "fixed", top: 18, right: 18, zIndex: 9999,
          background: toast.type === "error" ? "#fef2f2" : "#f0fdf4",
          border: `1px solid ${toast.type === "error" ? "#fca5a5" : "#86efac"}`,
          color: toast.type === "error" ? "#b91c1c" : "#15803d",
          padding: "11px 18px", borderRadius: 9, fontSize: 14, fontWeight: 500,
          animation: "slideDown 0.2s ease", boxShadow: "0 4px 16px rgba(0,0,0,0.12)", maxWidth: 340,
        }}>
          {toast.type === "error" ? "✗ " : "✓ "}{toast.msg}
        </div>
      )}

      {/* Confirm Delete Modal */}
      {confirmDelete && (
        <div onClick={() => setConfirmDelete(null)} style={{ position: "fixed", inset: 0, background: "rgba(0,0,0,0.35)", zIndex: 1000, display: "flex", alignItems: "center", justifyContent: "center", animation: "fadeIn 0.15s" }}>
          <div onClick={e => e.stopPropagation()} style={{ background: "#fff", borderRadius: 12, padding: 28, width: 360, boxShadow: "0 20px 60px rgba(0,0,0,0.2)" }}>
            <h3 style={{ fontSize: 16, fontWeight: 700, marginBottom: 8, color: "#111" }}>Delete Record?</h3>
            <p style={{ fontSize: 14, color: "#6b7280", marginBottom: 22 }}>
              <strong style={{ color: "#111" }}>{confirmDelete}</strong> will be permanently removed.
            </p>
            <div style={{ display: "flex", gap: 8, justifyContent: "flex-end" }}>
              <button onClick={() => setConfirmDelete(null)} style={{ padding: "8px 16px", borderRadius: 7, border: "1px solid #e5e7eb", background: "#fff", cursor: "pointer", fontSize: 14, fontFamily: "inherit" }}>Cancel</button>
              <button onClick={() => handleDelete(confirmDelete)} style={{ padding: "8px 16px", borderRadius: 7, border: "none", background: "#dc2626", color: "#fff", cursor: "pointer", fontSize: 14, fontWeight: 600, fontFamily: "inherit" }}>Delete</button>
            </div>
          </div>
        </div>
      )}

      {/* Backup Modal */}
      {backupModal && (
        <div onClick={() => setBackupModal(false)} style={{ position: "fixed", inset: 0, background: "rgba(0,0,0,0.35)", zIndex: 1000, display: "flex", alignItems: "center", justifyContent: "center", animation: "fadeIn 0.15s" }}>
          <div onClick={e => e.stopPropagation()} style={{ background: "#fff", borderRadius: 14, padding: 30, width: 440, boxShadow: "0 20px 60px rgba(0,0,0,0.2)" }}>
            <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 20 }}>
              <h3 style={{ fontSize: 17, fontWeight: 700, color: "#111" }}>💾 Database Backup</h3>
              <button onClick={() => setBackupModal(false)} style={{ background: "none", border: "none", cursor: "pointer", fontSize: 22, color: "#9ca3af", lineHeight: 1 }}>×</button>
            </div>
            <div style={{ display: "flex", flexDirection: "column", gap: 12 }}>
              <div style={{ background: "#eff6ff", border: "1px solid #bfdbfe", borderRadius: 10, padding: 16 }}>
                <div style={{ fontSize: 13, fontWeight: 600, color: "#1d4ed8", marginBottom: 4 }}>📤 Export Backup</div>
                <div style={{ fontSize: 13, color: "#6b7280", marginBottom: 12 }}>Download all {records.length} records as a JSON file.</div>
                <button onClick={exportBackup} style={{ width: "100%", padding: "9px", background: "#1a56db", color: "#fff", border: "none", borderRadius: 7, cursor: "pointer", fontSize: 14, fontWeight: 600, fontFamily: "inherit" }}>
                  ⬇ Download Backup (.json)
                </button>
              </div>
              <div style={{ background: "#fffbeb", border: "1px solid #fde68a", borderRadius: 10, padding: 16 }}>
                <div style={{ fontSize: 13, fontWeight: 600, color: "#b45309", marginBottom: 4 }}>📥 Restore Backup</div>
                <div style={{ fontSize: 13, color: "#6b7280", marginBottom: 12 }}>
                  Upload a backup JSON. Accepts bare array or <code style={{ background: "#f3f4f6", padding: "1px 5px", borderRadius: 4 }}>{`{records:[...]}`}</code> format.<br />
                  <strong style={{ color: "#92400e" }}>⚠ Replaces all current data.</strong>
                </div>
                <input type="file" accept=".json,application/json" ref={fileRef} onChange={handleRestore} style={{ display: "none" }} />
                <button onClick={() => fileRef.current.click()} style={{ width: "100%", padding: "9px", background: "#d97706", color: "#fff", border: "none", borderRadius: 7, cursor: "pointer", fontSize: 14, fontWeight: 600, fontFamily: "inherit" }}>
                  📂 Choose Backup File
                </button>
              </div>
              <div style={{ display: "flex", gap: 8 }}>
                <button onClick={exportCSV} style={{ flex: 1, padding: "8px", background: "#f3f4f6", border: "1px solid #e5e7eb", borderRadius: 7, cursor: "pointer", fontSize: 13, fontFamily: "inherit", color: "#374151" }}>⬇ Export CSV</button>
                <button onClick={exportJSON} style={{ flex: 1, padding: "8px", background: "#f3f4f6", border: "1px solid #e5e7eb", borderRadius: 7, cursor: "pointer", fontSize: 13, fontFamily: "inherit", color: "#374151" }}>⬇ Export JSON</button>
              </div>
            </div>
          </div>
        </div>
      )}

      {/* Header */}
      <div style={{ background: "#fff", borderBottom: "1px solid #e5e7eb" }}>
        <div style={{ maxWidth: 1100, margin: "0 auto", padding: "0 20px", display: "flex", alignItems: "center", justifyContent: "space-between", height: 58 }}>
          <div style={{ display: "flex", alignItems: "center", gap: 11 }}>
            <div style={{ width: 34, height: 34, background: "linear-gradient(135deg,#1a56db,#60a5fa)", borderRadius: 9, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 17 }}>📋</div>
            <div>
              <div style={{ fontWeight: 700, fontSize: 15, color: "#111" }}>AIU Student Registry</div>
              <div style={{ fontSize: 12, color: "#9ca3af" }}>{records.length} records</div>
            </div>
          </div>
          <div style={{ display: "flex", gap: 8 }}>
            <button onClick={() => setBackupModal(true)} style={{ padding: "7px 14px", border: "1px solid #d1d5db", borderRadius: 7, background: "#fff", cursor: "pointer", fontSize: 13, fontFamily: "inherit", fontWeight: 500, color: "#374151" }}>💾 Backup</button>
            <button onClick={exportCSV} style={{ padding: "7px 13px", border: "1px solid #d1d5db", borderRadius: 7, background: "#fff", cursor: "pointer", fontSize: 13, fontFamily: "inherit", color: "#374151" }}>⬇ CSV</button>
            <button onClick={exportJSON} style={{ padding: "7px 13px", border: "1px solid #d1d5db", borderRadius: 7, background: "#fff", cursor: "pointer", fontSize: 13, fontFamily: "inherit", color: "#374151" }}>⬇ JSON</button>
          </div>
        </div>
      </div>

      <div style={{ maxWidth: 1100, margin: "0 auto", padding: "22px 20px" }}>

        {/* Stats */}
        <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 14, marginBottom: 18 }}>
          <div style={{ background: "#fff", borderRadius: 12, padding: "18px 22px", border: "1px solid #e5e7eb", boxShadow: "0 1px 3px rgba(0,0,0,0.04)" }}>
            <div style={{ fontSize: 11, color: "#9ca3af", fontWeight: 600, letterSpacing: "0.07em", textTransform: "uppercase", marginBottom: 8 }}>TOTAL RECORDS</div>
            <div style={{ fontSize: 38, fontWeight: 700, color: "#111", letterSpacing: "-1px" }}>{records.length}</div>
          </div>
          <div style={{ background: "#fff", borderRadius: 12, padding: "18px 22px", border: "1px solid #e5e7eb", boxShadow: "0 1px 3px rgba(0,0,0,0.04)" }}>
            <div style={{ fontSize: 11, color: "#9ca3af", fontWeight: 600, letterSpacing: "0.07em", textTransform: "uppercase", marginBottom: 8 }}>LATEST REGISTRATION NO.</div>
            <div style={{ fontSize: 32, fontWeight: 700, color: "#1a56db", letterSpacing: "-0.5px", fontFamily: "monospace" }}>{latestId}</div>
          </div>
        </div>

        {/* Add Form */}
        <div style={{ background: "#fff", borderRadius: 12, padding: "20px 22px", border: "1px solid #e5e7eb", boxShadow: "0 1px 3px rgba(0,0,0,0.04)", marginBottom: 18 }}>
          <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 14 }}>
            <div style={{ fontWeight: 600, fontSize: 15, color: "#111" }}>Add New Record</div>
            <div style={{ fontSize: 13, color: "#9ca3af" }}>Last used: <span style={{ color: "#1a56db", fontFamily: "monospace", fontWeight: 600 }}>{latestId}</span></div>
          </div>
          <div style={{ display: "grid", gridTemplateColumns: "1fr 1.5fr 1.5fr auto", gap: 12, alignItems: "start" }}>
            <div>
              <div style={{ fontSize: 12, color: "#6b7280", marginBottom: 5, fontWeight: 500 }}>Registration No.</div>
              <input value={form.id} onChange={e => handleRegIdChange(e.target.value)} placeholder={`e.g. ${getNextId(records)}`} onKeyDown={e => e.key === "Enter" && handleAdd()}
                style={{ width: "100%", padding: "9px 11px", border: `1.5px solid ${regError ? "#f87171" : "#e5e7eb"}`, borderRadius: 8, fontSize: 14, fontFamily: "inherit", background: regError ? "#fff5f5" : "#fff", color: "#111" }} />
              {regError && <div style={{ fontSize: 11, color: "#dc2626", marginTop: 4 }}>⚠ {regError}</div>}
            </div>
            <div>
              <div style={{ fontSize: 12, color: "#6b7280", marginBottom: 5, fontWeight: 500 }}>Full Name</div>
              <input value={form.name} onChange={e => setForm(f => ({ ...f, name: e.target.value }))} placeholder="Student name" onKeyDown={e => e.key === "Enter" && handleAdd()}
                style={{ width: "100%", padding: "9px 11px", border: "1.5px solid #e5e7eb", borderRadius: 8, fontSize: 14, fontFamily: "inherit", color: "#111" }} />
            </div>
            <div>
              <div style={{ fontSize: 12, color: "#6b7280", marginBottom: 5, fontWeight: 500 }}>Purpose</div>
              <input value={form.purpose} onChange={e => setForm(f => ({ ...f, purpose: e.target.value }))} placeholder="e.g. B.Sc Computer Science" onKeyDown={e => e.key === "Enter" && handleAdd()}
                style={{ width: "100%", padding: "9px 11px", border: "1.5px solid #e5e7eb", borderRadius: 8, fontSize: 14, fontFamily: "inherit", color: "#111" }} />
            </div>
            <div style={{ paddingTop: 22 }}>
              <button onClick={handleAdd} disabled={!!regError}
                style={{ padding: "9px 22px", background: regError ? "#93c5fd" : "#1a56db", color: "#fff", border: "none", borderRadius: 8, cursor: regError ? "not-allowed" : "pointer", fontSize: 14, fontWeight: 600, fontFamily: "inherit", whiteSpace: "nowrap", height: 40, transition: "background 0.15s" }}>
                + Add
              </button>
            </div>
          </div>
        </div>

        {/* Table */}
        <div style={{ background: "#fff", borderRadius: 12, border: "1px solid #e5e7eb", boxShadow: "0 1px 3px rgba(0,0,0,0.04)", overflow: "hidden" }}>
          <div style={{ padding: "14px 18px", borderBottom: "1px solid #f3f4f6", display: "flex", gap: 10, alignItems: "center", flexWrap: "wrap" }}>
            <div style={{ position: "relative", flex: 1, minWidth: 180, maxWidth: 300 }}>
              <span style={{ position: "absolute", left: 10, top: "50%", transform: "translateY(-50%)", color: "#9ca3af", pointerEvents: "none" }}>🔍</span>
              <input value={search} onChange={e => setSearch(e.target.value)} placeholder="Search..."
                style={{ width: "100%", paddingLeft: 32, paddingRight: 10, paddingTop: 8, paddingBottom: 8, border: "1.5px solid #e5e7eb", borderRadius: 8, fontSize: 14, fontFamily: "inherit", color: "#111" }} />
            </div>
            {selected.size > 0 && (
              <button onClick={handleBulkDelete} style={{ padding: "8px 14px", background: "#fef2f2", color: "#dc2626", border: "1px solid #fca5a5", borderRadius: 8, cursor: "pointer", fontSize: 13, fontWeight: 500, fontFamily: "inherit" }}>
                🗑 Delete {selected.size} selected
              </button>
            )}
            {search && <span style={{ fontSize: 13, color: "#9ca3af" }}>{filtered.length} result{filtered.length !== 1 ? "s" : ""}</span>}
          </div>

          <div style={{ overflowX: "auto" }}>
            <table style={{ width: "100%", borderCollapse: "collapse" }}>
              <thead style={{ background: "#f9fafb" }}>
                <tr>
                  <th style={{ ...thS, width: 44, textAlign: "center", cursor: "default" }}>
                    <input type="checkbox" checked={selected.size === filtered.length && filtered.length > 0} onChange={toggleAll} style={{ cursor: "pointer" }} />
                  </th>
                  {[["id","REG. NO."],["name","FULL NAME"],["purpose","PURPOSE"],["added","ADDED"]].map(([k,l]) => (
                    <th key={k} className="th-h" onClick={() => handleSort(k)} style={thS}>{l}<SortArrow col={k} /></th>
                  ))}
                  <th style={{ ...thS, textAlign: "right", cursor: "default" }}>ACTIONS</th>
                </tr>
              </thead>
              <tbody>
                {filtered.length === 0 ? (
                  <tr><td colSpan={6} style={{ textAlign: "center", padding: "48px 16px", color: "#9ca3af", fontSize: 14 }}>
                    {search ? "No records match your search." : "No records yet — add one above!"}
                  </td></tr>
                ) : filtered.map(r => {
                  const isLatest = r.id === latestId;
                  const isEditing = editingId === r.id;
                  const inpStyle = (w) => ({ width: w || "100%", padding: "4px 8px", border: "1.5px solid #1a56db", borderRadius: 6, fontSize: 13, fontFamily: "inherit" });
                  return (
                    <tr key={r.id} className="tr-h" style={{ borderBottom: "1px solid #f3f4f6", background: selected.has(r.id) ? "#eff6ff" : "#fff", transition: "background 0.1s" }}>
                      <td style={{ padding: "12px 16px", textAlign: "center" }}>
                        <input type="checkbox" checked={selected.has(r.id)} onChange={() => toggleSelect(r.id)} style={{ cursor: "pointer" }} />
                      </td>
                      <td style={{ padding: "12px 16px" }}>
                        {isEditing
                          ? <input value={editForm.id} onChange={e => setEditForm(f => ({ ...f, id: e.target.value }))} style={inpStyle(90)} />
                          : <div style={{ display: "flex", alignItems: "center", gap: 7 }}>
                              <span style={{ color: "#1a56db", fontFamily: "monospace", fontSize: 13, fontWeight: 600 }}>{r.id}</span>
                              {isLatest && <span style={{ background: "#dcfce7", color: "#16a34a", fontSize: 10, fontWeight: 700, padding: "2px 7px", borderRadius: 20 }}>Latest</span>}
                            </div>
                        }
                      </td>
                      <td style={{ padding: "12px 16px", fontSize: 14, color: "#111", fontWeight: 500 }}>
                        {isEditing ? <input value={editForm.name} onChange={e => setEditForm(f => ({ ...f, name: e.target.value }))} style={inpStyle()} /> : r.name}
                      </td>
                      <td style={{ padding: "12px 16px", fontSize: 14, color: "#6b7280" }}>
                        {isEditing ? <input value={editForm.purpose} onChange={e => setEditForm(f => ({ ...f, purpose: e.target.value }))} style={inpStyle(130)} /> : r.purpose}
                      </td>
                      <td style={{ padding: "12px 16px", fontSize: 13, color: "#9ca3af", whiteSpace: "nowrap" }}>{formatDate(r.added)}</td>
                      <td style={{ padding: "12px 16px", textAlign: "right" }}>
                        {isEditing ? (
                          <div style={{ display: "flex", gap: 6, justifyContent: "flex-end" }}>
                            <button onClick={handleEditSave} style={{ padding: "5px 12px", background: "#1a56db", color: "#fff", border: "none", borderRadius: 6, cursor: "pointer", fontSize: 12, fontFamily: "inherit", fontWeight: 600 }}>Save</button>
                            <button onClick={() => setEditingId(null)} style={{ padding: "5px 10px", background: "#f3f4f6", border: "1px solid #e5e7eb", borderRadius: 6, cursor: "pointer", fontSize: 12, fontFamily: "inherit" }}>Cancel</button>
                          </div>
                        ) : (
                          <div style={{ display: "flex", gap: 6, justifyContent: "flex-end" }}>
                            <button onClick={() => { setEditingId(r.id); setEditForm({ ...r }); }} title="Edit"
                              style={{ background: "#f3f4f6", border: "1px solid #e5e7eb", borderRadius: 6, cursor: "pointer", width: 30, height: 30, fontSize: 14, display: "flex", alignItems: "center", justifyContent: "center" }}>✏️</button>
                            <button onClick={() => setConfirmDelete(r.id)} title="Delete"
                              style={{ background: "#fef2f2", border: "1px solid #fecaca", borderRadius: 6, cursor: "pointer", width: 30, height: 30, fontSize: 14, display: "flex", alignItems: "center", justifyContent: "center" }}>🗑️</button>
                          </div>
                        )}
                      </td>
                    </tr>
                  );
                })}
              </tbody>
            </table>
          </div>
          <div style={{ padding: "11px 18px", borderTop: "1px solid #f3f4f6", display: "flex", justifyContent: "space-between", alignItems: "center" }}>
            <span style={{ fontSize: 13, color: "#9ca3af" }}>Showing {filtered.length} of {records.length} records</span>
            <span style={{ fontSize: 12, color: "#10b981", fontWeight: 500 }}>● Session active</span>
          </div>
        </div>
      </div>
    </div>
  );
}
