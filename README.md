<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sieerre - Japanese Resto & Creative Crochet</title>
    <!-- Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600&family=Quicksand:wght@300;400;500;700&family=Playfair+Display:ital,wght@0,700;1,700&display=swap" rel="stylesheet">
    <!-- Icons -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/lucide-react/0.263.1/lucide-react.min.js"></script>
    <style>
        :root {
            --lavender: #9b8ec4;
            --soft-purple: #7c6daa;
            --bg-light: #F5F3FF;
            --text-dark: #4a4a4a;
            --accent-warm: #d4a373;
            --transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            --font-handwritten: 'Dancing Script', cursive;
            --font-main: 'Quicksand', sans-serif;
            --font-heading: 'Playfair Display', serif;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: var(--font-main);
            background-color: var(--bg-light);
            color: var(--text-dark);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Utils */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .section-padding {
            padding: 80px 0;
        }

        .btn {
            padding: 12px 28px;
            border-radius: 50px;
            border: none;
            cursor: pointer;
            font-family: var(--font-main);
            font-weight: 600;
            transition: var(--transition);
            text-decoration: none;
            display: inline-block;
        }

        .btn-primary {
            background-color: var(--soft-purple);
            color: white;
        }

        .btn-primary:hover {
            background-color: var(--lavender);
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(124, 109, 170, 0.2);
        }

        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: var(--transition);
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Navigation */
        nav {
            background: white;
            padding: 20px 0;
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 15px rgba(0,0,0,0.05);
        }

        .nav-content {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .logo {
            font-family: var(--font-handwritten);
            font-size: 3rem;
            color: var(--soft-purple);
            margin-bottom: 15px;
            text-decoration: none;
        }

        .nav-links {
            display: flex;
            gap: 30px;
            list-style: none;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-dark);
            font-weight: 500;
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: var(--transition);
        }

        .nav-links a:hover, .nav-links a.active {
            color: var(--soft-purple);
        }

        .hamburger {
            display: none;
            flex-direction: column;
            gap: 5px;
            cursor: pointer;
        }

        .hamburger span {
            width: 25px;
            height: 3px;
            background: var(--soft-purple);
            border-radius: 2px;
        }

        /* Page Management */
        .page {
            display: none;
        }

        .page.active {
            display: block;
            animation: fadeInPage 0.6s ease-out;
        }

        @keyframes fadeInPage {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Hero Slider */
        .hero {
            height: 80vh;
            position: relative;
            overflow: hidden;
        }

        .slider-container {
            height: 100%;
            display: flex;
            transition: transform 0.8s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .slide {
            min-width: 100%;
            height: 100%;
            position: relative;
            background-size: cover;
            background-position: center;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            text-align: center;
        }

        .slide::after {
            content: '';
            position: absolute;
            inset: 0;
            background: rgba(0,0,0,0.4);
        }

        .slide-content {
            position: relative;
            z-index: 2;
            max-width: 800px;
            padding: 20px;
        }

        .slide-content h2 {
            font-family: var(--font-heading);
            font-size: 4rem;
            margin-bottom: 20px;
        }

        .slide-content p {
            font-size: 1.2rem;
            margin-bottom: 30px;
            font-weight: 300;
        }

        /* Menu Section */
        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 50px;
        }

        .menu-item {
            background: white;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.05);
            transition: var(--transition);
        }

        .menu-item:hover {
            transform: translateY(-10px);
        }

        .menu-img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .menu-info {
            padding: 20px;
        }

        .menu-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }

        .menu-price {
            color: var(--soft-purple);
            font-weight: 700;
        }

        /* Pricing/Packages Table */
        .package-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
        }

        .package-card {
            background: white;
            padding: 40px;
            border-radius: 30px;
            text-align: center;
            border: 2px solid transparent;
            transition: var(--transition);
        }

        .package-card.featured {
            border-color: var(--lavender);
            transform: scale(1.05);
            box-shadow: 0 20px 40px rgba(155, 142, 196, 0.15);
        }

        .package-price {
            font-size: 2.5rem;
            color: var(--soft-purple);
            margin: 20px 0;
            font-weight: 700;
        }

        .package-features {
            list-style: none;
            margin-bottom: 30px;
        }

        .package-features li {
            padding: 10px 0;
            border-bottom: 1px solid #eee;
        }

        /* Forms */
        .auth-container, .reserve-container, .contact-container {
            max-width: 500px;
            margin: 0 auto;
            background: white;
            padding: 40px;
            border-radius: 25px;
            box-shadow: 0 15px 40px rgba(0,0,0,0.05);
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            font-size: 0.9rem;
        }

        .form-group input, .form-group textarea, .form-group select {
            width: 100%;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 12px;
            font-family: inherit;
        }

        /* Parallax */
        .parallax {
            height: 400px;
            background-attachment: fixed;
            background-position: center;
            background-repeat: no-repeat;
            background-size: cover;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            text-align: center;
            position: relative;
        }

        .parallax::before {
            content: '';
            position: absolute;
            inset: 0;
            background: rgba(124, 109, 170, 0.6);
        }

        .parallax-content {
            position: relative;
            z-index: 2;
        }

        /* Contact Info Box */
        .contact-info-box {
            background: var(--bg-light);
            border-radius: 16px;
            padding: 25px 30px;
            margin-top: 30px;
        }

        .contact-info-box h4 {
            font-family: var(--font-heading);
            color: var(--soft-purple);
            margin-bottom: 15px;
            font-size: 1.1rem;
        }

        .contact-info-box p {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 10px;
            font-size: 0.95rem;
        }

        .contact-info-box a {
            color: var(--soft-purple);
            text-decoration: none;
            font-weight: 600;
        }

        .contact-info-box a:hover {
            text-decoration: underline;
        }

        /* Footer */
        footer {
            background: white;
            padding: 80px 0 20px;
            border-top: 1px solid #eee;
        }

        .footer-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 40px;
            margin-bottom: 60px;
        }

        .footer-logo {
            font-family: var(--font-handwritten);
            font-size: 2.5rem;
            color: var(--soft-purple);
            margin-bottom: 20px;
        }

        .footer-links h4 {
            margin-bottom: 25px;
            font-family: var(--font-heading);
            color: var(--soft-purple);
        }

        .footer-links ul {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 12px;
        }

        .footer-links a {
            text-decoration: none;
            color: var(--text-dark);
            transition: var(--transition);
        }

        .footer-links a:hover {
            color: var(--soft-purple);
            padding-left: 5px;
        }

        .social-icons {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .social-icons a {
            width: 40px;
            height: 40px;
            background: var(--bg-light);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--soft-purple);
            transition: var(--transition);
        }

        .social-icons a:hover {
            background: var(--soft-purple);
            color: white;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
                flex-direction: column;
                position: absolute;
                top: 100%;
                left: 0;
                width: 100%;
                background: white;
                padding: 20px;
                text-align: center;
                box-shadow: 0 10px 20px rgba(0,0,0,0.1);
            }

            .nav-links.show {
                display: flex;
            }

            .hamburger {
                display: flex;
                margin-top: 10px;
            }

            .slide-content h2 {
                font-size: 2.5rem;
            }

            .package-card.featured {
                transform: scale(1);
            }
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: var(--bg-light);
        }
        ::-webkit-scrollbar-thumb {
            background: var(--lavender);
            border-radius: 10px;
        }
    </style>
</head>
<body>

    <!-- Navigation -->
    <nav>
        <div class="container nav-content">
            <a href="#" class="logo" onclick="navigateTo('home')">Sieerre</a>
            <div class="hamburger" id="hamburger">
                <span></span>
                <span></span>
                <span></span>
            </div>
            <ul class="nav-links" id="navLinks">
                <li><a href="#" onclick="navigateTo('home')" class="active">Beranda</a></li>
                <li><a href="#" onclick="navigateTo('menu')">Menu</a></li>
                <li><a href="#" onclick="navigateTo('packages')">Paket Rajut</a></li>
                <li><a href="#" onclick="navigateTo('reservation')">Reservasi</a></li>
                <li><a href="#" onclick="navigateTo('about')">Tentang Kami</a></li>
                <li><a href="#" onclick="navigateTo('contact')">Kontak</a></li>
                <li><a href="#" onclick="navigateTo('login')">Masuk</a></li>
            </ul>
        </div>
    </nav>

    <!-- PAGE: HOME -->
    <main id="home" class="page active">
        <section class="hero">
            <div class="slider-container" id="heroSlider">
                <div class="slide" style="background-image: url('https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?auto=format&fit=crop&q=80&w=1600')">
                    <div class="slide-content">
                        <h2>Ketenangan dalam Setiap Rajutan</h2>
                        <p>Nikmati hidangan Jepang otentik sambil mengekspresikan kreativitas Anda di Sieerre.</p>
                        <a href="#" onclick="navigateTo('reservation')" class="btn btn-primary">Pesan Meja Sekarang</a>
                    </div>
                </div>
                <div class="slide" style="background-image: url('https://images.unsplash.com/photo-1534433394341-a0709b699929?auto=format&fit=crop&q=80&w=1600')">
                    <div class="slide-content">
                        <h2>Seni Merajut & Kuliner</h2>
                        <p>Kami menyediakan benang dan peralatan rajut berkualitas untuk menemani waktu santai Anda.</p>
                        <a href="#" onclick="navigateTo('packages')" class="btn btn-primary">Lihat Paket Kreatif</a>
                    </div>
                </div>
            </div>
        </section>

        <section class="section-padding container">
            <div style="text-align: center; max-width: 700px; margin: 0 auto;">
                <h3 style="font-family: var(--font-handwritten); font-size: 2.5rem; color: var(--soft-purple);">Cerita Kami</h3>
                <h2 style="font-family: var(--font-heading); font-size: 2.5rem; margin: 20px 0;">Paduan Harmoni Jepang & Kreativitas</h2>
                <p class="fade-in">Di Sieerre, kami percaya bahwa makanan enak dan kegiatan kreatif adalah kunci kebahagiaan. Berlokasi di jantung Indonesia, kami menghadirkan nuansa Zen Jepang yang dipadukan dengan kenyamanan studio rajut.</p>
            </div>
        </section>

        <div class="parallax" style="background-image: url('https://images.unsplash.com/photo-1447933630913-bb7941c7004d?auto=format&fit=crop&q=80&w=1600')">
            <div class="parallax-content">
                <h2 style="font-family: var(--font-handwritten); font-size: 3.5rem;">Ciptakan Karya Sambil Menikmati Sushi</h2>
            </div>
        </div>
    </main>

    <!-- PAGE: MENU -->
    <main id="menu" class="page">
        <section class="section-padding container">
            <div style="text-align: center; margin-bottom: 50px;">
                <h2 style="font-family: var(--font-heading); font-size: 3rem;">Menu Spesialisasi Kami</h2>
                <p>Hidangan Jepang pilihan dengan bahan-bahan segar setiap hari.</p>
            </div>
            <div class="menu-grid">
                <div class="menu-item fade-in">
                    <img src="https://images.unsplash.com/photo-1579871494447-9811cf80d66c?auto=format&fit=crop&q=80&w=400" alt="Sushi" class="menu-img">
                    <div class="menu-info">
                        <div class="menu-header">
                            <h4>Sieerre Signature Roll</h4>
                            <span class="menu-price">Rp 85.000</span>
                        </div>
                        <p>Salmon, alpukat, dan saus krim rahasia Sieerre.</p>
                    </div>
                </div>
                <div class="menu-item fade-in">
                    <img src="https://images.unsplash.com/photo-1569718212165-3a8278d5f624?auto=format&fit=crop&q=80&w=400" alt="Ramen" class="menu-img">
                    <div class="menu-info">
                        <div class="menu-header">
                            <h4>Hokkaido Miso Ramen</h4>
                            <span class="menu-price">Rp 72.000</span>
                        </div>
                        <p>Mie gandum buatan tangan dengan kaldu miso kental.</p>
                    </div>
                </div>
                <div class="menu-item fade-in">
                    <img src="https://images.unsplash.com/photo-1514432324607-a09d9b4aefdd?auto=format&fit=crop&q=80&w=400" alt="Tea" class="menu-img">
                    <div class="menu-info">
                        <div class="menu-header">
                            <h4>Premium Matcha Set</h4>
                            <span class="menu-price">Rp 45.000</span>
                        </div>
                        <p>Matcha murni dari Uji, Jepang dengan Mochi tradisional.</p>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- PAGE: PACKAGES -->
    <main id="packages" class="page">
        <section class="section-padding container">
            <div style="text-align: center; margin-bottom: 50px;">
                <h2 style="font-family: var(--font-heading); font-size: 3rem;">Paket Kreatif Sieerre</h2>
                <p>Pilih paket yang paling sesuai dengan kebutuhan kreativitas Anda.</p>
            </div>
            <div class="package-grid">
                <div class="package-card fade-in">
                    <h3>Pemula (Beginner)</h3>
                    <div class="package-price">Rp 150k</div>
                    <ul class="package-features">
                        <li>1 Hidangan Utama</li>
                        <li>1 Minuman (Ocha/Teh)</li>
                        <li>Kit Rajut Dasar (Benang + Hook)</li>
                        <li>Panduan Pola Sederhana</li>
                    </ul>
                    <a href="#" onclick="navigateTo('reservation')" class="btn btn-primary">Pilih Paket</a>
                </div>
                <div class="package-card featured fade-in">
                    <h3>Hobi (Enthusiast)</h3>
                    <div class="package-price">Rp 275k</div>
                    <ul class="package-features">
                        <li>Set Menu Lengkap (Appetizer, Main, Dessert)</li>
                        <li>Minuman Bebas Pilih</li>
                        <li>Benang Katun Premium</li>
                        <li>Akses Workshop Singkat</li>
                    </ul>
                    <a href="#" onclick="navigateTo('reservation')" class="btn btn-primary">Pilih Paket</a>
                </div>
                <div class="package-card fade-in">
                    <h3>Komunitas (Group)</h3>
                    <div class="package-price">Rp 120k/pax</div>
                    <ul class="package-features">
                        <li>Minimal 5 Orang</li>
                        <li>Platter Sharing Jepang</li>
                        <li>Benang Tanpa Batas (Project di tempat)</li>
                        <li>Meja Bundar Khusus Merajut</li>
                    </ul>
                    <a href="#" onclick="navigateTo('reservation')" class="btn btn-primary">Pilih Paket</a>
                </div>
            </div>
        </section>
    </main>

    <!-- PAGE: RESERVATION -->
    <main id="reservation" class="page">
        <section class="section-padding container">
            <div class="reserve-container">
                <h2 style="font-family: var(--font-heading); text-align: center; margin-bottom: 30px;">Reservasi Meja</h2>
                <form id="reserveForm">
                    <div class="form-group">
                        <label>Nama Lengkap</label>
                        <input type="text" id="resName" required placeholder="Contoh: Budi Santoso">
                    </div>
                    <div class="form-group">
                        <label>Tanggal & Waktu</label>
                        <input type="datetime-local" id="resDate" required>
                    </div>
                    <div class="form-group">
                        <label>Jumlah Orang</label>
                        <input type="number" id="resGuest" min="1" max="20" value="2">
                    </div>
                    <div class="form-group">
                        <label>Pilih Paket (Opsional)</label>
                        <select id="resPackage">
                            <option value="Hanya Makan">Hanya Makan (Tanpa Rajut)</option>
                            <option value="Paket Pemula">Paket Pemula</option>
                            <option value="Paket Hobi">Paket Hobi</option>
                            <option value="Paket Komunitas">Paket Komunitas</option>
                        </select>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">Konfirmasi via WhatsApp</button>
                </form>
            </div>
        </section>
    </main>

    <!-- PAGE: CONTACT -->
    <main id="contact" class="page">
        <section class="section-padding container">
            <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 50px;">
                <div>
                    <div class="contact-container">
                        <h2 style="font-family: var(--font-heading); margin-bottom: 20px;">Hubungi Kami</h2>
                        <form id="contactForm">
                            <div class="form-group">
                                <label>Email</label>
                                <input type="email" required placeholder="email@contoh.com">
                            </div>
                            <div class="form-group">
                                <label>Pesan</label>
                                <textarea rows="5" required placeholder="Tuliskan pertanyaan Anda..."></textarea>
                            </div>
                            <button type="submit" class="btn btn-primary">Kirim Pesan</button>
                        </form>
                    </div>
                    <div class="contact-info-box" style="max-width: 500px; margin: 20px auto 0;">
                        <h4>Informasi Kontak</h4>
                        <p>
                            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#7c6daa" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="20" height="16" x="2" y="4" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
                            <a href="mailto:renataawibiologi@gmail.com">renataawibiologi@gmail.com</a>
                        </p>
                        <p>
                            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#7c6daa" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 13.5a19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 3.62 2.82h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l.76-.76a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 21.73 17.5z"/></svg>
                            <a href="https://wa.me/6281234567891" target="_blank">081234567891</a>
                        </p>
                    </div>
                </div>
                <div>
                    <h2 style="font-family: var(--font-heading); margin-bottom: 20px;">Lokasi Kami</h2>
                    <p style="margin-bottom: 20px;">Jl. Sidomulyo No.1, Semaki, Kec. Umbulharjo, Kota Yogyakarta (SMA Negeri 8 Yogyakarta).</p>
                    <div style="width: 100%; height: 350px; border-radius: 20px; overflow: hidden;">
                        <iframe 
                            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3953.0!2d110.3844!3d-7.8012!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e7a5786b0ba7027%3A0x5028b4b0c9b87a3f!2sSMA%20Negeri%208%20Yogyakarta!5e0!3m2!1sid!2sid!4v1717200000000!5m2!1sid!2sid" 
                            width="100%" height="100%" style="border:0;" allowfullscreen="" loading="lazy">
                        </iframe>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- PAGE: LOGIN -->
    <main id="login" class="page">
        <section class="section-padding container">
            <div class="auth-container">
                <h2 style="font-family: var(--font-heading); text-align: center; margin-bottom: 30px;">Selamat Datang Kembali</h2>
                <form onsubmit="event.preventDefault(); alert('Masuk berhasil!');">
                    <div class="form-group">
                        <label>Username / Email</label>
                        <input type="text" required>
                    </div>
                    <div class="form-group">
                        <label>Kata Sandi</label>
                        <input type="password" required>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">Masuk</button>
                    <p style="text-align: center; margin-top: 20px; font-size: 0.9rem;">
                        Belum punya akun? <a href="#" style="color: var(--soft-purple);">Daftar di sini</a>
                    </p>
                </form>
            </div>
        </section>
    </main>

    <!-- PAGE: ABOUT -->
    <main id="about" class="page">
        <section class="section-padding container">
            <div style="max-width: 800px; margin: 0 auto; text-align: center;">
                <h2 style="font-family: var(--font-heading); font-size: 3rem; margin-bottom: 30px;">Tentang Sieerre</h2>
                <img src="https://images.unsplash.com/photo-1542124467000-d99f798bb9d8?auto=format&fit=crop&q=80&w=800" style="width: 100%; border-radius: 30px; margin-bottom: 40px;" alt="Restoran">
                <p style="font-size: 1.1rem; margin-bottom: 20px;">Sieerre lahir dari ide sederhana: menciptakan ruang di mana waktu seolah melambat. Di tengah hiruk-pikuk kehidupan modern, kami ingin memberikan tempat pelarian yang memadukan kelezatan sushi dengan terapeutik merajut.</p>
                <p style="font-size: 1.1rem;">Nama "Sieerre" diambil dari filosofi ketenangan. Di sini, setiap simpul rajutan dan setiap suapan sushi adalah bentuk apresiasi terhadap momen saat ini. Kami menyediakan semua peralatan yang Anda butuhkan, sehingga Anda hanya perlu membawa semangat kreativitas Anda.</p>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer>
        <div class="container footer-grid">
            <div>
                <div class="footer-logo">Sieerre</div>
                <p>Ruang kreatif untuk kuliner Jepang dan seni merajut. Temukan ketenangan di setiap sudut.</p>
                <div class="social-icons">
                    <a href="#"><i data-lucide="instagram"></i></a>
                    <a href="#"><i data-lucide="facebook"></i></a>
                    <a href="#"><i data-lucide="twitter"></i></a>
                </div>
            </div>
            <div class="footer-links">
                <h4>Navigasi</h4>
                <ul>
                    <li><a href="#" onclick="navigateTo('home')">Beranda</a></li>
                    <li><a href="#" onclick="navigateTo('menu')">Menu Kami</a></li>
                    <li><a href="#" onclick="navigateTo('packages')">Paket Rajut</a></li>
                    <li><a href="#" onclick="navigateTo('reservation')">Reservasi</a></li>
                </ul>
            </div>
            <div class="footer-links">
                <h4>Jam Operasional</h4>
                <ul>
                    <li>Senin - Jumat: 10:00 - 21:00</li>
                    <li>Sabtu - Minggu: 09:00 - 22:00</li>
                    <li>Workshop Merajut: Setiap Sabtu</li>
                </ul>
            </div>
            <div class="footer-links">
                <h4>Kabar Harian</h4>
                <p style="font-size: 0.8rem; margin-bottom: 15px;">Dapatkan info promo dan pola rajut gratis!</p>
                <form onsubmit="event.preventDefault(); alert('Terima kasih telah berlangganan!');" style="display: flex; gap: 10px;">
                    <input type="email" placeholder="Email Anda" style="padding: 10px; border-radius: 10px; border: 1px solid #ddd; width: 100%;">
                    <button type="submit" class="btn btn-primary" style="padding: 10px 15px;">Ikuti</button>
                </form>
            </div>
        </div>
        <div class="container" style="border-top: 1px solid #eee; padding-top: 20px; padding-bottom: 20px;"></div>
    </footer>

    <script>
        // Initializing Lucide Icons
        lucide.createIcons();

        // Page Navigation Logic
        function navigateTo(pageId) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
            document.querySelectorAll('.nav-links a').forEach(a => a.classList.remove('active'));
            
            const activePage = document.getElementById(pageId);
            if(activePage) {
                activePage.classList.add('active');
                window.scrollTo({ top: 0, behavior: 'smooth' });
            }

            // Mobile menu close on click
            document.getElementById('navLinks').classList.remove('show');
            
            // Highlight active link
            const links = document.querySelectorAll('.nav-links a');
            links.forEach(link => {
                if(link.getAttribute('onclick').includes(pageId)) {
                    link.classList.add('active');
                }
            });
        }

        // Mobile Hamburger Menu
        const hamburger = document.getElementById('hamburger');
        const navLinks = document.getElementById('navLinks');
        
        hamburger.addEventListener('click', () => {
            navLinks.classList.toggle('show');
        });

        // Hero Slider Logic
        let currentSlide = 0;
        const slides = document.querySelectorAll('.slide');
        const sliderContainer = document.getElementById('heroSlider');

        function nextSlide() {
            currentSlide = (currentSlide + 1) % slides.length;
            sliderContainer.style.transform = `translateX(-${currentSlide * 100}%)`;
        }
        setInterval(nextSlide, 5000);

        // Reservation WhatsApp Link Logic
        document.getElementById('reserveForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const name = document.getElementById('resName').value;
            const date = document.getElementById('resDate').value;
            const guests = document.getElementById('resGuest').value;
            const pkg = document.getElementById('resPackage').value;
            
            const text = `Halo Sieerre! Saya ingin reservasi:\n\nNama: ${name}\nWaktu: ${date}\nJumlah Tamu: ${guests} Orang\nPaket: ${pkg}`;
            const encodedText = encodeURIComponent(text);
            const whatsappUrl = `https://wa.me/6281234567891?text=${encodedText}`;
            
            window.open(whatsappUrl, '_blank');
        });

        // Scroll Animation (Intersection Observer)
        const observerOptions = {
            threshold: 0.1
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));

        // Smooth Scroll for internal anchors
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                if (this.getAttribute('href') !== '#') {
                    e.preventDefault();
                    document.querySelector(this.getAttribute('href')).scrollIntoView({
                        behavior: 'smooth'
                    });
                }
            });
        });
    </script>
</body>
</html>
