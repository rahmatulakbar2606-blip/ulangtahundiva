<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday! 🌸🎁</title>
<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,600;1,400&family=Poppins:wght@300;400;500;600;700&family=Sacramento&display=swap" rel="stylesheet">
<!-- Confetti Library -->
<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
<style>
        :root {
            --bg-color: #fff0f3;
            --primary-color: #ff7096;
            --accent-pink: #ffb3c6;
            --text-color: #59405c;
            --card-bg: rgba(255, 255, 255, 0.92);
            --shadow: 0 20px 40px rgba(255, 112, 150, 0.25);
            --spotify-green: #1db954;
            --spotify-dark: #121212;
            --spotify-card: #181818;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #fff0f3 0%, #ffd6e0 50%, #f3c4fb 100%);
            color: var(--text-color);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            padding: 20px 0;
            position: relative;
        }

        /* --- ANIMASI FOTO BACKGROUND MENGAMBANG --- */
        .photo-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            pointer-events: none;
            z-index: 0;
            overflow: hidden;
        }

        .photo-bg img {
            position: absolute;
            bottom: -150px;
            width: 90px;
            height: 90px;
            object-fit: cover;
            border-radius: 18px;
            border: 3px solid #ffffff;
            box-shadow: 0 8px 20px rgba(255, 112, 150, 0.3);
            opacity: 0.45;
            animation: floatPhoto 16s linear infinite;
        }

        .photo-bg img:nth-child(1) { left: 5%; animation-duration: 14s; animation-delay: 0s; }
        .photo-bg img:nth-child(2) { left: 22%; animation-duration: 18s; animation-delay: 3s; width: 75px; height: 75px; }
        .photo-bg img:nth-child(3) { left: 45%; animation-duration: 15s; animation-delay: 1s; width: 100px; height: 100px; }
        .photo-bg img:nth-child(4) { left: 68%; animation-duration: 19s; animation-delay: 4s; width: 80px; height: 80px; }
        .photo-bg img:nth-child(5) { left: 85%; animation-duration: 16s; animation-delay: 2s; }

        @keyframes floatPhoto {
            0% { transform: translateY(0) rotate(0deg) scale(0.9); opacity: 0; }
            15% { opacity: 0.5; }
            85% { opacity: 0.5; }
            100% { transform: translateY(-120vh) rotate(360deg) scale(1.1); opacity: 0; }
        }

        /* Dekorasi Bunga & Kelopak Mengambang */
        .floral-bg span {
            position: absolute;
            display: block;
            font-size: 24px;
            bottom: -50px;
            animation: floatUp 12s linear infinite;
            z-index: 0;
            opacity: 0.6;
            user-select: none;
        }
        .floral-bg span:nth-child(1) { left: 12%; animation-duration: 9s; animation-delay: 0s; }
        .floral-bg span:nth-child(2) { left: 32%; animation-duration: 14s; animation-delay: 2s; font-size: 18px; }
        .floral-bg span:nth-child(3) { left: 58%; animation-duration: 11s; animation-delay: 1s; font-size: 30px; }
        .floral-bg span:nth-child(4) { left: 78%; animation-duration: 8s; animation-delay: 3s; font-size: 20px; }
        .floral-bg span:nth-child(5) { left: 92%; animation-duration: 13s; animation-delay: 1.5s; font-size: 26px; }

        @keyframes floatUp {
            0% { transform: translateY(0) rotate(0deg); opacity: 0; }
            20% { opacity: 0.7; }
            80% { opacity: 0.7; }
            100% { transform: translateY(-110vh) rotate(360deg); opacity: 0; }
        }

        .container {
            width: 100%;
            max-width: 680px;
            padding: 20px;
            text-align: center;
            position: relative;
            z-index: 1;
        }

        .card::before {
            content: '🌸 💐 🌸';
            display: block;
            font-size: 1.2rem;
            margin-bottom: 10px;
            letter-spacing: 5px;
            text-align: center;
        }

        .card {
            background: var(--card-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            padding: 35px 25px;
            border-radius: 30px;
            box-shadow: var(--shadow);
            margin-bottom: 25px;
            text-align: left;
            display: none;
            opacity: 0;
            transform: scale(0.95);
            transition: all 0.5s cubic-bezier(0.68, -0.55, 0.27, 1.55);
            position: relative;
            border: 3px solid rgba(255, 204, 213, 0.8);
        }

        .card.active {
            display: block;
            opacity: 1;
            transform: scale(1);
        }

        .card h2 {
            font-family: 'Playfair Display', serif;
            color: #ff477e;
            margin-bottom: 12px;
            text-align: center;
            font-size: 1.8rem;
        }

        .message-text {
            font-size: 0.95rem;
            line-height: 1.7;
            color: #6b5270;
            margin-bottom: 15px;
            text-align: center;
        }

        /* --- STYLING SPOTIFY PLAYER (HALAMAN 3) --- */
        .spotify-card {
            background: var(--spotify-dark);
            color: white;
            border-radius: 20px;
            padding: 20px;
            margin: 20px 0;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.35);
            border: 1px solid #282828;
            position: relative;
            overflow: hidden;
        }

        .spotify-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 15px;
        }

        .spotify-logo {
            display: flex;
            align-items: center;
            gap: 6px;
            font-weight: 700;
            font-size: 0.85rem;
            color: var(--spotify-green);
        }

        .spotify-logo svg {
            width: 20px;
            height: 20px;
            fill: var(--spotify-green);
        }

        .spotify-body {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 15px;
        }

        .spotify-cover {
            width: 70px;
            height: 70px;
            border-radius: 12px;
            object-fit: cover;
            box-shadow: 0 5px 15px rgba(0,0,0,0.5);
            transition: transform 0.5s ease;
        }

        .spotify-cover.playing {
            animation: rotateAlbum 12s linear infinite;
        }

        @keyframes rotateAlbum {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .spotify-track-info {
            flex-grow: 1;
            text-align: left;
            overflow: hidden;
        }

        .spotify-track-title {
            font-size: 0.95rem;
            font-weight: 700;
            color: #ffffff;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .spotify-artist {
            font-size: 0.8rem;
            color: #b3b3b3;
            margin-top: 2px;
        }

        .spotify-like-btn {
            color: var(--spotify-green);
            font-size: 1.2rem;
            cursor: pointer;
            user-select: none;
        }

        .spotify-progress-container {
            width: 100%;
            margin-bottom: 12px;
        }

        .spotify-progress-bar {
            width: 100%;
            height: 4px;
            background: #4d4d4d;
            border-radius: 2px;
            position: relative;
            cursor: pointer;
            overflow: hidden;
        }

        .spotify-progress-fill {
            height: 100%;
            width: 0%;
            background: var(--spotify-green);
            border-radius: 2px;
            transition: width 0.1s linear;
        }

        .spotify-time {
            display: flex;
            justify-content: space-between;
            font-size: 0.7rem;
            color: #a7a7a7;
            margin-top: 4px;
        }

        .spotify-controls {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .spotify-btn-group {
            display: flex;
            align-items: center;
            gap: 18px;
            margin: 0 auto;
        }

        .spotify-icon-btn {
            background: none;
            border: none;
            color: #b3b3b3;
            font-size: 1.1rem;
            cursor: pointer;
            transition: 0.2s;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .spotify-icon-btn:hover {
            color: #ffffff;
            transform: scale(1.1);
        }

        .spotify-play-btn {
            background: var(--spotify-green);
            color: #000000;
            border: none;
            width: 42px;
            height: 42px;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.1rem;
            transition: transform 0.2s;
            box-shadow: 0 4px 12px rgba(29, 185, 84, 0.4);
        }

        .spotify-play-btn:hover {
            transform: scale(1.08);
            background: #1ed760;
        }

        .spotify-volume {
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .spotify-volume-icon {
            font-size: 0.85rem;
            color: #b3b3b3;
        }

        .spotify-volume-slider {
            width: 70px;
            accent-color: var(--spotify-green);
            cursor: pointer;
            height: 4px;
        }

        /* --- STYLING HALAMAN KALENDER --- */
        .calendar-card-box {
            background: #ffffff;
            border-radius: 20px;
            padding: 20px;
            border: 2px solid #ffccd5;
            box-shadow: 0 8px 20px rgba(255, 112, 150, 0.12);
            margin: 20px 0;
        }

        .calendar-header-title {
            text-align: center;
            font-family: 'Playfair Display', serif;
            color: #ff477e;
            font-size: 1.3rem;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .calendar-grid {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 8px;
            text-align: center;
        }

        .day-header {
            font-weight: 600;
            font-size: 0.8rem;
            color: #ff7096;
            padding-bottom: 5px;
        }

        .day-cell {
            padding: 10px 0;
            font-size: 0.9rem;
            color: #59405c;
            border-radius: 50%;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 500;
        }

        .day-cell.empty { visibility: hidden; }

        .day-cell.circled {
            color: #ff477e;
            font-weight: 700;
        }

        .day-cell.circled::after {
            content: '';
            position: absolute;
            width: 36px;
            height: 36px;
            border: 3px solid #ff477e;
            border-radius: 52% 48% 45% 55% / 48% 52% 48% 52%;
            transform: rotate(-6deg);
            box-shadow: 0 0 8px rgba(255, 71, 126, 0.4);
            animation: pulseCircle 2s infinite alternate;
        }

        @keyframes pulseCircle {
            0% { transform: scale(1) rotate(-6deg); }
            100% { transform: scale(1.08) rotate(-3deg); }
        }

        .page-photo-banner {
            width: 100%;
            height: 180px;
            object-fit: cover;
            border-radius: 20px;
            margin-bottom: 18px;
            border: 3px solid #ffccd5;
            box-shadow: 0 6px 18px rgba(255, 112, 150, 0.18);
        }

        .page-photo-circle {
            width: 120px;
            height: 120px;
            object-fit: cover;
            border-radius: 50%;
            margin: 0 auto 15px auto;
            display: block;
            border: 4px solid #ffccd5;
            box-shadow: 0 8px 20px rgba(255, 112, 150, 0.25);
        }

        .letter-container {
            background: #fffdf9;
            border: 2px dashed #ffb3c6;
            border-radius: 20px;
            padding: 22px;
            position: relative;
            box-shadow: inset 0 0 15px rgba(255,200,210,0.2);
            margin: 15px 0;
        }
        .letter-container::before {
            content: '💌';
            position: absolute;
            top: -15px;
            left: 20px;
            font-size: 1.8rem;
        }
        .letter-paragraph {
            font-size: 0.92rem;
            line-height: 1.8;
            color: #5a435d;
            text-align: justify;
            margin-bottom: 15px;
        }
        .gratitude-list {
            background: #ffeef2;
            padding: 15px;
            border-radius: 15px;
            margin-top: 10px;
        }
        .gratitude-list h4 {
            font-size: 0.9rem;
            color: #ff477e;
            margin-bottom: 8px;
            font-family: 'Playfair Display', serif;
        }
        .gratitude-list ul {
            list-style: none;
            padding-left: 5px;
        }
        .gratitude-list li {
            font-size: 0.85rem;
            color: #6b5270;
            margin-bottom: 6px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .gift-box-content {
            display: flex;
            flex-direction: column;
            gap: 20px;
            margin: 15px 0;
        }

        .gift-media-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 15px;
        }

        .gift-media-card {
            background: #ffffff;
            border: 2px solid #ffccd5;
            border-radius: 20px;
            padding: 12px;
            text-align: center;
            box-shadow: 0 8px 20px rgba(255, 112, 150, 0.12);
            transition: 0.3s;
        }

        .gift-media-card:hover {
            transform: translateY(-4px);
            border-color: #ff477e;
        }

        .gift-media-card img {
            width: 100%;
            height: 140px;
            object-fit: cover;
            border-radius: 14px;
            margin-bottom: 8px;
        }

        .gift-media-card h3 {
            font-size: 0.9rem;
            color: #ff477e;
            font-family: 'Playfair Display', serif;
        }

        .sweet-quote-box {
            background: linear-gradient(135deg, #fff0f3, #ffe6ec);
            border: 2px dashed #ff7096;
            border-radius: 20px;
            padding: 20px;
            text-align: center;
            position: relative;
        }

        .sweet-quote-box p {
            font-size: 0.92rem;
            line-height: 1.7;
            color: #59405c;
            font-style: italic;
        }

        .sweet-quote-box span {
            display: block;
            margin-top: 10px;
            font-weight: 700;
            color: #ff477e;
            font-size: 0.85rem;
        }

        /* --- DESAIN KUE ULANG TAHUN 3D --- */
        .cake-container {
            position: relative;
            width: 220px;
            height: 160px;
            margin: 65px auto 20px auto;
        }

        .plate {
            width: 240px;
            height: 14px;
            background: #e2e2e2;
            border-radius: 10px;
            position: absolute;
            bottom: 0;
            left: -10px;
            box-shadow: 0 6px 12px rgba(0,0,0,0.15);
        }

        .layer {
            position: absolute;
            width: 180px;
            border-radius: 12px 12px 0 0;
            left: 20px;
        }

        .layer-bottom {
            height: 45px;
            background: #6d381e;
            bottom: 14px;
        }

        .layer-middle {
            height: 40px;
            background: #ffb3c6;
            bottom: 59px;
        }

        .layer-top {
            height: 38px;
            background: #ff7096;
            bottom: 99px;
        }

        .icing {
            position: absolute;
            top: 23px;
            left: 20px;
            width: 180px;
            height: 18px;
            background: #ffffff;
            border-radius: 12px 12px 10px 10px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
            z-index: 2;
        }

        .icing::after {
            content: '';
            position: absolute;
            top: 12px;
            left: 0;
            width: 100%;
            height: 12px;
            background: radial-gradient(circle, #ffffff 60%, transparent 65%);
            background-size: 18px 18px;
        }

        .cake-name {
            position: absolute;
            bottom: 66px;
            left: 0;
            width: 100%;
            text-align: center;
            font-family: 'Sacramento', cursive;
            font-size: 1.5rem;
            font-weight: bold;
            color: #ffffff;
            text-shadow: 1px 1px 3px rgba(0,0,0,0.3);
            z-index: 4;
            letter-spacing: 1px;
            pointer-events: none;
        }

        .topping-strawberry {
            position: absolute;
            font-size: 1.2rem;
            z-index: 5;
            top: -10px;
        }
        .berry-1 { left: 45px; }
        .berry-2 { right: 45px; }

        .candle {
            background: repeating-linear-gradient(45deg, #fff, #fff 5px, #ff477e 5px, #ff477e 10px);
            width: 12px;
            height: 36px;
            border-radius: 3px;
            position: absolute;
            top: -14px;
            left: 104px;
            cursor: pointer;
            z-index: 10;
        }

        .candle::before {
            content: '';
            position: absolute;
            top: -6px;
            left: 5px;
            width: 2px;
            height: 6px;
            background: #444;
        }

        .flame {
            position: absolute;
            background: #ff9d00;
            width: 14px;
            height: 22px;
            border-radius: 50% 50% 35% 35%;
            top: -26px;
            left: -1px;
            box-shadow: 0 0 12px #ff9d00, 0 0 20px #ff2a00;
            animation: flicker 0.6s infinite alternate ease-in-out;
            transform-origin: center bottom;
            transition: opacity 0.4s ease, transform 0.4s ease;
        }

        .flame.out {
            opacity: 0;
            transform: scale(0);
        }

        @keyframes flicker {
            0% { transform: rotate(-2deg) scale(1); box-shadow: 0 0 12px #ff9d00, 0 0 20px #ff2a00; }
            100% { transform: rotate(2deg) scale(1.1); box-shadow: 0 0 16px #ff9d00, 0 0 25px #ff2a00; }
        }

        .candle-hint {
            font-size: 0.85rem;
            color: #ff477e;
            font-weight: 600;
            margin-bottom: 15px;
            text-align: center;
            transition: all 0.3s ease;
        }

        .photo-album-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(130px, 1fr));
            gap: 15px;
            margin: 20px 0;
            justify-items: center;
        }

        .album-item {
            background: white;
            padding: 10px 10px 20px 10px;
            border-radius: 12px;
            box-shadow: 0 6px 15px rgba(255, 112, 150, 0.15);
            border: 2px solid #ffe3e9;
            width: 100%;
            max-width: 160px;
            transition: all 0.3s ease;
            position: relative;
        }

        .album-item:nth-child(odd) { transform: rotate(-2deg); }
        .album-item:nth-child(even) { transform: rotate(2deg); }

        .album-item:hover {
            transform: scale(1.05) rotate(0deg);
            z-index: 5;
            box-shadow: 0 10px 25px rgba(255, 112, 150, 0.3);
        }

        .album-item img {
            width: 100%;
            height: 130px;
            object-fit: cover;
            border-radius: 8px;
        }

        .album-item p {
            font-size: 0.75rem;
            color: #ff477e;
            text-align: center;
            margin-top: 8px;
            font-weight: 600;
            font-family: 'Playfair Display', serif;
        }

        #page-1 {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 60vh;
            text-align: center;
        }

        .password-input {
            padding: 14px 22px;
            font-size: 1rem;
            border: 2px solid var(--accent-pink);
            border-radius: 30px;
            outline: none;
            text-align: center;
            width: 260px;
            margin-bottom: 15px;
            background: #fff9fa;
            color: var(--text-color);
            transition: 0.3s;
        }

        .password-input:focus {
            border-color: var(--primary-color);
            box-shadow: 0 0 12px rgba(255, 112, 150, 0.3);
        }

        .error-msg {
            color: #ff3366;
            font-size: 0.85rem;
            margin-top: -8px;
            margin-bottom: 15px;
            display: none;
            font-weight: 500;
        }

        .btn {
            background: linear-gradient(135deg, #ff7096 0%, #ff477e 100%);
            color: white;
            border: none;
            padding: 12px 32px;
            font-size: 1rem;
            font-weight: 600;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 6px 20px rgba(255, 71, 126, 0.4);
            transition: all 0.3s ease;
        }

        .btn:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 10px 25px rgba(255, 71, 126, 0.6);
        }

        h1 {
            font-family: 'Playfair Display', serif;
            font-size: 2.2rem;
            color: #ff477e;
            margin-bottom: 10px;
        }

        p.subtitle {
            font-size: 0.95rem;
            margin-bottom: 20px;
            color: #7d5b82;
        }

        .gift-box-wrapper {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin: 20px 0;
        }

        .gift-item {
            background: #fff0f3;
            border: 2px dashed var(--primary-color);
            padding: 18px 15px;
            border-radius: 20px;
            cursor: pointer;
            transition: 0.3s;
            width: 48%;
            text-align: center;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
        }

        .gift-item:hover {
            transform: translateY(-5px) scale(1.03);
            background: #ffe3e9;
            box-shadow: 0 5px 15px rgba(255,112,150,0.3);
        }

        .gift-item span {
            font-size: 2.5rem;
            display: block;
            margin-bottom: 5px;
        }

        .gift-item small {
            font-size: 0.85rem;
            font-weight: 700;
            color: #ff477e;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .gift-item p {
            font-size: 0.78rem;
            color: #59405c;
            margin-top: 8px;
            font-weight: 500;
        }

        .reasons-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin: 20px 0;
        }

        .reason-box {
            background: linear-gradient(145deg, #fff0f3, #ffffff);
            padding: 18px;
            border-radius: 20px;
            text-align: center;
            border: 2px solid #ffccd5;
            font-size: 0.85rem;
            color: #6b5270;
            position: relative;
            transition: 0.3s;
            box-shadow: 0 5px 15px rgba(255,204,213,0.3);
        }

        .reason-box:hover {
            transform: translateY(-5px);
            border-color: var(--primary-color);
            box-shadow: 0 8px 20px rgba(255,112,150,0.25);
        }

        .reason-box b {
            display: block;
            color: #ff477e;
            margin-bottom: 5px;
            font-size: 0.95rem;
        }

        /* --- STYLING VIDEO HALAMAN 5 --- */
        .video-container {
            position: relative;
            width: 100%;
            padding-bottom: 56.25%; /* Rasio Aspek 16:9 */
            height: 0;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 8px 20px rgba(0,0,0,0.1);
            background: #000;
            margin: 15px 0;
            border: 3px solid #ffccd5;
        }

        .video-container video {
            position: absolute;
            top: 0; 
            left: 0;
            width: 100%; 
            height: 100%;
            object-fit: contain;
            border: none;
            outline: none;
        }

        .gallery {
            display: flex;
            gap: 15px;
            justify-content: center;
            margin: 15px 0;
            flex-wrap: wrap;
        }

        .polaroid {
            background: white;
            padding: 12px 12px 25px 12px;
            border-radius: 12px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.08);
            width: 140px;
            transform: rotate(-3deg);
            transition: 0.3s;
            border: 2px solid #fff0f3;
            position: relative;
        }
        .polaroid::before {
            content: '🎀';
            position: absolute;
            top: -10px;
            right: -5px;
            font-size: 1.2rem;
        }
        .polaroid:nth-child(even) { transform: rotate(3deg); }
        .polaroid:hover { transform: scale(1.08) rotate(0deg); z-index: 10; }

        .polaroid img {
            width: 100%;
            height: 110px;
            object-fit: cover;
            border-radius: 6px;
        }

        .polaroid span {
            display: block;
            font-size: 0.75rem;
            text-align: center;
            margin-top: 8px;
            font-family: 'Playfair Display', serif;
            color: #ff477e;
            font-weight: 600;
        }

        .fun-box {
            background: linear-gradient(135deg, #ffe6ec, #fff0f3);
            padding: 22px;
            border-radius: 25px;
            text-align: center;
            margin-top: 15px;
            border: 2px dashed var(--primary-color);
            box-shadow: inset 0 2px 10px rgba(255,112,150,0.1);
        }

        .btn-group {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 18px;
            position: relative;
            height: 55px;
        }

        .btn-yes {
            background-color: #4bb543;
            color: white;
            border: none;
            padding: 12px 28px;
            border-radius: 25px;
            cursor: pointer;
            font-weight: 600;
            box-shadow: 0 5px 15px rgba(75, 181, 67, 0.3);
        }

        .btn-no {
            background-color: #ff3366;
            color: white;
            border: none;
            padding: 12px 28px;
            border-radius: 25px;
            cursor: pointer;
            position: absolute;
            font-weight: 600;
            box-shadow: 0 5px 15px rgba(255, 51, 102, 0.3);
            transition: 0.1s ease-out;
        }

        .exit-card-content {
            text-align: center;
            padding: 10px 0;
        }

        .exit-icon {
            font-size: 3.5rem;
            margin-bottom: 10px;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        .exit-action-btns {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-top: 25px;
            align-items: center;
        }

        .btn-replay {
            background: linear-gradient(135deg, #ff7096, #ff477e);
            color: white;
            border: none;
            padding: 12px 30px;
            font-size: 0.95rem;
            font-weight: 600;
            border-radius: 50px;
            cursor: pointer;
            width: 100%;
            max-width: 280px;
            box-shadow: 0 5px 15px rgba(255, 71, 126, 0.3);
            transition: 0.3s;
        }

        .btn-replay:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(255, 71, 126, 0.5);
        }

        .btn-close-web {
            background: #f0f0f0;
            color: #6b5270;
            border: 2px solid #ffccd5;
            padding: 10px 25px;
            font-size: 0.88rem;
            font-weight: 600;
            border-radius: 50px;
            cursor: pointer;
            width: 100%;
            max-width: 280px;
            transition: 0.3s;
        }

        .btn-close-web:hover {
            background: #ffe6ec;
            color: #ff477e;
        }

        .nav-buttons {
            display: flex;
            justify-content: space-between;
            margin-top: 25px;
        }

        .btn-nav {
            background-color: #ffccd5;
            color: #59405c;
            border: none;
            padding: 10px 22px;
            font-size: 0.85rem;
            border-radius: 25px;
            cursor: pointer;
            font-weight: 600;
            transition: 0.2s;
        }
        .btn-nav:hover { background-color: var(--primary-color); color: white; }

        @media (max-width: 480px) {
            h1 { font-size: 1.8rem; }
            .card { padding: 25px 18px; }
            .reasons-grid { grid-template-columns: 1fr; }
            .gift-box-wrapper { flex-direction: column; align-items: center; }
            .gift-item { width: 100%; max-width: 280px; }
            .gift-media-grid { grid-template-columns: 1fr; }
            .photo-bg img { width: 70px !important; height: 70px !important; }
            .spotify-controls { flex-direction: column; gap: 10px; }
            .spotify-volume { margin-top: 5px; }
        }
    </style>
</head>
<body>
<!-- SOUND LATAR BELAKANG -->
<audio id="bg-sound" loop preload="auto">
    <source src="musik.mp3" type="audio/mp3">
</audio>
<!-- AUDIO SPOTIFY (HALAMAN 3) -->
<audio id="spotify-music" loop preload="auto">
    <source src="ssstik.io_1786760301077.mp3" type="audio/mp3">
</audio>
<!-- ANIMASI FOTO MELAYANG DI LATAR BELAKANG -->
<div class="photo-bg">
    <img src="foto 1.jpeg" alt="Bg Photo 1">
    <img src="foto 2.jpeg" alt="Bg Photo 2">
    <img src="foto 4.jpeg" alt="Bg Photo 3">
    <img src="foto 1.jpeg" alt="Bg Photo 4">
    <img src="foto 1.jpeg" alt="Bg Photo 5">
</div>
<!-- Latar Belakang Bunga/Kelopak Mengambang -->
<div class="floral-bg">
    <span>🎀✨❤️</span>
    <span>🌸💖🌸</span>
    <span>🎀✨❤️</span>
    <span>🌷</span>
    <span>💖✨</span>
</div>
<div class="container">
    <!-- HALAMAN 1 -->
    <div id="page-1" class="card active">
        <img src="foto 3.jpeg" alt="Special Gift" class="page-photo-circle">
        <h1>Hai, Sayang💖</h1>
        <p class="subtitle">Ayo masukan sandinya, cluenya tanggal jadian kita lengkap.</p>
        <input type="password" id="passcode-input" class="password-input" placeholder="Ketik Sandi Disini...">
        <div id="error-msg" class="error-msg">Ups, kodenya salah! Kamu lupa yaa</div>
        <button class="btn" onclick="checkPassword()">Open Sayang 🎀</button>
    </div>

    <!-- HALAMAN 2 -->
    <div id="page-2" class="card">
        <h2>Hari Spesial Kamu✨</h2>
        <p class="message-text">Hari ini adalah hari yang sangat istimewa buat kamu di bulan ini ... 💕</p>
        <div class="calendar-card-box">
            <div class="calendar-header-title">
                <span>September</span>
            </div>
            <div class="calendar-grid">
                <div class="day-header">Min</div>
                <div class="day-header">Sen</div>
                <div class="day-header">Sel</div>
                <div class="day-header">Rab</div>
                <div class="day-header">Kam</div>
                <div class="day-header">Jum</div>
                <div class="day-header">Sab</div>
                <div class="day-cell empty"></div>
                <div class="day-cell empty"></div>
                <div class="day-cell">1</div>
                <div class="day-cell">2</div>
                <div class="day-cell">3</div>
                <div class="day-cell">4</div>
                <div class="day-cell">5</div>
                <div class="day-cell">6</div>
                <div class="day-cell">7</div>
                <div class="day-cell circled">8</div>
                <div class="day-cell">9</div>
                <div class="day-cell">10</div>
                <div class="day-cell">11</div>
                <div class="day-cell">12</div>
                <div class="day-cell">13</div>
                <div class="day-cell">14</div>
                <div class="day-cell">15</div>
                <div class="day-cell">16</div>
                <div class="day-cell">17</div>
                <div class="day-cell">18</div>
                <div class="day-cell">19</div>
                <div class="day-cell">20</div>
                <div class="day-cell">21</div>
                <div class="day-cell">22</div>
                <div class="day-cell">23</div>
                <div class="day-cell">24</div>
                <div class="day-cell">25</div>
                <div class="day-cell">26</div>
                <div class="day-cell">27</div>
                <div class="day-cell">28</div>
                <div class="day-cell">29</div>
                <div class="day-cell">30</div>
                <div class="day-cell">31</div>
            </div>
        </div>
        <div class="sweet-quote-box" style="margin-top: 15px;">
            <p>"Hari di mana senyuman terindah dilahirkan ke dunia ini. Happy Birthday Sayang! 💖✨"</p>
        </div>
        <div class="nav-buttons">
            <button class="btn-nav" onclick="goToPage('page-1')">&larr; Back</button>
            <button class="btn-nav" onclick="goToPage('page-3')">Next &rarr;</button>
        </div>
    </div>

    <!-- HALAMAN 3 -->
    <div id="page-3" class="card">
        <img src="foto 5.jpeg" alt="Birthday Banner" class="page-photo-banner">
        <h2>Hore, Kadonya terbuka! 🎉</h2>
        <!-- SPOTIFY PLAYER CARD -->
        <div class="spotify-card">
            <div class="spotify-header">
                <div class="spotify-logo">
                    <svg viewBox="0 0 24 24">
                        <path d="M12 0C5.376 0 0 5.376 0 12s5.376 12 12 12 12-5.376 12-12S18.624 0 12 0zm5.521 17.34c-.24.359-.66.48-1.021.24-2.82-1.74-6.36-2.101-10.561-1.141-.418.122-.779-.179-.899-.539-.12-.421.18-.78.54-.9 4.56-1.021 8.52-.6 11.64 1.32.42.18.479.659.301 1.02zm1.44-3.3c-.301.42-.841.6-1.262.3-3.239-1.98-8.159-2.58-11.939-1.38-.479.12-1.02-.12-1.14-.6-.12-.48.12-1.021.6-1.141 C9.6 9.9 15 10.561 18.72 12.84c.361.181.54.78.241 1.2zm.12-3.36C15.24 8.4 8.82 8.16 5.16 9.301c-.6.18-.1.2-1.2-.419-.18-.6.42-1.2 1.02-1.38 4.26-1.26 11.28-1.02 15.72 1.62.54.3.719 1.02.419 1.56-.3.42-1.02.6-1.56.3z"/>
                    </svg>
                    <span>PLAYING FROM PLAYLIST</span>
                </div>
                <span class="spotify-like-btn" onclick="toggleLike(this)">💚</span>
            </div>
            <div class="spotify-body">
                <img src="foto 6.jpeg" alt="Album Cover" class="spotify-cover" id="spotify-cover">
                <div class="spotify-track-info">
                    <div class="spotify-track-title">Happy Birthday To You 💖</div>
                    <div class="spotify-artist">I Love You Forever • Acoustic</div>
                </div>
            </div>
            <!-- Progress Bar -->
            <div class="spotify-progress-container">
                <div class="spotify-progress-bar" id="spotify-progress-bar" onclick="seekAudio(event)">
                    <div class="spotify-progress-fill" id="spotify-progress-fill"></div>
                </div>
                <div class="spotify-time">
                    <span id="spotify-current-time">0:00</span>
                    <span id="spotify-duration-time">0:00</span>
                </div>
            </div>
            <!-- Controls -->
            <div class="spotify-controls">
                <div class="spotify-btn-group">
                    <button class="spotify-icon-btn">🔀</button>
                    <button class="spotify-icon-btn">⏮</button>
                    <button class="spotify-play-btn" id="play-pause-btn" onclick="toggleSpotifyMusic()">▶</button>
                    <button class="spotify-icon-btn">⏭</button>
                    <button class="spotify-icon-btn">🔁</button>
                </div>
                <div class="spotify-volume">
                    <span class="spotify-volume-icon">🔊</span>
                    <input type="range" class="spotify-volume-slider" id="volume-control" min="0" max="100" value="50" oninput="changeVolume(this.value)">
                </div>
            </div>
        </div>
        <p class="message-text">
            Selamat ulang tahun sayang, sosok paling spesial dalam hidup aku! 💐 Ada 2 kado spesial yang sudah aku siapkan. Pilih kado mana yang mau kamu buka dulu!
        </p>
        <div class="gift-box-wrapper">
            <div class="gift-item" onclick="goToPage('page-gift-1')">
                <span>💌</span>
                <small>Amplop Misteri</small>
                <p>"Buka ini dulu dong!"</p>
            </div>
            <div class="gift-item" onclick="goToPage('page-gift-2')">
                <span>🎁</span>
                <small>Kotak Kejutan</small>
                <p>"Buka yang ini aja!"</p>
            </div>
        </div>
        <div class="nav-buttons">
            <button class="btn-nav" onclick="goToPage('page-2')">&larr; Back</button>
            <button class="btn-nav" onclick="goToPage('page-4')">Next &rarr;</button>
        </div>
    </div>

    <!-- HALAMAN KADO 1 -->
    <div id="page-gift-1" class="card">
        <h2>💌 Surat Cinta</h2>
        <div class="letter-container">
            <p class="letter-paragraph">
                <b>Hai Cantik,</b><br>
                Selamat ulang tahun ya! Di hari yang indah ini, aku pengen nyampein betapa bersyukurnya aku bisa kenal dan berjalan bareng sosok sehebat kamu.
            </p>
            <p class="letter-paragraph">
                Terima kasih ya sudah selalu membagikan senyuman manis dan energi positif ke orang-orang di sekitarmu. Semoga di usia yang baru ini, setiap mimpi dan cita-cita yang kamu simpan dalam hati bisa terwujud satu per satu! ✨
            </p>
            <div class="gratitude-list">
                <h4>🌸 Hal Yang paling aku syukuri bersama kamu:</h4>
                <ul>
                    <li>💖 Senyumanmu yang selalu bisa bikin suasana hati tenang.</li>
                    <li>🌟 Kebaikan hatimu yang tulus ke siapa saja.</li>
                    <li>🍕 Sifat rewelmu yang ngerasa aku diperhatikan.</li>
                    <li>🍕 Ceritamu yang selalu membuat aku tersenyum.</li>
                </ul>
            </div>
        </div>
        <div class="nav-buttons">
            <button class="btn-nav" onclick="goToPage('page-3')">&larr; Back</button>
            <button class="btn-nav" onclick="goToPage('page-gift-2')">Next &rarr;</button>
        </div>
    </div>

    <!-- HALAMAN KADO 2 -->
    <div id="page-gift-2" class="card">
        <h2>Kue Ulang Tahun🎂</h2>
        <p class="message-text" style="font-size: 0.88rem; margin-bottom: 12px;">
            Tiup atau klik api lilinnya untuk mematikan lilin dan buat permintaan! ✨
        </p>
        <div class="cake-container">
            <div class="plate"></div>
            <div class="layer layer-bottom"></div>
            <div class="layer layer-middle"></div>
            <div class="layer layer-top">
                <span class="topping-strawberry berry-1">🍓</span>
                <span class="topping-strawberry berry-2">🍓</span>
            </div>
            <div class="cake-name">DIVA</div>
            <div class="icing"></div>
            <div class="candle" id="candle" onclick="blowCandle()">
                <div class="flame" id="flame"></div>
            </div>
        </div>
        <p id="candle-status" class="candle-hint">🔥 Ketuk/klik api lilin untuk meniupnya! 🔥</p>
        <div class="gift-box-content">
            <div class="gift-media-grid">
                <div class="gift-media-card">
                    <img src="foto 7.jpg" alt="Buket Bunga">
                    <h3>💐 Special Flower Bouquet For You 💐</h3>
                </div>
            </div>
            <div class="sweet-quote-box">
                <p>
                    "Seperti lilin di atas kue yang menerangi ruangan, dan bunga indah yang mekar di musim semi... Semoga hidupmu selalu dipenuhi oleh kehangatan, kebahagiaan tanpa batas, dan orang-orang yang tulus menyayangimu dan semoga diwujudkan semua wishlist serta mimpi-mimpimu 💖✨"
                </p>
                <span>Make a Wish & Enjoy Your Special Day! 🎂🌸</span>
            </div>
        </div>
        <div class="nav-buttons">
            <button class="btn-nav" onclick="goToPage('page-3')">&larr; Back</button>
            <button class="btn-nav" onclick="goToPage('page-4')">Next &rarr;</button>
        </div>
    </div>

    <!-- HALAMAN 4 -->
    <div id="page-4" class="card">
        <img src="foto 8.jpeg" alt="Special Reasons" class="page-photo-banner">
        <h2>Alasan Kenapa Kamu Istimewa 🌷</h2>
        <p class="message-text" style="font-size: 0.85rem; margin-bottom: 10px;">Dirangkum langsung dari kebun keimutan dunia:</p>
        <div class="reasons-grid">
            <div class="reason-box">
                <b>🍕 Menciptakan Ketenangan yang Sederhana</b>
               Bukan tentang kemewahan, melainkan tawanya dan keberadaannya yang selalu berhasil menenangkan badai pikirannya.
            </div>
            <div class="reason-box">
                <b>😂 Mewarnai hidup</b>
                Dengan bersama kamu aku tau bahwa hidup itu indah, lucu. dan penuh warna.
            </div>
            <div class="reason-box">
                <b>🔋 Good Energy</b>
                Punya aura positif (walaupun hobi mager kambuhan).
            </div>
            <div class="reason-box">
                <b>👑 Main Character</b>
                Hari ini dan selamanya, kamulah bintang utamanya!
            </div>
        </div>
        <div class="nav-buttons">
            <button class="btn-nav" onclick="goToPage('page-3')">&larr; Back</button>
            <button class="btn-nav" onclick="goToPage('page-photo-gallery')">Next &rarr;</button>
        </div>
    </div>

    <!-- HALAMAN FOTO GALLERY -->
    <div id="page-photo-gallery" class="card">
        <h2>📸 Galeri Kenangan Indah</h2>
        <p class="message-text" style="font-size: 0.85rem; margin-bottom: 10px;">
            Kumpulan momen manis yang selalu bikin senyum-senyum sendiri 🌸✨
        </p>
        <div class="photo-album-grid">
            <div class="album-item">
                <img src="foto 9.jpeg" alt="Photo 1">
                <p>Sweet Smile 💖</p>
            </div>
            <div class="album-item">
                <img src="foto 10.jpeg" alt="Photo 2">
                <p>Pretty Day 🌷</p>
            </div>
            <div class="album-item">
                <img src="foto 11.jpeg" alt="Photo 3">
                <p>Sunshine Girl ☀️</p>
            </div>
            <div class="album-item">
                <img src="foto 12.jpeg" alt="Photo 4">
                <p>Happy Vibes 🎉</p>
            </div>
        </div>
        <div class="nav-buttons">
            <button class="btn-nav" onclick="goToPage('page-4')">&larr; Back</button>
            <button class="btn-nav" onclick="goToPage('page-5')">Next &rarr;</button>
        </div>
    </div>

    <!-- HALAMAN 5 (VIDEO DIUPDATE DENGAN VIDEO BARU) -->
    <div id="page-5" class="card">
        <img src="foto 14.jpeg" alt="Gallery Header" class="page-photo-banner">
        <h2>🎥 Kenangan Manis & Video</h2>
        <div class="video-container">
            <video id="page5-video" controls playsinline webkit-playsinline preload="metadata" poster="foto 1.jpeg">
                <source src="video.mp4" type="video/MP4">
                Maaf, browser kamu tidak mendukung pemutaran video ini.
            </video>
        </div>
        <div class="gallery" id="photo-gallery">
        </div>
        <div class="nav-buttons">
            <button class="btn-nav" onclick="goToPage('page-photo-gallery')">&larr; Back</button>
            <button class="btn-nav" onclick="goToPage('page-6')">Next &rarr;</button>
        </div>
    </div>

    <!-- HALAMAN 6 -->
    <div id="page-6" class="card">
        <img src="foto 13.jpeg" alt="Celebration" class="page-photo-banner">
        <h2>Doa & Pertanyaan Spesial 🌸</h2>
        <p class="message-text">
            Semoga di usia yang baru ini, kebahagiaanmu mekar selamanya seperti bunga di musim semi, rezekinya lancar, dan semua impianmu tercapai satu persatu. Aamiin! 🥳💐
        </p>
        <div class="fun-box">
            <p style="font-size: 0.95rem; font-weight: 600; color: #ff477e;">I LOVE YOU Sayang❤️, kamu sayang kan sama aku? 🥺❤️</p>
            <div class="btn-group">
                <button class="btn-yes" onclick="triggerCelebration()">Sayang Banget! 🥰</button>
                <button class="btn-no" id="btn-run" onmouseover="moveButton()" onclick="moveButton()">Enggak 😜</button>
            </div>
        </div>
        <div class="nav-buttons" style="margin-top: 20px;">
            <button class="btn-nav" onclick="goToPage('page-5')">&larr; Back</button>
            <button class="btn-nav" style="background-color: #ff477e; color: white;" onclick="goToPage('page-exit')">Selesai 🏁</button>
        </div>
    </div>

    <!-- HALAMAN EXIT -->
    <div id="page-exit" class="card">
        <div class="exit-card-content">
            <div class="exit-icon">💖✨🌸</div>
            <h2>Terima Kasih Ya!</h2>
            <p class="message-text" style="font-size: 0.92rem; margin-top: 10px;">
                Makasih udah menyempatkan waktu buat buka hadiah sederhana ini. maaf cuma ini yang baru bisa aku siapin. insha allah pas aku pulang aku ada hadiah buat kamu. Semoga harimu selalu penuh dengan tawa dan kebahagiaan!
            </p>
            <div class="sweet-quote-box" style="margin: 20px 0; background: #fff0f3;">
                <p style="font-size: 0.88rem; color: #ff477e; font-weight: 600;">
                    "Setiap detik bersamamu adalah momen indah yang selalu aku syukuri. Happy Birthday Once Again! 🥳🎂"
                </p>
            </div>
            <div class="exit-action-btns">
                <button class="btn-replay" onclick="goToPage('page-1')">🔄 Ulangi Dari Awal</button>
                <button class="btn-close-web" onclick="finishSession()">👋 Selesai & Keluar</button>
            </div>
        </div>
    </div>
</div>

<script>
    const SECRET_CODE = "27102024";

    // --- KONTROL SOUND LATAR BELAKANG (BGM) ---
    const bgSound = document.getElementById('bg-sound');
    bgSound.volume = 0.4;

    function startBGSound() {
        if (bgSound.paused) {
            bgSound.play().catch(err => {
                console.log("Autoplay diblokir oleh browser:", err);
            });
        }
    }

    window.addEventListener('DOMContentLoaded', () => {
        startBGSound();
    });
    document.addEventListener('click', () => {
        startBGSound();
    }, { once: true });

    // --- KONTROL LAGU SPOTIFY (HALAMAN 3) ---
    const spotifyMusic = document.getElementById('spotify-music');
    const cover = document.getElementById('spotify-cover');
    const fill = document.getElementById('spotify-progress-fill');
    const currentTimeElem = document.getElementById('spotify-current-time');
    const durationTimeElem = document.getElementById('spotify-duration-time');
    const playBtn = document.getElementById('play-pause-btn');

    spotifyMusic.volume = 0.5;

    function playSpotifyMusic() {
        spotifyMusic.play().then(() => {
            if (playBtn) playBtn.textContent = "⏸";
            if (cover) cover.classList.add('playing');
            bgSound.pause();
        }).catch(err => {
            console.log("Error memutar audio Spotify:", err);
        });
    }

    function pauseSpotifyMusic() {
        spotifyMusic.pause();
        if (playBtn) playBtn.textContent = "▶";
        if (cover) cover.classList.remove('playing');
        bgSound.play().catch(err => {
            console.log("Error melanjutkan BGM:", err);
        });
    }

    function toggleSpotifyMusic() {
        if (spotifyMusic.paused) {
            playSpotifyMusic();
        } else {
            pauseSpotifyMusic();
        }
    }

    // --- KONTROL & DETEKSI ERROR VIDEO HALAMAN 5 ---
    const page5Video = document.getElementById('page5-video');
    const videoErrorHint = document.getElementById('video-error-hint');

    if (page5Video) {
        page5Video.addEventListener('error', () => {
            if (videoErrorHint) videoErrorHint.style.display = 'block';
            console.log("Error: File video 'Video 2.mp4' tidak ditemukan atau format tidak didukung.");
        });

        page5Video.addEventListener('play', () => {
            if (!bgSound.paused) bgSound.pause();
            if (!spotifyMusic.paused) {
                spotifyMusic.pause();
                if (playBtn) playBtn.textContent = "▶";
                if (cover) cover.classList.remove('playing');
            }
        });

        page5Video.addEventListener('pause', () => {
            const activeCard = document.querySelector('.card.active');
            if (activeCard && activeCard.id === 'page-5') {
                if (spotifyMusic.paused) {
                    bgSound.play().catch(err => {
                        console.log("Gagal melanjutkan BGM:", err);
                    });
                }
            }
        });
    }

    function checkPassword() {
        const inputVal = document.getElementById('passcode-input').value;
        const errorMsg = document.getElementById('error-msg');

        if (inputVal === SECRET_CODE) {
            goToPage('page-2');
        } else {
            errorMsg.style.display = 'block';
            document.getElementById('passcode-input').value = '';
        }
    }

    document.getElementById('passcode-input').addEventListener('keypress', function(e) {
        if (e.key === 'Enter') {
            checkPassword();
        }
    });

    function goToPage(pageId) {
        if (page5Video && !page5Video.paused) {
            page5Video.pause();
        }

        const cards = document.querySelectorAll('.card');
        cards.forEach(card => {
            card.classList.remove('active');
            card.style.display = 'none';
        });

        const target = document.getElementById(pageId);
        target.style.display = 'block';
        setTimeout(() => {
            target.classList.add('active');
        }, 50);

        if (pageId === 'page-1') {
            startBGSound();
        }

        if (pageId !== 'page-3' && !spotifyMusic.paused) {
            pauseSpotifyMusic();
        }

        if (['page-2', 'page-3', 'page-gift-1', 'page-gift-2', 'page-photo-gallery', 'page-exit'].includes(pageId)) {
            triggerConfetti();
        }
    }

    function changeVolume(val) {
        spotifyMusic.volume = val / 100;
    }

    function toggleLike(elem) {
        elem.textContent = elem.textContent === '💚' ? '🤍' : '💚';
    }

    spotifyMusic.addEventListener('timeupdate', () => {
        if (spotifyMusic.duration) {
            const percent = (spotifyMusic.currentTime / spotifyMusic.duration) * 100;
            fill.style.width = percent + '%';
            currentTimeElem.textContent = formatTime(spotifyMusic.currentTime);
            durationTimeElem.textContent = formatTime(spotifyMusic.duration);
        }
    });

    function seekAudio(e) {
        const progressBar = document.getElementById('spotify-progress-bar');
        const clickX = e.offsetX;
        const width = progressBar.clientWidth;
        spotifyMusic.currentTime = (clickX / width) * spotifyMusic.duration;
    }

    function formatTime(seconds) {
        const mins = Math.floor(seconds / 60);
        const secs = Math.floor(seconds % 60);
        return `${mins}:${secs < 10 ? '0' : ''}${secs}`;
    }

    let isFlameOut = false;

    function blowCandle() {
        const flame = document.getElementById('flame');
        const statusText = document.getElementById('candle-status');

        if (!isFlameOut) {
            flame.classList.add('out');
            isFlameOut = true;
            statusText.innerHTML = "✨ Hore! Lilin berhasil ditiup! Semoga semua kebaikan menyertaimu 💖✨";
            statusText.style.color = "#4bb543";

            if (typeof confetti === 'function') {
                confetti({
                    particleCount: 100,
                    spread: 80,
                    origin: { y: 0.5 },
                    colors: ['#ff477e', '#ffccd5', '#ffd166', '#06d6a0']
                });
            }
        } else {
            flame.classList.remove('out');
            isFlameOut = false;
            statusText.innerHTML = "🔥 Ketuk/klik api lilin untuk meniupnya! 🔥";
            statusText.style.color = "#ff477e";
        }
    }

    let escapeCount = 0;
    const escapeTexts = ["Enggak 😜", "Eits, kabur!", "Kejar dong 😋", "Yakin gak sayang?", "Pencet yang hijau aja!"];

    function moveButton() {
        const btnNo = document.getElementById('btn-run');
        const randomX = Math.floor(Math.random() * 160) - 80;
        const randomY = Math.floor(Math.random() * 70) - 35;
        btnNo.style.transform = `translate(${randomX}px, ${randomY}px)`;
        escapeCount = (escapeCount + 1) % escapeTexts.length;
        btnNo.textContent = escapeTexts[escapeCount];
    }

    function triggerCelebration() {
        confetti({
            particleCount: 200,
            spread: 120,
            origin: { y: 0.6 },
            colors: ['#ff477e', '#ff7096', '#ffccd5', '#4bb543', '#ffe6ec']
        });
        alert("Yey! Aku juga sayang banget sama kamu! ❤️✨ Makasih ya udah jadi bagian terindah dalam hidupku! 🌸🥳");
        goToPage('page-exit');
    }

    function triggerConfetti() {
        confetti({
            particleCount: 70,
            spread: 60,
            origin: { y: 0.6 },
            colors: ['#ff477e', '#ffb3c6', '#ff7096']
        });
    }

    function finishSession() {
        if (page5Video) page5Video.pause();
        pauseSpotifyMusic();
        bgSound.pause();
        alert("Terima kasih sudah berkunjung! Kamu bisa menutup tab browser ini sekarang 🌸✨");
    }
</script>
</body>
</html>
