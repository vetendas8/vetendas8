<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Seymur - Profil</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Fira Code', 'Courier New', monospace;
            background: linear-gradient(135deg, #0D1117 0%, #1a1f2e 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            color: #e0e6ed;
            padding: 20px;
        }

        .container {
            text-align: center;
            max-width: 900px;
            width: 100%;
        }

        .header {
            margin-bottom: 40px;
            animation: fadeIn 0.8s ease-in;
        }

        .header h1 {
            font-size: 2.5em;
            background: linear-gradient(135deg, #17b890 0%, #ff6b6b 50%, #20b2aa 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 10px;
            text-shadow: 0 0 20px rgba(32, 178, 170, 0.3);
        }

        .header p {
            color: #8892b0;
            font-size: 1.1em;
            margin-top: 10px;
        }

        /* 3D Küp */
        .cube-container {
            perspective: 1000px;
            display: flex;
            justify-content: center;
            margin: 40px 0;
        }

        .cube-wrapper {
            width: 300px;
            height: 300px;
            position: relative;
            transform-style: preserve-3d;
            animation: rotateCube 15s infinite linear;
        }

        .cube-face {
            position: absolute;
            width: 300px;
            height: 300px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.4em;
            font-weight: bold;
            border: 3px solid;
            border-radius: 10px;
            backdrop-filter: blur(10px);
            padding: 30px;
            text-align: center;
            flex-direction: column;
            justify-content: space-around;
            transform-style: preserve-3d;
            transition: all 0.3s ease;
        }

        /* Renk Şeması */
        .face-1 {
            background: rgba(32, 178, 170, 0.2);
            border-color: #20b2aa;
            color: #20b2aa;
            transform: rotateY(0deg) translateZ(150px);
            box-shadow: 0 0 30px rgba(32, 178, 170, 0.5);
        }

        .face-2 {
            background: rgba(23, 184, 144, 0.2);
            border-color: #17b890;
            color: #17b890;
            transform: rotateY(90deg) translateZ(150px);
            box-shadow: 0 0 30px rgba(23, 184, 144, 0.5);
        }

        .face-3 {
            background: rgba(255, 107, 107, 0.2);
            border-color: #ff6b6b;
            color: #ff6b6b;
            transform: rotateY(180deg) translateZ(150px);
            box-shadow: 0 0 30px rgba(255, 107, 107, 0.5);
        }

        .face-4 {
            background: rgba(32, 178, 170, 0.2);
            border-color: #20b2aa;
            color: #20b2aa;
            transform: rotateY(270deg) translateZ(150px);
            box-shadow: 0 0 30px rgba(32, 178, 170, 0.5);
        }

        .face-5 {
            background: rgba(23, 184, 144, 0.2);
            border-color: #17b890;
            color: #17b890;
            transform: rotateX(90deg) translateZ(150px);
            box-shadow: 0 0 30px rgba(23, 184, 144, 0.5);
        }

        .face-6 {
            background: rgba(255, 107, 107, 0.2);
            border-color: #ff6b6b;
            color: #ff6b6b;
            transform: rotateX(-90deg) translateZ(150px);
            box-shadow: 0 0 30px rgba(255, 107, 107, 0.5);
        }

        @keyframes rotateCube {
            0% {
                transform: rotateX(0deg) rotateY(0deg);
            }
            25% {
                transform: rotateX(0deg) rotateY(90deg);
            }
            50% {
                transform: rotateX(0deg) rotateY(180deg);
            }
            75% {
                transform: rotateX(0deg) rotateY(270deg);
            }
            100% {
                transform: rotateX(0deg) rotateY(360deg);
            }
        }

        .face-title {
            font-size: 1.3em;
            margin-bottom: 15px;
            font-weight: bold;
            letter-spacing: 2px;
        }

        .face-content {
            font-size: 0.95em;
            line-height: 1.6;
        }

        .face-content p {
            margin: 5px 0;
        }

        /* Alt Bilgiler */
        .info-section {
            margin-top: 60px;
            padding: 30px;
            background: rgba(32, 178, 170, 0.1);
            border: 2px solid #20b2aa;
            border-radius: 10px;
            animation: slideUp 0.8s ease-out;
        }

        .info-section h2 {
            color: #17b890;
            margin-bottom: 20px;
            font-size: 1.5em;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin: 20px 0;
        }

        .skill-badge {
            padding: 12px;
            background: rgba(255, 107, 107, 0.2);
            border: 2px solid #ff6b6b;
            border-radius: 8px;
            color: #ff6b6b;
            font-weight: bold;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .skill-badge:hover {
            background: rgba(255, 107, 107, 0.4);
            transform: translateY(-5px);
            box-shadow: 0 0 20px rgba(255, 107, 107, 0.6);
        }

        .social-links {
            margin-top: 20px;
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
        }

        .social-link {
            padding: 10px 20px;
            background: rgba(23, 184, 144, 0.2);
            border: 2px solid #17b890;
            border-radius: 8px;
            color: #17b890;
            text-decoration: none;
            font-weight: bold;
            transition: all 0.3s ease;
        }

        .social-link:hover {
            background: rgba(23, 184, 144, 0.4);
            box-shadow: 0 0 20px rgba(23, 184, 144, 0.6);
            transform: translateY(-3px);
        }

        /* Animasyonlar */
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .pulse {
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% {
                opacity: 1;
            }
            50% {
                opacity: 0.7;
            }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .cube-wrapper {
                width: 250px;
                height: 250px;
            }

            .cube-face {
                width: 250px;
                height: 250px;
                font-size: 1.1em;
            }

            .cube-face {
                transform-origin: center;
            }

            .face-1 { transform: rotateY(0deg) translateZ(125px); }
            .face-2 { transform: rotateY(90deg) translateZ(125px); }
            .face-3 { transform: rotateY(180deg) translateZ(125px); }
            .face-4 { transform: rotateY(270deg) translateZ(125px); }
            .face-5 { transform: rotateX(90deg) translateZ(125px); }
            .face-6 { transform: rotateX(-90deg) translateZ(125px); }

            .header h1 {
                font-size: 2em;
            }

            .skills-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        .divider {
            height: 2px;
            background: linear-gradient(90deg, #20b2aa 0%, #17b890 50%, #ff6b6b 100%);
            margin: 30px 0;
            border-radius: 1px;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="header">
            <h1>👋 Selamlar, Seymur!</h1>
            <p>💻 Kod Yazarım | 🧠 Sistem Mühendisliği | 🎵 Melankolik Müzik Severim</p>
        </div>

        <!-- 3D Küp -->
        <div class="cube-container">
            <div class="cube-wrapper">
                <!-- Yüz 1: Ana Bilgi -->
                <div class="cube-face face-1">
                    <div class="face-title">👨‍💻 Seymur</div>
                    <div class="face-content">
                        <p><strong>Kod Yazarı</strong></p>
                        <p>Planlama & Sistem Bilgisi</p>
                    </div>
                </div>

                <!-- Yüz 2: Beceriler -->
                <div class="cube-face face-2">
                    <div class="face-title">🚀 Becerilerim</div>
                    <div class="face-content">
                        <p>Python • C++</p>
                        <p>Sistem Tasarımı</p>
                        <p>Problem Çözme</p>
                    </div>
                </div>

                <!-- Yüz 3: Araçlar -->
                <div class="cube-face face-3">
                    <div class="face-title">🛠️ Araçlarım</div>
                    <div class="face-content">
                        <p>VS Code</p>
                        <p>ChatGPT ile Alıştırma</p>
                        <p>Linux & Komut Satırı</p>
                    </div>
                </div>

                <!-- Yüz 4: İlgiler -->
                <div class="cube-face face-4">
                    <div class="face-title">🎵 İlgilerim</div>
                    <div class="face-content">
                        <p>Klasik Müzik</p>
                        <p>Melankolik Müzik</p>
                        <p>Animasyon & Tasarım</p>
                    </div>
                </div>

                <!-- Yüz 5: Hedefler -->
                <div class="cube-face face-5">
                    <div class="face-title">🎯 Hedeflerim</div>
                    <div class="face-content">
                        <p><strong>Full Stack Developer</strong></p>
                        <p>Sistem Mimarı</p>
                        <p>Yenilikçi Projeler</p>
                    </div>
                </div>

                <!-- Yüz 6: Motto -->
                <div class="cube-face face-6">
                    <div class="face-title">✨ Felsefem</div>
                    <div class="face-content">
                        <p>"Kod yazın,</p>
                        <p>öğrenin,</p>
                        <p>yaratın"</p>
                    </div>
                </div>
            </div>
        </div>

        <div class="divider"></div>

        <!-- Teknik Beceriler -->
        <div class="info-section">
            <h2>💡 Teknik Yetenek Alanları</h2>
            <div class="skills-grid">
                <div class="skill-badge">Python</div>
                <div class="skill-badge">C++</div>
                <div class="skill-badge">Sistem Tasarımı</div>
                <div class="skill-badge">Algoritma</div>
                <div class="skill-badge">Veri Yapıları</div>
                <div class="skill-badge">Planlama</div>
            </div>
        </div>

        <!-- İstatistikler -->
        <div class="info-section" style="background: rgba(23, 184, 144, 0.1); border-color: #17b890; margin-top: 20px;">
            <h2>📊 GitHub İstatistikleri</h2>
            <p style="margin-top: 15px; color: #a0aec0;">
                <img src="https://github-readme-stats.vercel.app/api?username=vetendas8&show_icons=true&theme=transparent&text_color=e0e6ed&icon_color=20b2aa&border_color=20b2aa" alt="GitHub Stats">
            </p>
        </div>

        <!-- En Çok Kullanılan Diller -->
        <div class="info-section" style="background: rgba(255, 107, 107, 0.1); border-color: #ff6b6b; margin-top: 20px;">
            <h2>🔤 En Çok Kullanılan Diller</h2>
            <p style="margin-top: 15px;">
                <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=vetendas8&layout=compact&theme=transparent&text_color=e0e6ed&border_color=ff6b6b" alt="Top Languages">
            </p>
        </div>

        <div class="divider"></div>

        <!-- İletişim -->
        <div style="margin-top: 40px; animation: slideUp 1s ease-out;">
            <h2 style="color: #20b2aa; margin-bottom: 20px; font-size: 1.5em;">💬 Benimle İletişime Geçin</h2>
            <div class="social-links">
                <a href="https://github.com/vetendas8" class="social-link">🐙 GitHub</a>
                <a href="https://twitter.com" class="social-link">𝕏 Twitter</a>
                <a href="mailto:your-email@example.com" class="social-link">📧 Email</a>
            </div>
        </div>

        <!-- Footer -->
        <div style="margin-top: 60px; color: #8892b0; font-size: 0.9em;">
            <p>✨ 3D Küp Animasyonlu Profil README | Seymur © 2026</p>
            <p style="margin-top: 10px; opacity: 0.7;">Yapım: <span class="pulse">Full Stack Developer Journey</span></p>
        </div>
    </div>
</body>
</html>