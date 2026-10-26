
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>17</title>
    
    <!-- CSS Bootstrap -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
    
    <style>
      /* Style Alert Melayang di Atas */
      .top-notification {
        position: sticky;
        top: 0;
        z-index: 1050;
        margin-bottom: 0;
        border-radius: 0;
        box-shadow: 0 4px 10px rgba(0,0,0,0.15);
      }

      /* Canvas Confetti agar menutupi seluruh background */
      #confetti-canvas {
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        z-index: -1;
        pointer-events: none;
      }

      /* Background Soft Birthday Gradient */
      body {
        background: linear-gradient(135deg, #ffe6f0 0%, #fff0f5 50%, #f0f8ff 100%);
        min-height: 100vh;
      }

      .carousel-img {
        height: 400px;
        object-fit: contain;
        object-position: center;
        background-color: #000;
      }

      /* Efek sorotan khusus untuk tombol Lihat Detail saat di-scroll */
      .highlight-btn {
        animation: pulse 1.5s infinite;
      }

      @keyframes pulse {
        0% { transform: scale(1); box-shadow: 0 0 0 0 rgba(13, 110, 253, 0.7); }
        70% { transform: scale(1.05); box-shadow: 0 0 0 10px rgba(13, 110, 253, 0); }
        100% { transform: scale(1); box-shadow: 0 0 0 0 rgba(13, 110, 253, 0); }
      }
    </style>
  </head>
  <body>

    <!-- Notification Alert di Paling Atas -->
    <div id="topAlert" class="alert alert-warning alert-dismissible fade show top-notification d-flex justify-content-between align-items-center px-3 py-2" role="alert">
      <div>
        <strong>🔔 Notifikasi:</strong> Mau lanjut baca? Klik <b>Yes</b> untuk gulir otomatis ke bawah dan tekan tombol <b>"Lihat Detail"</b>!
      </div>
      <div class="d-flex gap-2 ms-3">
        <button type="button" class="btn btn-sm btn-success fw-bold" onclick="scrollDownAndHighlight()">Yes</button>
        <button type="button" class="btn btn-sm btn-outline-danger fw-bold" data-bs-dismiss="alert" aria-label="Close">No</button>
      </div>
    </div>

    <!-- Canvas untuk Animasi Confetti -->
    <canvas id="confetti-canvas"></canvas>

    <!-- Header -->
    <h1 class="p-3 text-center fw-bold shadow-sm" style="background-color: #ffb6c1; color: #fff; text-shadow: 1px 1px 2px rgba(0,0,0,0.2);">
      Hi there, Celine!
    </h1>
    
    <div class="container my-4">
      
      <!-- Carousel Start -->
      <div id="carouselExample" class="carousel slide mb-5" data-bs-ride="carousel">
        <div class="carousel-inner rounded-3 shadow">

          <div class="carousel-item active">
            <img src="foto1.jpeg" class="d-block w-100 carousel-img" alt="Foto Pertama">
          </div>

          <div class="carousel-item">
            <img src="foto2.jpeg" class="d-block w-100 carousel-img" alt="Foto Kedua">
          </div>

          <div class="carousel-item">
            <img src="foto3.jpeg" class="d-block w-100 carousel-img" alt="Foto Ketiga">
          </div>

        </div>

        <button class="carousel-control-prev" type="button" data-bs-target="#carouselExample" data-bs-slide="prev">
          <span class="carousel-control-prev-icon" aria-hidden="true"></span>
          <span class="visually-hidden">Previous</span>
        </button>

        <button class="carousel-control-next" type="button" data-bs-target="#carouselExample" data-bs-slide="next">
          <span class="carousel-control-next-icon" aria-hidden="true"></span>
          <span class="visually-hidden">Next</span>
        </button>
      </div>
      <!-- Carousel End -->

      <!-- Section Card -->
      <div class="row g-4">
        
        <!-- Card Standard -->
        <div class="col-md-6">
          <div class="card h-100 shadow-sm border-0">
            <img src="foto1.jpeg" class="card-img-top" alt="Card Image" style="height: 200px; object-fit: cover;">
            <div class="card-body d-flex flex-column justify-content-between">
              <div>
                <h5 class="card-title fw-bold">Rahasia</h5>
                <p class="card-text text-muted">Click buttonnya celllllll</p>
              </div>
              <a href="page1.htm" id="targetBtn" class="btn btn-primary mt-3">Lihat Detail</a>
            </div>
          </div>
        </div>

        <!-- Card Placeholder -->
        <div class="col-md-6">
          <div class="card h-100 shadow-sm border-0" aria-hidden="true">
            <div class="bg-secondary opacity-25 rounded-top" style="height: 200px;"></div>
            <div class="card-body d-flex flex-column justify-content-between">
              <div>
                <h5 class="card-title placeholder-glow mb-3">
                  <span class="placeholder col-6"></span>
                </h5>
                <p class="card-text placeholder-glow">
                  <span class="placeholder col-7"></span>
                  <span class="placeholder col-4"></span>
                  <span class="placeholder col-4"></span>
                  <span class="placeholder col-6"></span>
                  <span class="placeholder col-8"></span>
                </p>
              </div>
              <a href="page1.htm" class="btn btn-primary disabled placeholder col-4 mt-3" aria-disabled="true"></a>
            </div>
          </div>
        </div>

      </div>

    </div>

    <!-- JS Bootstrap -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
    
    <!-- Library Animasi Confetti -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <!-- Script Utama -->
    <script>
      // Function untuk Scroll ke Bawah secara Halus & Meng-highlight Tombol
      function scrollDownAndHighlight() {
        const targetBtn = document.getElementById('targetBtn');
        
        // Scroll ke tombol "Lihat Detail"
        targetBtn.scrollIntoView({ behavior: 'smooth', block: 'center' });

        // Tambah animasi denial/pulse pada tombol
        targetBtn.classList.add('highlight-btn');
        
        // Hapus animasi setelah beberapa detik
        setTimeout(() => {
          targetBtn.classList.remove('highlight-btn');
        }, 4000);
      }

      // Animasi Confetti Latar Belakang
      const canvas = document.getElementById('confetti-canvas');
      const myConfetti = confetti.create(canvas, {
        resize: true,
        useWorker: true
      });

      function randomInRange(min, max) {
        return Math.random() * (max - min) + min;
      }

      setInterval(() => {
        myConfetti({
          particleCount: 3,
          angle: randomInRange(55, 125),
          spread: randomInRange(50, 70),
          origin: { y: 0 },
          colors: ['#ff69b4', '#ff1493', '#00bfff', '#ffd700', '#ff4500']
        });
      }, 250);
    </script>
  
