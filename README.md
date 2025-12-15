
#  </div>[![.github/workflows/static.yml](https://github.com/kojaynahtul-hub/Project--slot--rpl/actions/workflows/static.yml/badge.svg?event=check_run)](https://github.com/kojaynahtul-hub/Project--slot--rpl/actions/workflows/static.yml)
  diff --git a/.github/workflows/static.yml b/.github/workflows/static.yml
new file mode 100644
index 0000000..e69de29
--- /dev/null
+++ b/.github/workflows/static.yml
@@ -0,0 +1,38
+# Simple workflow for deploying static content to Pages
+name: Deploy static content to Pages
+
+on:
+  push:
+    branches: ["master"]
+  workflow_dispatch:
+
+permissions:
+  contents: read
+  pages: write
+  id-token: write
+
+concurrency:
+  group: "pages"
+  cancel-in-progress: false
+
+jobs:
+  deploy:
+    runs-on: ubuntu-latest
+    environment:
+      name: github-pages
+      url: ${{ steps.deployment.outputs.page_url }}
+    steps:
+      - name: Checkout
+        uses: actions/checkout@v4
+
+      - name: Setup Pages
+        uses: actions/configure-pages@v5
+
+      - name: Upload artifact
+        uses: actions/upload-pages-artifact@v3
+        with:
+          path: '.'
+
+      - name: Deploy to GitHub Pages
+        id: deployment
+        uses: actions/deploy-pages@v4
diff --git a/README.md b/README.md
new file mode 100644
index 0000000..e69de29
--- /dev/null
+++ b/README.md
@@ -0,0 +1,32
+# Project--slot--rpl
+
+Sederhana: proyek mesin slot berbasis web.
+
+
+Cara cepat memperbaiki:
+1. Jika Anda punya file Word (.docx) asli, buka di Word/LibreOffice â†’ Export as HTML, lalu upload file HTML dan aset (gambar) ke repo.
+2. Jika Anda ingin restore file biner asli, unggah kembali file aslinya ke repo.
+
+Menjalankan lokal:
+- Python 3: `python -m http.server 8000`
+- Buka http://localhost:8000/slot_machine_project.html
+
+Setelah push:
+- Buka tab Actions â†’ cek workflow "Deploy static content to Pages".
+- Jika ada error, salin log dan kirim ke saya agar saya bantu diagnosis.
diff --git a/slot_machine_project.html b/slot_machine_project.html
new file mode 100644
index 0000000..e69de29
--- /dev/null
+++ b/slot_machine_project.html
@@ -0,0 +1,206
+<!doctype html>
+<html lang="id">
+<head>
+  <meta charset="utf-8" />
+  <meta name="viewport" content="width=device-width,initial-scale=1" />
+  <title>Slot Machine - Project--slot--rpl</title>
+  <style>
+    body { font-family: system-ui, Arial, sans-serif; background:#0b1020; color:#fff; display:flex; align-items:center; justify-content:center; min-height:100vh; margin:0; }
+    .container { width:520px; background:#0f1724; padding:18px; border-radius:10px; box-shadow:0 10px 30px rgba(0,0,0,.6); }
+    .display { display:flex; gap:12px; justify-content:center; margin:18px 0; }
+    .reel { width:120px; height:120px; background:#061022; border-radius:8px; display:flex; align-items:center; justify-content:center; font-size:48px; }
+    .controls { display:flex; justify-content:space-between; align-items:center; gap:10px; }
+    button { padding:10px 14px; border-radius:8px; border:0; cursor:pointer; background:#1f6feb; color:#fff; }
+    .info { font-size:14px; color:#cfe0ff; }
+    .small { font-size:13px; color:#9fb4e6; }
+  </style>
+</head>
+<body>
+  <div class="container" role="main">
+    <h2>Slot Machine (Real)</h2>
+    <div class="info">Credit: <span id="credits">400</span>  â€¢  Bet: <span id="bet">10</span></div>
+
+    <div class="display" aria-hidden="false">
+      <div class="reel" id="r1">ðŸ’</div>
+      <div class="reel" id="r2">ðŸ‹</div>
+      <div class="reel" id="r3">7ï¸âƒ£</div>
+    </div>
+
+    <div class="controls">
+      <div>
+        <button id="minus">- Bet</button>
+        <button id="plus">+ Bet</button>
+      </div>
+      <div>
+        <button id="spin">SPIN</button>
+      </div>
+      <div class="small">Win: <span id="win">0</span></div>
+    </div>
+
+    <p class="small" style="margin-top:12px">This is a minimal demo. Replace with your original HTML or export from .docx â†’ HTML if needed.</p>
+  </div>
+
+  <script>
+    const symbols = ['ðŸ’','ðŸ‹','ðŸŠ','ðŸ‰','â­','7ï¸âƒ£'];
+    const creditsEl = document.getElementById('credits');
+    const betEl = document.getElementById('bet');
+    const winEl = document.getElementById('win');
+    let credits = 400;
+    let bet = 10;
+
+    function rnd() { return symbols[Math.floor(Math.random()*symbols.length)]; }
+
+    function updateUI() {
+      creditsEl.textContent = credits;
+      betEl.textContent = bet;
+    }
+
+    document.getElementById('minus').addEventListener('click', () => {
+      if (bet > 1) bet -= 1;
+      updateUI();
+    });
+    document.getElementById('plus').addEventListener('click', () => {
+      if (bet < credits) bet += 1;
+      updateUI();
+    });
+
+    function spinOnce() {
+      if (bet > credits) { alert('Bet lebih besar dari credit'); return; }
+      credits -= bet;
+      updateUI();
+      const r1 = document.getElementById('r1');
+      const r2 = document.getElementById('r2');
+      const r3 = document.getElementById('r3');
+
+      let i=0;
+      const interval = setInterval(() => {
+        r1.textContent = rnd();
+        r2.textContent = rnd();
+        r3.textContent = rnd();
+        i++;
+        if (i>20) {
+          clearInterval(interval);
+          const s1 = rnd(), s2 = rnd(), s3 = rnd();
+          r1.textContent = s1; r2.textContent = s2; r3.textContent = s3;
+          let payout = 0;
+          if (s1 === s2 && s2 === s3) {
+            if (s1 === '7ï¸âƒ£') payout = bet * 10;
+            else payout = bet * 5;
+          } else if (s1 === s2 || s2 === s3 || s1 === s3) {
+            payout = bet * 2;
+          }
+          credits += payout;
+          winEl.textContent = payout;
+          updateUI();
+        }
+      }, 60);
+    }
+
+    document.getElementById('spin').addEventListener('click', spinOnce);
+    updateUI();
+  </script>
+</body>
+</html>
