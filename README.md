HTML
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cinematic Portfolio</title>
    <!-- Google Fonts: ปรับฟอนต์ให้ดูโมเดิร์นและอบอุ่น -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Anuphan:wght@300;400;600&family=Playfair+Display:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
    
    <style>
        /* สไตล์พื้นฐานและการกำหนดโทนสี (Mood & Tone) */
        :root {
            --bg-color: #fcf9f5;      /* สีครีมละมุน อารมณ์ Nostalgic */
            --text-color: #2c2520;    /* สีน้ำตาลเข้มเกือบดำ ช่วยให้สบายตา */
            --accent-color: #d4a373;  /* สีทอง Warm Glow */
            --card-bg: #ffffff;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Anuphan', sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Header & Navigation */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 2rem 10%;
            position: absolute;
            width: 100%;
            z-index: 10;
        }

        .logo {
            font-family: 'Playfair Display', serif;
            font-size: 1.5rem;
            font-weight: 600;
            letter-spacing: 2px;
        }

        nav a {
            text-decoration: none;
            color: var(--text-color);
            margin-left: 2rem;
            font-size: 0.9rem;
            letter-spacing: 1px;
            transition: color 0.3s;
        }

        nav a:hover {
            color: var(--accent-color);
        }

        /* Hero Section: หน้าเปิดตัวแบบ Cinematic */
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 1rem;
            background: linear-gradient(to bottom, rgba(252,249,245,0.8), var(--bg-color)), 
                        url('https://images.unsplash.com/photo-1507525428034-b723cf961d3e?q=80&w=2073') center/cover no-repeat;
            /* หมายเหตุ: สามารถเปลี่ยน URL รูปภาพพื้นหลังตามใจชอบได้ที่นี่ */
        }

        .hero h1 {
            font-family: 'Playfair Display', serif;
            font-size: 4rem;
            font-weight: 400;
            font-style: italic;
            margin-bottom: 1rem;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 1.5s forwards 0.5s;
        }

        .hero p {
            font-size: 1.1rem;
            letter-spacing: 3px;
            text-transform: uppercase;
            color: #7a6f66;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 1.5s forwards 1s;
        }

        /* Gallery Section: จัดเรียงผลงาน */
        .gallery-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 5rem 2rem;
        }

        .section-title {
            font-family: 'Playfair Display', serif;
            font-size: 2rem;
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
        }

        .section-title::after {
            content: '';
            display: block;
            width: 40px;
            height: 1px;
            background-color: var(--accent-color);
            margin: 10px auto 0;
        }

        /* ใช้ Grid ในการจัดวางรูปภาพแบบไม่เท่ากัน เพิ่มความมีมิติ (Asymmetric Layout) */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2.5rem;
        }

        .grid-item {
            background-color: var(--card-bg);
            border-radius: 4px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.03);
            transition: transform 0.4s ease, box-shadow 0.4s ease;
        }

        .grid-item:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(212, 163, 115, 0.15);
        }

        .image-box {
            position: relative;
            overflow: hidden;
            padding-top: 65%; /* ควบคุมอัตราส่วนรูปภาพ */
        }

        .image-box img {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.6s cubic-bezier(0.25, 1, 0.5, 1);
        }

        .grid-item:hover .image-box img {
            transform: scale(1.05);
        }

        .info-box {
            padding: 1.5rem;
        }

        .info-box h3 {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
            font-weight: 600;
        }

        .info-box p {
            font-size: 0.9rem;
            color: #8a7e74;
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 3rem;
            font-size: 0.85rem;
            color: #8a7e74;
            border-top: 1px solid #f0e6df;
        }

        /* Animations */
        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Responsive สำหรับมือถือ */
        @media (max-width: 768px) {
            header {
                padding: 1.5rem 5%;
            }
            .hero h1 {
                font-size: 2.5rem;
            }
            .grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>

    <!-- ส่วนหัว/เมนู -->
    <header>
        <div class="logo">MEMORIES.</div>
        <nav>
            <a href="#">หน้าแรก</a>
            <a href="#">ผลงาน</a>
            <a href="#">ติดต่อ</a>
        </nav>
    </header>

    <!-- ส่วนต้อนรับ (Hero) -->
    <section class="hero">
        <h1>Golden Hour Memories</h1>
        <p>บันทึกความทรงจำผ่านแสงเงาและมุมมอง</p>
    </section>

    <!-- ส่วนแสดงผลงาน (Gallery) -->
    <main class="gallery-container">
        <h2 class="section-title">Selected Works</h2>
        
        <div class="grid">
            <!-- ชิ้นงานที่ 1 -->
            <div class="grid-item">
                <div class="image-box">
                    <img src="https://images.unsplash.com/photo-1542038784456-1ea8e935640e?q=80&w=1000" alt="Work 1">
                </div>
                <div class="info-box">
                    <h3>The Nostalgic Alley</h3>
                    <p>ภาพถ่ายตรอกเก่าเล่าความทรงจำยุค 60s</p>
                </div>
            </div>

            <!-- ชิ้นงานที่ 2 -->
            <div class="grid-item">
                <div class="image-box">
                    <img src="https://images.unsplash.com/photo-1509198397868-475647b2a1e5?q=80&w=1000" alt="Work 2">
                </div>
                <div class="info-box">
                    <h3>Warm Golden Glow</h3>
                    <p>ศิลปะแห่งแสงแดดยามเย็นที่สาดส่องลงบนเนื้อไม้</p>
                </div>
            </div>

            <!-- ชิ้นงานที่ 3 -->
            <div class="grid-item">
                <div class="image-box">
                    <img src="https://images.unsplash.com/photo-1513836279014-a89f7a76ae86?q=80&w=1000" alt="Work 3">
                </div>
                <div class="info-box">
                    <h3>Nature & Cozy Space</h3>
                    <p>การผสมผสานสีเขียวของใบไม้เข้ากับความเงียบสงบ</p>
                </div>
            </div>
        </div>
    </main>

    <!-- ส่วนท้าย -->
    <footer>
        <p>&copy; 2026 MEMORIES Studio. All rights reserved.</p>
    </footer>

</body>
</html>
