# Shivamani-Photography
<!doctype html>
<html lang="te">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Sam Photography</title>
  <meta name="description" content="Sam Photography — Portfolio">
  <link href="https://fonts.googleapis.com/css2?family=Work+Sans:wght@300;500;700&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg:#0f1720; --card:#0b1220; --muted:#9aa4b2;
    }
    *{box-sizing:border-box}
    body{
      margin:0;font-family:'Work Sans',system-ui,-apple-system,Segoe UI,Roboto,Arial;
      background:linear-gradient(180deg,var(--bg),#071019);color:#fff;
      -webkit-font-smoothing:antialiased;
    }
    header{padding:36px 20px;text-align:center}
    header h1{margin:0;font-size:clamp(20px,4vw,34px);letter-spacing:0.6px}
    header p{margin:8px 0 0;color:var(--muted)}
    .wrap{max-width:1100px;margin:28px auto;padding:0 18px}
    .controls{display:flex;gap:10px;justify-content:center;margin-bottom:16px}
    .btn{background:#0e1530;border:1px solid rgba(255,255,255,0.04);padding:8px 12px;border-radius:8px;font-weight:500;cursor:pointer;color:#dce6f2}
    .gallery{
      display:grid;
      grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
      gap:12px;
    }
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01)); padding:6px; border-radius:10px;}
    .card img{width:100%;height:220px;object-fit:cover;border-radius:8px;display:block;cursor:pointer;transition:transform .25s}
    .card img:hover{transform:scale(1.03)}
    footer{padding:22px 0;text-align:center;color:var(--muted);font-size:13px;margin-top:30px}
    /* Modal */
    .overlay{position:fixed;inset:0;background:rgba(2,6,23,0.8);display:none;align-items:center;justify-content:center;padding:20px;z-index:50}
    .overlay.open{display:flex}
    .overlay .box{max-width:1100px;width:100%;border-radius:10px;overflow:hidden}
    .overlay img{width:100%;height:auto;display:block}
    .caption{padding:12px;background:linear-gradient(180deg, rgba(0,0,0,0.2), rgba(0,0,0,0.4));color:#e6eef8;font-size:15px}
    .closeBtn{position:fixed;top:18px;right:18px;background:#071428;border:0;padding:8px 10px;border-radius:8px;color:#dce6f2;cursor:pointer}
    @media (max-width:480px){ .card img{height:160px} .caption{font-size:14px} }
  </style>
</head>
<body>
  <header>
    <h1>Sam Photography</h1>
    <p>Moments — Captured & Shared</p>
  </header>

  <main class="wrap">
    <div class="controls">
      <button class="btn" onclick="filter('all')">All</button>
      <button class="btn" onclick="filter('nature')">Nature</button>
      <button class="btn" onclick="filter('portrait')">Portrait</button>
      <button class="btn" onclick="filter('street')">Street</button>
    </div>

    <section class="gallery" id="gallery">
      <!-- Replace these sample images with your own (upload to repo / use your URLs) -->
      <figure class="card" data-cat="nature">
        <img src="images/photo1.jpg" alt="Sunset at Beach" onclick="openModal(this)">
        <figcaption style="display:none">Sunset at Beach</figcaption>
      </figure>

      <figure class="card" data-cat="portrait">
        <img src="images/photo2.jpg" alt="Portrait — Maya" onclick="openModal(this)">
        <figcaption style="display:none">Portrait — Maya</figcaption>
      </figure>

      <figure class="card" data-cat="street">
        <img src="images/photo3.jpg" alt="City Street" onclick="openModal(this)">
        <figcaption style="display:none">City Street</figcaption>
      </figure>

      <figure class="card" data-cat="nature">
        <img src="images/photo4.jpg" alt="Mountain View" onclick="openModal(this)">
        <figcaption style="display:none">Mountain View</figcaption>
      </figure>

      <!-- add more figures as needed -->
    </section>
  </main>

  <footer>© <span id="yr"></span> Sam Photography — Built with ❤️</footer>

  <!-- Modal overlay -->
  <div id="overlay" class="overlay" onclick="closeModal(event)">
    <button class="closeBtn" onclick="closeModal(event)">Close ✕</button>
    <div class="box" onclick="event.stopPropagation()">
      <img id="modalImg" src="" alt="">
      <div class="caption" id="modalCaption"></div>
    </div>
  </div>

  <script>
    document.getElementById('yr').textContent = new Date().getFullYear();

    function openModal(imgEl){
      const overlay = document.getElementById('overlay');
      const modalImg = document.getElementById('modalImg');
      const modalCaption = document.getElementById('modalCaption');
      modalImg.src = imgEl.src;
      modalImg.alt = imgEl.alt || '';
      modalCaption.textContent = imgEl.alt || '';
      overlay.classList.add('open');
    }
    function closeModal(e){
      if(e) e.stopPropagation();
      document.getElementById('overlay').classList.remove('open');
      document.getElementById('modalImg').src = '';
    }
    function filter(cat){
      const items = document.querySelectorAll('#gallery .card');
      items.forEach(it => {
        if(cat === 'all' || it.dataset.cat === cat) it.style.display = '';
        else it.style.display = 'none';
      });
    }
  </script>
</body>
</html>
