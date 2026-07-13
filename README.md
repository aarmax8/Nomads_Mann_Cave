# Nomads_Mann_Cave
drink menu for the Mann Cave
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>DILLIGAF Menu Studio</title>

    <!-- iOS full-screen web app capabilities -->
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-title" content="Nomad's">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <link rel="apple-touch-icon" href="https://raw.githubusercontent.com/aarmax8/Nomads/b15a4394afade6bb543c1ece00102771641d1c82/Nicon5.png">
    
    <!-- External stylesheet and icon CDNs -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Black+Ops+One&family=Cinzel:wght@400;700&family=IM+Fell+DW+Pica&family=Roboto+Condensed:wght@700&family=Rye&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    
    <style>
        html, body {
            overscroll-behavior-y: contain;
            overflow: hidden;
            height: 100vh;
            height: -webkit-fill-available; 
            width: 100%;
            margin: 0;
            padding: 0;
            background-image: url('https://raw.githubusercontent.com/aarmax8/Nomads/c81556a569470611da64fb23e311817602720d95/pittsburghbridge.jpg');
            background-size: cover;
            background-position: center 85%;
            background-color: #000;
        }
        
        .app-container {
            display: flex;
            flex-direction: column;
            height: 100vh;
            height: -webkit-fill-available; 
            width: 100%;
            background-color: transparent;
            box-sizing: border-box;
        }

        header {
            flex-shrink: 0;
            position: relative;
            height: calc(110px + env(safe-area-inset-top));
            z-index: 10;
            width: 100%;
            box-sizing: border-box;
        }
        
        main {
            flex-grow: 1;
            z-index: 1; 
            min-height: 0;
            display: flex;
            flex-direction: column; 
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            position: relative;
        } 

        #header-logo-image {
            width: 100%;
            height: 100%;
            object-fit: fill; 
            position: absolute;
            top: 0;
            bottom: 0;
            left: 0;
            z-index: 1;
        }

        #header-logo-container {
            max-width: 1200px;
            margin-left: auto;
            margin-right: auto;
            position: relative;
            height: 100%;
        }

        /* Glint headlight effect on the header logo */
        #header-logo-container::after {
            content: '';
            position: absolute;
            top: 80%; 
            left: -150%; 
            width: 200px; 
            height: 200px; 
            margin-top: -100px; 
            background: radial-gradient(ellipse at center, 
                rgba(255, 255, 255, 0.3) 0%, 
                rgba(255, 255, 255, 0.05) 50%, 
                rgba(255, 255, 255, 0) 70% 
            );
            border-radius: 50%; 
            filter: blur(20px); 
            animation: glint-effect 7s infinite linear; 
            z-index: 2; 
        }

        @keyframes glint-effect {
            100% { left: 150%; }
        }
        
        #action-bar {
            flex-shrink: 0;
            height: 70px;
            padding: 0 0.5rem;
            box-sizing: border-box;
            background: linear-gradient(to bottom, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.95) 100%);
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.3);
            display: flex;
            justify-content: space-evenly;
            align-items: center;
            z-index: 20; 
        }

        .footer-btn {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            background: transparent;
            border: none;
            color: #ffffff; 
            padding: 0.25rem;
            border-radius: 0.5rem;
            cursor: pointer;
            transition: all 0.2s ease;
            gap: 0.1rem;
            font-size: 0.75rem;
            width: 65px; 
            line-height: 1.2;
            text-shadow: 0 1px 2px rgba(0,0,0,0.9);
        }
        .footer-btn i {
            font-size: 1.25rem;
            margin-bottom: 0.1rem;
            color: #ffffff;
            filter: drop-shadow(0 1px 2px rgba(0,0,0,0.9));
        }
        .footer-btn:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }

        #action-bar .footer-btn {
            width: 80px;
        }
        #action-bar .footer-btn i {
            font-size: 1.5rem;
            margin-bottom: 0.2rem;
        }
        #action-bar .footer-btn span {
            font-size: 0.8rem;
            font-weight: 700;
        }

        #action-bar .footer-btn.is-active-filter {
            color: #f59e0b; 
        }
        #action-bar .footer-btn.is-active-filter i {
            color: #f59e0b; 
        }
        
        #action-bar #action-favorites-btn.is-active {
            color: #f59e0b;
        }
        #action-bar #action-favorites-btn.is-active i {
            color: #f59e0b;
        }
        
        #action-bar .footer-btn:not(#action-favorites-btn) {
             color: #f59e0b;
        }
        #action-bar .footer-btn:not(#action-favorites-btn) i {
             color: #f59e0b;
        }
        
        /* Core carousel mode (Mobile default) */
        .carousel-view {
            display: flex; 
            gap: 1.5rem; 
            overflow-x: auto; 
            scroll-snap-type: x mandatory; 
            scroll-behavior: smooth; 
            scroll-padding: 1rem; 
            -webkit-overflow-scrolling: touch; 
            padding: 1rem 0;
            flex-grow: 1;
            min-height: 0; 
            box-sizing: border-box; 
        }

        /* Responsive Grid Layout (Desktop/Wide-screen mode) */
        .grid-view {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 1.5rem;
            overflow-y: auto;
            padding: 1.5rem;
            flex-grow: 1;
            min-height: 0;
            box-sizing: border-box;
        }

        #menu-grid.disable-animation .drink-card-inner {
            transition: none !important;
        }
        
        #menu-grid::-webkit-scrollbar { 
            width: 8px; 
            height: 8px; 
        }
        #menu-grid::-webkit-scrollbar-track {
            background: rgba(0,0,0,0.5); 
            border-radius: 4px;
        }
        #menu-grid::-webkit-scrollbar-thumb {
            background-color: #f59e0b;
            border-radius: 4px;
            border: 2px solid rgba(0,0,0,0.5); 
        }
        #menu-grid::-webkit-scrollbar-thumb:hover {
            background-color: #fbbf24; 
        }
        #menu-grid { 
            scrollbar-width: thin;
            scrollbar-color: #f59e0b rgba(0,0,0,0.5);
        }

        /* Drink Card Styling */
        .drink-card {
            perspective: 1500px;
            background-color: transparent; 
            transition: opacity 0.3s, transform 0.3s;
            position: relative; 
            height: 480px;
            content-visibility: auto; 
            contain-intrinsic-size: 320px 480px; 
            contain: layout style;
        }

        /* Carousel cards alignments mapping */
        .carousel-view .drink-card {
            flex: 0 0 80%; 
            scroll-snap-align: center; 
            margin-left: auto;
            margin-right: auto;
        }

        .carousel-view > .drink-card:first-child {
             margin-left: calc((100% - 80%) / 2); 
        }
        .carousel-view > .drink-card:last-child {
             margin-right: calc((100% - 80%) / 2); 
        }

        @media (min-width: 640px) { 
            .carousel-view .drink-card { flex-basis: 60%; }
            .carousel-view > .drink-card:first-child { margin-left: calc((100% - 60%) / 2); }
            .carousel-view > .drink-card:last-child { margin-right: calc((100% - 60%) / 2); }
        } 
        @media (min-width: 1024px) { 
            .carousel-view .drink-card { flex-basis: 40%; }
            .carousel-view > .drink-card:first-child { margin-left: calc((100% - 40%) / 2); }
            .carousel-view > .drink-card:last-child { margin-right: calc((100% - 40%) / 2); }
        } 

        .drink-card-inner {
            position: relative; 
            width: 100%; 
            height: 100%;
            transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1), box-shadow 0.4s ease-in-out;
            transform-style: preserve-3d;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.5); 
            border-radius: 0.75rem;
        }

        .drink-card.is-flipped .drink-card-inner { 
            transform: rotateY(180deg); 
        }
        
        .drink-card.is-active .drink-card-inner {
             box-shadow: 0 0 25px 8px rgba(45, 212, 191, 0.5);
        }
        .drink-card.is-active.is-flipped .drink-card-inner {
             box-shadow: 0 0 25px 8px rgba(245, 158, 11, 0.5);
        }
        .drink-card.is-highlighted .drink-card-inner {
             box-shadow: 0 0 30px 10px rgba(245, 158, 11, 0.8);
        }
        
        .drink-card-front, .drink-card-back {
            position: absolute; 
            width: 100%; 
            height: 100%;
            -webkit-backface-visibility: hidden; 
            backface-visibility: hidden;
            display: flex; 
            flex-direction: column; 
            overflow: hidden; 
            border-radius: 0.75rem;
        }

        /* --- CARD FRONT (Real/Common Cocktail info) --- */
        .drink-card-front {
            background-image: linear-gradient(145deg, rgba(30, 20, 20, 0.9) 0%, rgba(15, 10, 10, 0.95) 100%), url('https://raw.githubusercontent.com/aarmax8/Nomads/639ee0ed0a332926ddf78c332e7c114a32af99ab/leather%20background.jpg?raw=true');
            background-size: cover;
            background-position: center;
            border: 2px solid #2dd4bf; 
        }
        
        .card-header-front {
            position: relative; 
            padding: 0.75rem 3.5rem 0.5rem 1.25rem; 
            background: transparent; 
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            flex-shrink: 0;
        }

        .recipe-content { 
            flex-grow: 1; 
            overflow-y: auto; 
            padding: 0.5rem 1.25rem; 
            min-height: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        .recipe-content::-webkit-scrollbar { width: 4px; }
        .recipe-content::-webkit-scrollbar-thumb { background-color: #2dd4bf; border-radius: 4px; }

        .recipe-list-front { list-style: none; padding: 0; }
        .recipe-list-front li {
            display: flex; 
            align-items: center; 
            font-family: 'Roboto Condensed', sans-serif;
            font-size: 1rem; 
            line-height: 1.35; 
            letter-spacing: 0.02em; 
            margin-bottom: 0.4rem; 
            color: #f3f4f6; 
        }
        .recipe-list-front li i { 
            width: 24px; 
            text-align: center; 
            margin-right: 0.75rem; 
            font-size: 1.1rem; 
        }

        /* Pour Option Badges Area */
        .card-pour-options {
            padding: 0.5rem 1.25rem;
            background: rgba(0, 0, 0, 0.3);
            border-top: 1px solid rgba(255, 255, 255, 0.05);
            font-family: 'Roboto Condensed', sans-serif;
            font-size: 0.8rem;
        }

        .card-pour-badge {
            display: inline-block;
            padding: 0.15rem 0.4rem;
            background: rgba(45, 212, 191, 0.15);
            border: 1px solid rgba(45, 212, 191, 0.4);
            color: #2dd4bf;
            border-radius: 0.25rem;
            margin-right: 0.25rem;
            margin-top: 0.25rem;
            font-weight: 700;
        }

        .card-footer {
            padding: 0;
            flex-shrink: 0;
            border-top: none;
            background: transparent;
        }
        
        .card-hook-tagline {
            text-align: center; 
            font-size: 1.1rem; 
            line-height: 1.4;
            color: #2dd4bf;
            text-shadow: 0 0 8px rgba(45, 212, 191, 0.7); 
            padding: 0.5rem 1.25rem; 
            font-family: 'Cinzel', serif;
            letter-spacing: 0.03em; 
            border-top: 1px solid rgba(255, 255, 255, 0.1); 
        }

        /* --- STORY CARD BACK (Thematic names & lore) --- */
        .drink-card-back {
            transform: rotateY(180deg); 
            background-color: #0c0a09; 
            border: 2px solid #b45309; 
            color: #f3f4f6;
            position: relative;
            display: flex;
            flex-direction: column;
            justify-content: flex-end; 
            
            --bg-image: none;
            background-image: 
                linear-gradient(to bottom, rgba(12, 10, 9, 0.8) 0%, transparent 20%), 
                linear-gradient(to top, rgba(12, 10, 9, 1) 0%, rgba(12, 10, 9, 0.9) 30%, transparent 60%),
                var(--bg-image);

            background-position: center, center, top;
            background-repeat: no-repeat;
            background-size: 100% 100%, 100% 100%, cover;
        }

        .card-back-content {
            padding: 0 1.25rem;
            flex-grow: 0; 
            display: flex; 
            flex-direction: column;
            position: relative;
            z-index: 2;
        }

        .story-text {
            font-family: 'IM Fell DW Pica', serif;
            font-style: italic;
            text-align: justify;
            font-size: 1.15rem;
            line-height: 1.5;
            color: #f3f4f6; 
            text-shadow: 1px 1px 3px rgba(0,0,0,0.9); 
            max-height: 160px;
            overflow-y: auto;
            padding-right: 0.5rem; 
        }
        
        .story-text::-webkit-scrollbar { width: 4px; }
        .story-text::-webkit-scrollbar-thumb { background-color: #b45309; border-radius: 4px; }
        
        .no-image .card-back-content {
            margin-top: 0;
            justify-content: center;
            max-height: 100%;
        }
        .no-image {
             background-image: none;
        }
        .card-footer-back {
             padding: 0.5rem 0.75rem;
             background: rgba(0,0,0,0.5);
             border-top: 2px double rgba(180, 83, 9, 0.5);
             font-style: normal;
             display: flex;
             justify-content: center;
             align-items: center;
             min-height: 60px;
             font-family: 'Cinzel', serif;
             font-size: 1.25rem;
             color: #fbbf24;
             text-shadow: 0 0 8px rgba(245, 158, 11, 0.8);
             z-index: 2; 
             flex-shrink: 0; 
        }

        /* Favorite Action Buttons */
        .favorite-btn {
            position: absolute;
            z-index: 10;
            background: rgba(0,0,0,0.6);
            border: 1px solid rgba(255,255,255,0.25);
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.2s ease;
            transform: translateZ(0); 
        }
        .is-flipped .drink-card-front .favorite-btn {
            display: none;
        }
        .drink-card-front .favorite-btn {
            top: 0.75rem; 
            right: 0.75rem;
        }
        .favorite-btn:hover {
            transform: scale(1.1);
            background: rgba(0,0,0,0.8);
        }
        .favorite-btn .fa-heart {
            font-size: 1.2rem;
            color: #9ca3af; 
            transition: all 0.2s ease;
        }
        .favorite-btn.is-favorite .fa-heart {
            color: #f59e0b;
            text-shadow: 0 0 8px rgba(245, 158, 11, 0.7);
        }

        #favorites-list-container .favorite-item {
            display: flex;
            align-items: center;
            padding: 0.75rem 1rem;
            background: rgba(245, 158, 11, 0.05);
            border: 1px solid rgba(245, 158, 11, 0.2);
            border-radius: 0.5rem;
            cursor: pointer;
            transition: background-color 0.2s ease;
        }
        #favorites-list-container .favorite-item:hover {
            background: rgba(245, 158, 11, 0.15);
        }
        
        .drink-card.is-unavailable { opacity: 0.35; pointer-events: none; }
        
        .drink-card-title {
            font-size: 1.85rem; 
            line-height: 1.2; 
            color: #f59e0b; 
            text-align: center;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.8), 0 0 10px rgba(245, 158, 11, 0.5);
            padding-bottom: 0.25rem; 
        }
        .drink-card[data-is-barcode="true"] .drink-card-title {
            font-family: 'Cinzel', serif;
            font-size: 1.75rem;
        }

        .drink-card[data-is-barcode="true"] .drink-card-front {
            background-color: #0a0a0a;
            border: 3px double #444444;
            box-shadow: 0 8px 24px rgba(0,0,0,0.8);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center; 
            padding: 1rem;
            gap: 1rem;
        }
        .drink-card[data-is-barcode="true"] img {
            width: 100%;
            border-radius: 0.5rem;
            object-fit: contain;
            max-height: 60%;
        }

        #app-footer {
            position: relative; 
            flex-shrink: 0; 
            z-index: 50;
            padding-bottom: calc(env(safe-area-inset-bottom) * 0.6 + 6px);
            padding-top: 10px;
            min-height: calc(50px + 10px + (env(safe-area-inset-bottom) * 0.6));
            box-sizing: border-box; 
            background-color: rgba(15, 15, 15, 0.5);
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            box-shadow: 0 -4px 15px rgba(0, 0, 0, 0.5);
            display: flex;
            justify-content: center;
            align-items: center; 
            width: 100%;
            margin: 0;
        }

        #footer-content {
            width: 100%;
            max-width: 1200px;
            height: 50px;
            display: flex;
            justify-content: space-evenly;
            align-items: center;
        }
        
        #app-footer #scroll-prev-btn i,
        #app-footer #scroll-prev-btn span,
        #app-footer #scroll-next-btn i,
        #app-footer #scroll-next-btn span {
            color: #2dd4bf;
        }
        
        #app-footer #scroll-home-btn {
            color: #2dd4bf;
        }
        #app-footer #scroll-home-btn i {
            color: #2dd4bf;
        }
        
        #splash-screen {
            position: fixed;
            inset: 0;
            height: 100%;
            height: -webkit-fill-available;
            z-index: 1000;
            background-color: #000;
            background-image: linear-gradient(to bottom, transparent 85%, #000 95%), url('https://raw.githubusercontent.com/aarmax8/Nomads/ac96a3e89384bc4f8a4feefe4af617c47d901a0e/splash.jpg');
            background-size: cover;
            background-position: center;
            display: flex;
            flex-direction: column;
            justify-content: flex-end; 
            align-items: center; 
            cursor: pointer;
            transition: opacity 0.7s ease-out;
        }
        #splash-screen.is-hidden {
            opacity: 0;
            pointer-events: none;
        }
        .splash-text {
            font-family: 'Cinzel', serif;
            font-size: 1.25rem;
            color: #e5e7eb;
            text-shadow: 0 0 15px rgba(255, 255, 255, 0.7), 0 0 5px rgba(0, 0, 0, 1);
            background-color: rgba(0,0,0,0.6);
            padding: 0.75rem 1.75rem;
            border-radius: 9999px;
            border: 1px solid rgba(255,255,255,0.25);
            animation: pulse-text 2.5s infinite;
            margin-bottom: calc(15vh + env(safe-area-inset-bottom));
        }
        @keyframes pulse-text {
            0%, 100% { transform: scale(1); opacity: 0.9; }
            50% { transform: scale(1.04); opacity: 1; }
        }
        
        /* Filter Pills for modal queries */
        .filter-pill {
            background-color: rgba(255, 255, 255, 0.05); 
            border: 1px solid rgba(255, 255, 255, 0.2);
            color: #d1d5db; 
            padding: 0.4rem 0.85rem;
            border-radius: 9999px; 
            cursor: pointer;
            transition: all 0.2s ease;
            font-family: 'Roboto Condensed', sans-serif;
            font-weight: 700;
            font-size: 0.875rem; 
            flex-shrink: 0;
            text-shadow: 0 0 5px rgba(0,0,0,0.5);
        }
        .filter-pill:hover {
            background-color: rgba(255, 255, 255, 0.15);
        }
        .filter-pill.is-active {
            background-color: #f59e0b; 
            border: 1px solid #fbbf24; 
            color: #111827; 
            box-shadow: 0 0 10px rgba(245, 158, 11, 0.7); 
            transform: scale(1.05);
            text-shadow: none;
        }

        .modal-panel {
            background-image: 
                linear-gradient(to top, rgba(17, 17, 17, 0.98) 0%, rgba(17, 17, 17, 0.75) 30%, rgba(17, 17, 17, 0.95) 100%), 
                url('https://raw.githubusercontent.com/aarmax8/Nomads/c494fdd916aac964350c8174aa9fd9a37f7f09b7/thumbnail_IMG_8263.jpg?raw=true');
            background-size: cover;
            background-position: center;
            border: 2px solid #2dd4bf; 
        }
        
        /* Table of Contents layouts */
        .barcode-back-content {
            padding: 1.5rem; 
            flex-grow: 1; 
            overflow-y: auto; 
            display: flex;
            flex-direction: column;
            gap: 0.5rem; 
        }
        .barcode-back-content::-webkit-scrollbar { width: 6px; }
        .barcode-back-content::-webkit-scrollbar-thumb { background-color: #f59e0b; border-radius: 3px; }

        .toc-item {
            padding: 0.75rem 1rem; 
            border-radius: 0.5rem; 
            background: rgba(0, 0, 0, 0.5); 
            cursor: pointer;
            text-align: center;
            font-size: 1.1rem; 
            font-weight: 700;
            line-height: 1.2;
            transition: background-color 0.2s, transform 0.1s;
            border: 1px solid; 
        }

        .toc-item:hover {
            background-color: rgba(0, 0, 0, 0.75);
            transform: scale(1.02);
        }
        .toc-category-header {
            font-family: 'Rye', serif;
            font-size: 1.4rem;
            color: #2dd4bf; 
            text-align: center;
            padding: 0.5rem 0;
            margin-top: 1rem;
            border-bottom: 2px solid #2dd4bf;
        }

        /* Focused Image Alignments */
        .drink-card[data-name="Mechanic"] .drink-card-back { background-position: center, center, right; }
        .drink-card[data-name="Dirty Martini"] .drink-card-back { background-position: center, center, right; }
        .drink-card[data-name="Caramel Apple Cruiser"] .drink-card-back,
        .drink-card[data-name="Statesman"] .drink-card-back { background-position: center, center, right; }
        .drink-card[data-name="Kraken's Grip"] .drink-card-back,
        .drink-card[data-name="Mamie Taylor"] .drink-card-back,
        .drink-card[data-name="Rusty Blade"] .drink-card-back,
        .drink-card[data-name="Spiced Rum Buck"] .drink-card-back,
        .drink-card[data-name="Whiskey Highball"] .drink-card-back { background-position: center, center, left; }
    </style>
</head>
<body class="antialiased text-gray-300">

    <!-- Splash screen PWA -->
    <div id="splash-screen">
        <div class="splash-text">Tap to Enter</div>
    </div>

    <div id="app" class="app-container">
        <!-- Main Brand Header -->
        <header class="text-center">
            <div id="header-logo-container" class="w-full flex items-center justify-center">
                <img src="https://raw.githubusercontent.com/aarmax8/Nomads/e3f42af1097f6a8b37a1f9ea55c83cd494318755/title16.jpg?raw=true" id="header-logo-image" alt="Nomad's Logo">
            </div>
        </header>
        
        <main>
            <!-- Action bar with Layout Toggles, Stock, and Search Filters -->
            <div id="action-bar">
                <button id="action-random-btn" class="footer-btn" title="Pick a Random Drink">
                    <i class="fas fa-dice"></i>
                    <span class="text-xs">Random</span>
                </button>
                
                <button id="action-favorites-btn" class="footer-btn" title="Favorites">
                    <i class="fas fa-heart"></i>
                    <span class="text-xs">Faves</span>
                </button>

                <!-- Desktop/Mobile Layout Mode Swapper -->
                <button id="action-layout-btn" class="footer-btn" title="Toggle Layout Mode">
                    <i class="fas fa-grip"></i>
                    <span class="text-xs" id="layout-btn-label">Desktop View</span>
                </button>
                
                <button id="action-stock-btn" class="footer-btn" title="Bar Stock">
                    <i class="fas fa-wine-bottle"></i>
                    <span class="text-xs">Stock</span>
                </button>
                
                <button id="action-filters-btn" class="footer-btn" title="Filters">
                    <i class="fas fa-martini-glass-citrus"></i>
                    <span class="text-xs">Filters</span>
                </button>
            </div>
            
            <!-- Dynamic Cocktails Display Grid/Carousel -->
            <div id="menu-grid" class="carousel-view"></div>
        </main>

        <!-- Dynamic Navigation Control Footer -->
        <div id="app-footer">
            <div id="footer-content">
                <button id="scroll-home-btn" class="footer-btn" title="Back to Index">
                    <i class="fas fa-home"></i>
                    <span class="text-xs">Home</span>
                </button>

                <button id="scroll-prev-btn" class="footer-btn" title="Scroll Left">
                    <i class="fas fa-motorcycle fa-flip-horizontal"></i> 
                    <span class="text-xs">Rewind</span>
                </button>
                
                <button id="toggle-view-btn-main" class="footer-btn" title="Toggle Recipe/Story">
                    <i class="fas fa-book-open"></i>
                    <span class="text-xs" id="story-toggle-label">Story View</span>
                </button>

                <button id="scroll-next-btn" class="footer-btn" title="Scroll Right">
                    <i class="fas fa-motorcycle"></i>
                    <span class="text-xs">Skip</span>
                </button>
            </div>
        </div>
    </div>

    <!-- Favorites Modal -->
    <div id="favorites-modal" class="modal fixed inset-0 bg-black/60 flex items-center justify-center p-4 hidden opacity-0 z-50">
        <div class="modal-panel rounded-2xl shadow-2xl w-full max-w-2xl max-h-[90vh] flex flex-col">
            <div class="modal-header p-6 flex-shrink-0">
                <div class="flex justify-between items-center">
                    <h2 class="text-3xl text-amber-400 font-cinzel tracking-wider">Favorites</h2>
                    <button id="close-favorites-btn" class="text-gray-400 hover:text-white text-3xl">&times;</button>
                </div>
            </div>
            <div id="favorites-list-container" class="p-6 text-gray-300 overflow-y-auto"></div>
        </div>
    </div>

    <!-- Bar Stock Modal -->
    <div id="bar-stock-modal" class="modal fixed inset-0 bg-black/60 flex items-center justify-center p-4 hidden opacity-0 z-50">
        <div class="modal-panel rounded-2xl shadow-2xl w-full max-w-2xl max-h-[90vh] flex flex-col">
            <div class="modal-header p-6 flex justify-between items-center flex-shrink-0">
                <h2 class="text-3xl text-amber-400 font-cinzel tracking-wider">Bar Stock</h2>
                <button id="close-stock-btn" class="text-gray-400 hover:text-white text-3xl">&times;</button>
            </div>
            <div id="bar-stock-content" class="p-6 text-gray-300 flex-grow min-h-0 overflow-y-auto"></div>
        </div>
    </div>
    
    <!-- Filter Modal -->
    <div id="filter-modal" class="modal fixed inset-0 bg-black/60 flex items-center justify-center p-4 hidden opacity-0 z-50">
        <div class="modal-panel rounded-2xl shadow-2xl w-full max-w-2xl max-h-[90vh] flex flex-col">
            <div class="modal-header p-6 flex-shrink-0">
                <div class="flex justify-between items-center">
                    <h2 class="text-3xl text-amber-400 font-cinzel tracking-wider">Browse The Deck</h2>
                    <button id="close-filter-btn" class="text-gray-400 hover:text-white text-3xl">&times;</button>
                </div>
                <p class="text-gray-400 mt-2">Select filters to find your drink.</p>
            </div>
            <div id="filter-modal-content" class="p-6 text-gray-300 overflow-y-auto"></div>
            <div class="p-4 border-t border-white/10 flex justify-end gap-4">
                <button id="reset-filters-btn" class="py-2 px-6 rounded-lg bg-transparent border border-gray-500 hover:bg-gray-700 text-white font-bold transition-colors">Reset</button>
                <button id="apply-filters-btn" class="py-2 px-6 rounded-lg bg-amber-600 hover:bg-amber-500 text-black font-bold transition-colors">Show Drinks</button>
            </div>
        </div>
    </div>

    <script>
        "use strict";

        const STOCK_STORAGE_KEY = 'nomads_bar_stock_v4';
        const DRINKS_FAVORITES_KEY = 'nomads_favorite_drinks_v3';
        
        let cocktails = [];
        let favoriteDrinks = [];
        let barStock = {};
        let activeFilters = {
            category: 'all',
            spirit: null,
            ingredient: null,
            showFavoritesOnly: false
        };
        let isGlobalTarotView = false;
        let isToggleThrottled = false; 
        let isDesktopLayout = false;

        let menuGrid, barStockModal, filterModal, favoritesModal, randomDrinkBtn;

        /**
         * Common cocktails with generic ingredients on front, and made-up names/stories on back
         */
        function getInitialCocktailData() {
            return [
                { name: "Placeholder", recipe: [], isBarcode: true, story: "", flavorProfile: "", pours: [] },

                { 
                    name: "Redheaded Slut", 
                    flavorProfile: "Like a sweet peach that got into a fistfight with Jäger. The Jäger won.", 
                    recipe: ["1 oz Jägermeister", "1 oz Peach Schnapps", "Fill glass with Cranberry Juice"], 
                    story: "Redheaded Trouble: Named in honor of the bar fight started by a guy who told our baldest member he liked his 'fiery red hair.' Turns out it was a wig he was sensitive about. The ensuing chaos was beautiful.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/c8d1eb3f9af90ec4f55951765f680513fe3bf164/frontend/R.jpg", 
                    cardHook: "Some ghosts just want to party.",
                    pours: ["Jägermeister", "Peach Schnapps"]
                },
                { 
                    name: "Caramel Apple Shot", 
                    flavorProfile: "Tastes like a liquid caramel apple with bitters to make you feel like a grown-up.", 
                    recipe: ["1.5 oz Butterscotch Schnapps", "1.5 oz Apple Pucker", "2 dashes Angostura Bitters", "Fill with Sprite"], 
                    story: "Caramel Apple Cruiser: Our prospect, Pip, tried to make 'fancy autumn cocktails.' He tripped, dumped a bag of apples and a bottle of butterscotch into a vat of ginger soda. We tasted it and spared his life.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/c81556a569470611da64fb23e311817602720d95/mannart8.jpg", 
                    cardHook: "The taste of a glorious failure.",
                    pours: ["Butterscotch Schnapps", "Apple Pucker"]
                },
                { 
                    name: "Tom Collins", 
                    flavorProfile: "Crisp, effervescent botanical classic with a bright lemon zest lift.", 
                    recipe: ["2 oz Gin", "1 oz Lemon Juice", "0.75 oz Simple Syrup", "Top with Club Soda", "Cherry on Top"], 
                    story: "Negroni Twist: This isn't one of ours. We 'borrowed' the recipe from a fancy Italian bar after our President complimented the bartender's leather jacket... and then 'traded' him for it.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_8004.jpg", 
                    cardHook: "Bubbly, botanical, and completely classic.",
                    pours: ["Tanqueray Gin", "Sloe Gin"]
                },
                { 
                    name: "Jäger Apple Mule", 
                    flavorProfile: "It's green, it's mean, and it tastes like Jäger and sour orchard fruits.", 
                    recipe: ["1.5 oz Jägermeister", "0.5 oz Apple Pucker", "Fill glass with Sprite", "Splash of Lime Juice"], 
                    story: "Mechanic: Sal, our mechanic, calls this 'motivation.' He says the neon green reminds him of brand-new coolant, which is the only thing that gets him excited. We're worried about Sal.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/71f80d842e362733e8b2f22ea02e7b1fc732f0a9/mannart17.jpg", 
                    cardHook: "Tastes better than degreaser. Probably.",
                    pours: ["Jägermeister"]
                },
                { 
                    name: "Cherry Vodka Sour", 
                    flavorProfile: "Dangerously red. Tastes like a cherry candy that went to college and got a drinking problem.", 
                    recipe: ["1.5 oz Vodka", "1 oz Cherry Schnapps", "Fill glass with Sweet and Sour Mix", "Splash of Lime Juice"], 
                    story: "Redline Riot: A tribute to the time we tried to see if a cherry-red '78 Sportster could actually hit the redline in first gear without exploding. It could not. This drink is less expensive to clean up.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_8306.jpg", 
                    cardHook: "Here's to things we can't talk about.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka"]
                },
                { 
                    name: "Spiced Rum Buck", 
                    flavorProfile: "Warm spiced rum with a sharp lime kick and a bubbly finish.", 
                    recipe: ["2 oz Spiced Rum", "0.5 oz Lime Juice", "Fill glass with Sprite"], 
                    story: "Panhead Kick: This drink has all the stages of trying to kickstart a stubborn old Panhead: spicy anger, a sharp kick of frustration, and sweet relief when it roars to life.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/0dcbab77d90f59f2298642338dfee691353ce70a/frontend/USq6nI.jpg", 
                    cardHook: "A more reliable way to get started.",
                    pours: ["Captain Morgan Spiced Rum", "Kraken Black Spiced Rum", "Bacardi Rum"]
                },
                { 
                    name: "Shirley Temple", 
                    flavorProfile: "It's Sprite and cherry. Zero alcohol. Tastes like childhood and judgment.", 
                    recipe: ["Fill glass with Sprite", "Splash of Grenadine", "Cherry on Top"], 
                    story: "The Crusher's Choice: Our biggest, meanest member, Crusher, orders this. Not for his kid. For himself. He says it 'calms his inner rage.' You WILL NOT make fun of him.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7989.jpg", 
                    cardHook: "The toughest drink in the bar.",
                    pours: ["Sprite", "Grenadine", "Cherries"]
                }, 
                { 
                    name: "Dark 'n' Stormy", 
                    flavorProfile: "Dark, moody rum meets spicy ginger and a crack of lime.", 
                    recipe: ["2 oz Dark Rum", "0.5 oz Lime Juice", "2 dashes Angostura Bitters", "Fill glass with Sprite"], 
                    story: "Tornado Alley: We dared our prospect to ride through a tornado warning. He came back an hour later, clothes torn, hair standing on end, holding a bottle of dark rum he 'found'.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/19071808632f94b0b81d595f74f700f0.jpg", 
                    cardHook: "To making bad weather worse.",
                    pours: ["Kraken Black Spiced Rum", "Captain Morgan Spiced Rum", "Bacardi Rum"]
                },
                { 
                    name: "Amaretto Rum & Coke", 
                    flavorProfile: "A dangerously smooth mix of dark rum, sweet amaretto, and Coke.", 
                    recipe: ["1.5 oz Dark Rum", "1 oz Amaretto", "Fill glass with Coke"], 
                    story: "Kraken's Grip: After two of these, you'll have a death grip on the bar and the questionable belief that you can arm-wrestle a sea monster. You can't. Ask Fingers, he's got the scars.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/c7fd6a017b5f1a4a26d81720d989dd1cccfca51c/mannart14.jpg", 
                    cardHook: "It'll get a hold on you.",
                    pours: ["Amaretto", "Kraken Black Spiced Rum", "Bacardi Rum"]
                },
                { 
                    name: "Scotch Highball", 
                    flavorProfile: "A classic smoky effervescence. Scotch meets sparkling mineral water in a clean glass.", 
                    recipe: ["2 oz Scotch Whisky", "Top with Club Soda"], 
                    story: "Blood and Sand: Named after the classic bullfighter film, this drink captures the sand of the arena and the blood of the bull. It's complex, fruity, and packs a smoky punch.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/71f80d842e362733e8b2f22ea02e7b1fc732f0a9/mannart18.jpg", 
                    cardHook: "Smoky, clean, and classic.",
                    pours: ["Dewars Scotch", "Johnnie Walker Red Label"]
                },
                { 
                    name: "Island Hopper", 
                    flavorProfile: "It's coconut rum and pineapple. Tastes like a tropical vacation you can't afford.", 
                    recipe: ["1 oz Malibu Rum", "1 oz Bacardi Rum", "Fill with Pineapple Juice", "Splash of Lime Juice"], 
                    story: "Beach Cruiser: This is for the guy who wears a Hawaiian shirt under his leather cut. He talks about riding to the keys, but we all know he's just going to the tourist trap on the pier.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/c3832f3a3d3d7a73ddff445c272953dc90cb5c4d/mannart21.jpg", 
                    cardHook: "A vacation in a glass.",
                    pours: ["Malibu Rum", "Bacardi Rum"]
                },
                { 
                    name: "Appletini", 
                    flavorProfile: "A shockingly green blast of sour apple and clean vodka. Tastes like a dare.", 
                    recipe: ["1 oz Sweet and Sour Mix", "1 oz Apple Pucker", "2 oz Vodka", "Cherry on Top"], 
                    story: "The Prospect's Bane: This drink is too green to be safe and too sweet to be sober. It's what the rival club drinks when they think they're being subtle.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/1e1c514fd7e07a421ae95d827c230b7fea504fa7/aabuckeyecider.jpg", 
                    cardHook: "Boldly green, deeply potent.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka"]
                },
                { 
                    name: "Rosemary Gin Tonic", 
                    flavorProfile: "A classic botanical G&T featuring complex, refreshing herbal aromas.", 
                    recipe: ["2 oz Gin", "0.5 oz Lime Juice", "Top with Tonic Water", "2 dashes Rosemary Lavender Bitters"], 
                    story: "Long Haul: This drink is like a 10-hour ride through Nebraska. It starts out fine, then it gets weirdly complex, then it's just... a lot. By the end, you respect its commitment.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/cd94ee724b96582e3ef3f50a663b43038b8d2c77/mannart15.jpg", 
                    cardHook: "For when you're in it for the long haul.",
                    pours: ["Tanqueray Gin", "Sloe Gin"]
                },
                { 
                    name: "Green Tea Shot", 
                    flavorProfile: "Sweet, peach-citrus classic whiskey shot that tastes exactly like tea.", 
                    recipe: ["1.5 oz Jameson Irish Whiskey", "1 oz Peach Schnapps", "Fill with Sweet and Sour Mix", "Splash of Sprite"], 
                    story: "Doc's Herbal Cure: Doc told us to drink more green tea. We complied. This contains absolutely no actual tea, but after three of them, you won't care about antioxidants.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/c8d1eb3f9af90ec4f55951765f680513fe3bf164/frontend/b3ca1c20f8245c41dabb7020eb5794f7.jpg", 
                    cardHook: "A healthy dose of trouble.",
                    pours: ["Woodford Reserve", "WhistlePig", "Michter's", "Jameson Irish Whiskey", "Maker's Mark", "Crown Royal", "Bulleit Bourbon", "Southern Comfort", "Old Grand-Dad Whiskey", "Jim Beam Bourbon"]
                },
                { 
                    name: "Lemon Drop Martini", 
                    flavorProfile: "Chilled vodka, sweet citrus, and a bright sugared rim finish.", 
                    recipe: ["2 oz Vodka", "0.75 oz Triple Sec", "0.75 oz Lemon Juice", "0.5 oz Simple Syrup"], 
                    story: "The Patio Sipper: This is what you drink when you want to feel fancy, even if you're sitting on a rusty oil drum. The official drink of 'just one more.' Famous last words.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/8152e3c111a698e2a7f072b33b5662906e08d17d/mannart23.jpg", 
                    cardHook: "The quintessential patio classic.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka"]
                },
                { 
                    name: "Apricot Gimlet", 
                    flavorProfile: "A botanical, boozy blend of gin, sweet apricot, and citrus.", 
                    recipe: ["1.5 oz Gin", "0.75 oz Apricot Brandy", "Fill with Orange Juice", "0.5 oz Lemon Juice", "Cherry on Top"], 
                    story: "Paradise: We call this Paradise because it's what 'Wrench' drinks when he's dreaming of retiring to a beach somewhere. One sip and he's gone... mentally, at least.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/1bf52dfc1aad553db68333418c40d848.jpg", 
                    cardHook: "Your own personal oasis.",
                    pours: ["Tanqueray Gin", "Sloe Gin"]
                },
                { 
                    name: "Tequila Sunrise", 
                    flavorProfile: "Sweet orange juice and dynamic tequila layered with rich grenadine.", 
                    recipe: ["2 oz Tequila", "Fill with Orange Juice", "2 dashes Orange Bitters", "0.5 oz Grenadine", "Cherry on Top"], 
                    story: "Desert Sunrise: The only time you should see a desert sunrise is because you've been riding all night. This drink lets you skip the riding part.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/c8d1eb3f9af90ec4f55951765f680513fe3bf164/thumbnail_IMG_8003.jpg", 
                    cardHook: "All the beauty, none of the early morning.",
                    pours: ["El Mayor Tequila", "Jose Cuervo Silver Tequila"]
                },
                { 
                    name: "Elderflower Margarita", 
                    flavorProfile: "Rich floral elderflower meets agave spirits and sour citrus.", 
                    recipe: ["1.5 oz Tequila", "0.75 oz St-Germain", "1 oz Pineapple Juice", "0.5 oz Lime Juice"], 
                    story: "Gilded Serpent: Looks fancy. Tastes fancy. But it's still tequila. It's like putting a tuxedo on a snake. You know it's gonna bite you eventually.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/67bab4c8460e76ee5bd5fe757150ef26--bike-art-motorcycle-art.jpg", 
                    cardHook: "Fancy on the outside, dangerous on the inside.",
                    pours: ["El Mayor Tequila", "Jose Cuervo Silver Tequila"]
                },
                { 
                    name: "Drambuie & Sprite", 
                    flavorProfile: "Sweet, honeyed herbs paired with sparkling Sprite and citrus.", 
                    recipe: ["2 oz Drambuie", "Fill glass with Sprite", "Splash of Lime Juice"], 
                    story: "Rainmaker: You know that last mile before you get home? When your back aches, your ears are ringing, and you'd sell a kidney for a hot shower? This is that feeling in a glass.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/69070319cd6333061bdbb34ed7dee0c1.jpg", 
                    cardHook: "For the last mile of a heavy journey.",
                    pours: ["Drambuie"]
                },
                { 
                    name: "Lemon Drop Shot", 
                    flavorProfile: "A brief, highly sharp citrus explosion. Intensely sour and clean.", 
                    recipe: ["2 oz Vodka", "1 oz Lemon Juice", "0.75 oz Simple Syrup"], 
                    story: "Switchblade: It's small, sharp, and will end your night if you're not careful. Named in honor of our shortest member, 'Stubbs,' who is all of those things.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/6a73cec9f46d798d4ba58ec29f5623f2.jpg", 
                    cardHook: "Respect the lemon.",
                    pours: ["Stolichnaya Citros Vodka", "Grey Goose Vodka", "Ketel One Vodka"]
                },
                { 
                    name: "Comfort Cranberry Fizz", 
                    flavorProfile: "Fruity, sparkling, and easy-going Southern classic.", 
                    recipe: ["2 oz Southern Comfort", "2 oz Cranberry Juice", "Top with Club Soda"], 
                    story: "Buckeye Juice: Named for the state nut, but there's nothing nutty about it. It's scarlet red, fizzy, and hits with the force of a linebacker. A true fan favorite.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/5fdd2d485722e.jpg", 
                    cardHook: "Scarlet, fizzy, and strong.",
                    pours: ["Southern Comfort"]
                },
                { 
                    name: "Sloe Gin Comfort Fizz", 
                    flavorProfile: "Fruity, deeply tart, and sweet. Tastes like carbonated plum.", 
                    recipe: ["1 oz Sloe Gin", "1 oz Southern Comfort", "0.5 oz Lemon Juice", "Fill with Club Soda"], 
                    story: "Road Rash: It's red, it stings, and it's a story you'll tell for years. The drink, not the injury. The injury just gets you a lame scar and a lecture from Doc.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/David-Mann-Art-2.jpg", 
                    cardHook: "Much better than the real thing.",
                    pours: ["Sloe Gin", "Southern Comfort"]
                },
                { 
                    name: "Cosmopolitan", 
                    flavorProfile: "Classic sophisticated balance of sweet orange and tart cranberry.", 
                    recipe: ["1.5 oz Vodka", "0.75 oz Triple Sec", "0.75 oz Cranberry Juice", "0.5 oz Lime Juice"], 
                    story: "Poinsettia: This one only comes out during the holidays. It's fancy, it's red, and it makes everyone feel a bit more festive, even if they're just arguing about who has to shovel the snow.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/ea2380beff602a5a9070cc310b2a37e4b444246c/frontend/0ac5da1e71c995f58d75335fffabd844.jpg", 
                    cardHook: "Cheers to the festive season.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka"]
                },
                { 
                    name: "Bourbon Root Beer", 
                    flavorProfile: "Root beer sweetened with simple syrup and smooth whiskey oak finish.", 
                    recipe: ["1.5 oz Bourbon", "1 oz Root Beer Schnapps", "0.5 oz Simple Syrup", "Top with Sprite"], 
                    story: "Cowboy's Hard Root Beer: A cowboy bet us we couldn't make a drink that tasted like 'a rodeo in a bottle.' We made this. It's got the sweet taste of victory and the kick of a pissed-off bull.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/il_fullxfull.1315813799_ayvc.webp", 
                    cardHook: "This drink has spurs.",
                    pours: ["Woodford Reserve", "WhistlePig", "Michter's", "Jameson Irish Whiskey", "Maker's Mark", "Crown Royal", "Bulleit Bourbon", "Southern Comfort", "Old Grand-Dad Whiskey", "Jim Beam Bourbon"]
                },
                { 
                    name: "Peach Bourbon Smash", 
                    flavorProfile: "Bold bourbon softened with juicy peach and sour citrus.", 
                    recipe: ["1.5 oz Bourbon", "0.5 oz Peach Liqueur", "0.5 oz Simple Syrup", "0.75 oz Lemon Juice", "Dash of Bitters"], 
                    story: "Wolf Ticket: A 'Wolf Ticket' is a threat you don't intend to carry out. This drink? It makes promises it definitely keeps. The peach draws you in, the high-proof spirit takes you out.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/c7fd6a017b5f1a4a26d81720d989dd1cccfca51c/mannart22.jpg", 
                    cardHook: "Don't write checks you can't cash.",
                    pours: ["Woodford Reserve", "WhistlePig", "Michter's", "Jameson Irish Whiskey", "Maker's Mark", "Crown Royal", "Bulleit Bourbon", "Southern Comfort", "Old Grand-Dad Whiskey", "Jim Beam Bourbon"]
                },
                { 
                    name: "Garibaldi", 
                    flavorProfile: "Bitter, sweet, and bright orange. Tastes like a simple, refreshing idea.", 
                    recipe: ["2.5 oz Orange Juice", "2.5 oz Aperol"], 
                    story: "The Rebel's OJ: Named for an Italian revolutionary, this drink is as simple as it is refreshing. It's what you drink when you want something bright, bitter, and uncomplicated.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/672ca23068e35c6481458f0911d99ceb.jpg", 
                    cardHook: "Italy's simple, bitter classic.",
                    pours: ["Aperol"]
                },
                { 
                    name: "Crown Orange Collins", 
                    flavorProfile: "Rich blended whiskey mixed with bright, refreshing citrus elements.", 
                    recipe: ["2 oz Blended Whiskey", "2 oz Orange Juice", "0.5 oz Lemon Juice", "Splash of Grenadine", "Top with Club Soda"], 
                    story: "Ward Eight: This is what happens when you try to make 'Jungle Juice' with actual high-end blended whiskey. It's dangerously drinkable. A frontier of bad decisions awaits.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/4ef937229693734b1be907cc24f322eb.jpg", 
                    cardHook: "History, but with more sugar.",
                    pours: ["Woodford Reserve", "WhistlePig", "Michter's", "Jameson Irish Whiskey", "Maker's Mark", "Crown Royal", "Bulleit Bourbon", "Southern Comfort", "Old Grand-Dad Whiskey", "Jim Beam Bourbon"]
                },
                { 
                    name: "Whiskey Sour", 
                    flavorProfile: "A rich, velvety whiskey classic balanced with fresh-pressed citrus.", 
                    recipe: ["2 oz Bourbon", "0.75 oz Lemon Juice", "0.75 oz Simple Syrup", "2 dashes Angostura Bitters", "Cherry on Top"], 
                    story: "The High-Sided: Named after a famous Parisian magazine, our version is for the man about the chop shop. It's sophisticated, strong, and guaranteed to loosen the tongue.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/8152e3c111a698e2a7f072b33b5662906e08d17d/mannart24.jpg", 
                    cardHook: "The official drink of the well-dressed nomad.",
                    pours: ["Woodford Reserve", "WhistlePig", "Michter's", "Jameson Irish Whiskey", "Maker's Mark", "Crown Royal", "Bulleit Bourbon", "Southern Comfort", "Old Grand-Dad Whiskey", "Jim Beam Bourbon"]
                },
                { 
                    name: "Vodka Cranberry", 
                    flavorProfile: "Bubbly, light, and bittersweet fruit standard.", 
                    recipe: ["2 oz Vodka", "3 oz Cranberry Juice", "Top with Club Soda", "Splash of Lime Juice"], 
                    story: "The Low-Side: This is the Negroni's lighter brother. It's what you drink when you want to look sophisticated, but it's 2 PM on a Tuesday. We 'borrowed' this from the same Italian bar.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/e7b78721b45c1417e839ceb2df4a358144244771/mannart1.jpg", 
                    cardHook: "Simple, red, and classic.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka"]
                },
                { 
                    name: "Whiskey Cherry Coke", 
                    flavorProfile: "A boozy, bubbly cherry Coke. It's the drink version of a classic muscle car.", 
                    recipe: ["2 oz Bourbon", "0.5 oz Cherry Schnapps", "Fill glass with Coke"], 
                    story: "Black Cherry Bomb: This isn't a drink, it's an escalation. It starts with whiskey, adds some cherry, and ends with you thinking it's a good idea to see if your bike can do a burnout on the bar. It can't.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/5a6b0379f72b6c8fb2751409d48ac8fa.jpg", 
                    cardHook: "Tastes like minor property damage.",
                    pours: ["Woodford Reserve", "WhistlePig", "Michter's", "Jameson Irish Whiskey", "Maker's Mark", "Crown Royal", "Bulleit Bourbon", "Southern Comfort", "Old Grand-Dad Whiskey", "Jim Beam Bourbon"]
                },
                { 
                    name: "Southern Screwdriver", 
                    flavorProfile: "Sweet peach liqueur elements met with refreshing, tart orange juice.", 
                    recipe: ["1.5 oz Southern Comfort", "0.5 oz Sloe Gin", "Fill glass with Orange Juice"], 
                    story: "Southern Crossroads: This is the drink for when you have two bad options. It's sweet enough to make you forget you're making a choice, and strong enough to make you not care.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_8294.jpg", 
                    cardHook: "For making the wrong choices.",
                    pours: ["Southern Comfort", "Sloe Gin"]
                },
                { 
                    name: "Mamie Taylor", 
                    flavorProfile: "Smoky scotch, sharp lime, and bubbly Sprite. A delicious, carbonated warning.", 
                    recipe: ["2 oz Scotch Whisky", "0.5 oz Lime Juice", "2 dashes Angostura Bitters", "Fill with Sprite"], 
                    story: "Mamie Taylor: Named for our founder, 'Red,' not because he liked scotch, but because this is the color his face got when a prospect called his prized chopper 'cute.' A drink of respect and fear.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/bc62d5aebb9a232818104ce036e8325a73533520/frontend/206S17.jpg", 
                    cardHook: "To the legends in the club.",
                    pours: ["Dewars Scotch", "Johnnie Walker Red Label"]
                },
                { 
                    name: "Brandy Daisy", 
                    flavorProfile: "A sweet, powerful, and aromatic splash of brandy and orange citrus.", 
                    recipe: ["2 oz Brandy", "1 oz Triple Sec", "0.75 oz Lemon Juice", "Top with Club Soda"], 
                    story: "Brandy Thunder: Named for the sound 'Wrench' made when he dropped a transmission on the shop floor after drinking two of these. It's bright, it's loud, and it'll shake the garage.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/bd0bc33e2c84ea33e265900701fa8331.jpg", 
                    cardHook: "Bring the thunder.",
                    pours: ["E&J Brandy"]
                },
                { 
                    name: "Creamy Irish Russian", 
                    flavorProfile: "A rich coffee-cream drink with a refreshing, bubbly lift.", 
                    recipe: ["2 oz Vodka", "1 oz Kahlúa", "1 oz Baileys Irish Cream", "Fill glass with Club Soda"], 
                    story: "The Irish Russian: This is what happens when our most stubborn members, an Irishman and a Russian, argue over whose drink is better. It's a creamy, boozy mess that shuts them up.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/bd2c7d94ce4111f6235a52c8cf70e89e.jpg", 
                    cardHook: "The taste of a weird truce.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka"]
                },
                { 
                    name: "Margarita", 
                    flavorProfile: "The holy trinity of agave spirit, fresh lime, and orange liqueur.", 
                    recipe: ["2 oz Tequila", "1 oz Triple Sec", "1 oz Lime Juice", "Top with Club Soda"], 
                    story: "The Shakedown: We don't know who Rita is. All we know is that this combination of tequila and lime is the reason for half the bad tattoos in this club. Drink with caution.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/3a506b28b91e0e5d031cedbeca489a14.jpg", 
                    cardHook: "¡Vámonos!",
                    pours: ["El Mayor Tequila", "Jose Cuervo Silver Tequila"]
                },
                { 
                    name: "Moscow Mule", 
                    flavorProfile: "Crisp vodka, sharp lime, and sweet Sprite soda with a dash of bitters.", 
                    recipe: ["2 oz Vodka", "0.5 oz Lime Juice", "2 dashes Angostura Bitters", "Fill glass with Sprite"], 
                    story: "The Kickstand: It's crisp, it's spicy, and it kicks you right in the teeth when you're not expecting it. Just like our club's lawyer. We prefer the drink.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/c143359dbf62f9ce9349aa42e3bfe8aa.jpg", 
                    cardHook: "It's got a kick.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka"]
                },
                { 
                    name: "Aperol Amaretto Sour", 
                    flavorProfile: "Sweet almond, bright botanical herbs, and tart citrus.", 
                    recipe: ["1 oz Amaretto", "1 oz Gin", "0.5 oz Aperol", "0.5 oz Passion Fruit Syrup", "0.5 oz Lemon Juice"], 
                    story: "Killer Cocktail: Called this because the first guy who tried it, 'Pops,' claimed it was so good it 'killed' his craving for anything else. He then proceeded to wreck a jukebox with a pool cue.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/5638f66d00401c933df787eb50253fc8.jpg", 
                    cardHook: "As complex as your last bad decision.",
                    pours: ["Amaretto", "Aperol", "Tanqueray Gin", "Sloe Gin"]
                },
                { 
                    name: "Screwdriver", 
                    flavorProfile: "Simple, historic pairing of clean vodka and orange juice with a dash of bitters.", 
                    recipe: ["2 oz Vodka", "2 dashes Orange Bitters", "Fill glass with Orange Juice"], 
                    story: "The Hubcap: Our mechanic insists this is a legitimate cocktail. We're pretty sure it's just what he drinks when he runs out of clean glasses and has to mix it in a hubcap.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/cfff51feaf6082d29a37912a44bfedc3.jpg", 
                    cardHook: "The second-best use for a screwdriver.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka"]
                },
                { 
                    name: "Old Fashioned", 
                    flavorProfile: "Rich whiskey notes balanced elegantly with aromatic bitters and sugar.", 
                    recipe: ["2 oz Bourbon", "0.75 oz Simple Syrup", "2 dashes Angostura Bitters", "Cherry on Top"], 
                    story: "Rusty Blade: A traditional Old Fashioned. It's sharp, sweet, and means business. What you drink after you've just won a knife fight over a prime parking spot.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_8220.jpg", 
                    cardHook: "The sharpest blade is a sharp mind.",
                    pours: ["Woodford Reserve", "WhistlePig", "Michter's", "Jameson Irish Whiskey", "Maker's Mark", "Crown Royal", "Bulleit Bourbon", "Southern Comfort", "Old Grand-Dad Whiskey", "Jim Beam Bourbon"]
                },
                { 
                    name: "Rusty Nail", 
                    flavorProfile: "Smoky scotch whisky backed by sweet, honeyed Drambuie.", 
                    recipe: ["2 oz Scotch Whisky", "1 oz Drambuie", "Splash of Lemon Juice"], 
                    story: "The Dealmaker: This is what you drink when you've made a deal you know you'll regret. Like trading your chopper for a 'guaranteed' winning lottery ticket. Ask Jimmy how that went.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7993.jpg", 
                    cardHook: "Every deal has its price.",
                    pours: ["Dewars Scotch", "Johnnie Walker Red Label"]
                },
                { 
                    name: "Between the Sheets", 
                    flavorProfile: "Strong, citrusy, and sweet. A historic pairing of brandy, rum, and triple sec.", 
                    recipe: ["1 oz Brandy", "1 oz Bacardi Rum", "1 oz Triple Sec", "0.25 oz Lemon Juice", "2 dashes Orange Bitters"], 
                    story: "The Midnight Run: This drink is smooth, seductive, and means business. It's not for beginners. It's what you order when your night is about to get a lot more interesting.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/c8d1eb3f9af90ec4f55951765f680513fe3bf164/frontend/64c7af61b8476938a0b6bc9e8462ef3f--motorcycle-posters-motorcycle-art.jpg", 
                    cardHook: "Potent, sophisticated, and seductive.",
                    pours: ["E&J Brandy", "Bacardi Rum", "Triple Sec"]
                },
                { 
                    name: "Cuba Libre", 
                    flavorProfile: "A highball rum and Coke brightened with fresh-cracked lime juice.", 
                    recipe: ["2 oz Bacardi Rum", "0.5 oz Lime Juice", "2 dashes Angostura Bitters", "Fill glass with Coke"], 
                    story: "The Getaway: Means 'Free Cuba.' We drank it to celebrate freeing our club mascot, a grumpy bulldog named Che, from the local dog catcher. It was a whole thing. The dog was not grateful.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/d9a9ffbd510d7ea900f31195d5e857f6.jpg", 
                    cardHook: "Tastes like a good road trip.",
                    pours: ["Bacardi Rum", "Captain Morgan Spiced Rum", "Kraken Black Spiced Rum"]
                },
                { 
                    name: "Godfather", 
                    flavorProfile: "Bold oak-aged bourbon tempered with sweet, nutty amaretto.", 
                    recipe: ["2 oz Bourbon", "0.75 oz Amaretto"], 
                    story: "The Godfather: This is what you drink right before you make a very serious, legally questionable promise to a group of men you probably shouldn't trust. It tastes like brotherhood.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/3cdd71f09194cbf21b99337a4fc180c7d71380e5/frontend/yWMhLC.jpg", 
                    cardHook: "To promises you'll try to keep.",
                    pours: ["Woodford Reserve", "WhistlePig", "Michter's", "Jameson Irish Whiskey", "Maker's Mark", "Crown Royal", "Bulleit Bourbon", "Southern Comfort", "Old Grand-Dad Whiskey", "Jim Beam Bourbon"]
                },
                { 
                    name: "White Russian", 
                    flavorProfile: "A rich, creamy, and simple blend of vodka, coffee, and Irish cream.", 
                    recipe: ["2 oz Vodka", "1 oz Kahlúa", "1 oz Baileys Irish Cream"], 
                    story: "The Bathrobe: This drink is for when you just don't want to deal with anything. It's a creamy, alcoholic blanket for your problems. It doesn't solve them, but it makes them quieter.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/e5a7f5bfc3b2c200266b6df05a132e17.jpg", 
                    cardHook: "It really ties the room together.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka"]
                },
                { 
                    name: "Long Island Iced Tea", 
                    flavorProfile: "Tastes like sweet tea. Contains no tea. A strong mix of five clear spirits.", 
                    recipe: ["0.5 oz Vodka", "0.5 oz Gin", "0.5 oz Bacardi Rum", "0.5 oz Tequila", "0.5 oz Triple Sec", "1 oz Lemon Juice", "Fill glass with Coke"], 
                    story: "The Multi-Tool: This isn't a drink, it's a dare. It's a mix of everything that will get you into trouble, served in a glass. The only 'tea' involved is the 'T-rouble' you'll be in tomorrow.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/c8d1eb3f9af90ec4f55951765f680513fe3bf164/mannart7.jpg", 
                    cardHook: "A beautiful, delicious lie.",
                    pours: ["Grey Goose Vodka", "Tanqueray Gin", "Bacardi Rum", "Jose Cuervo Silver Tequila", "Triple Sec"]
                },
                { 
                    name: "Sazerac", 
                    flavorProfile: "Bold whiskey paired with herbal anise aromas and aromatic bitters.", 
                    recipe: ["2 oz Bourbon", "Rinse of Pernod", "0.5 oz Simple Syrup", "2 dashes Peychaud's Bitters", "Top with Club Soda"], 
                    story: "The Big Easy Sazerac: Our president spent a week in New Orleans and came back with 'spiritual awakening' and this recipe. The awakening wore off, but the Sazerac stuck around.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/3cdd71f09194cbf21b99337a4fc180c7d71380e5/thumbnail_IMG_8298.jpg", 
                    cardHook: "Respect the Big Easy.",
                    pours: ["Woodford Reserve", "WhistlePig", "Michter's", "Jameson Irish Whiskey", "Maker's Mark", "Crown Royal", "Bulleit Bourbon", "Southern Comfort", "Old Grand-Dad Whiskey", "Jim Beam Bourbon"]
                },
                { 
                    name: "Anise Gin Tonic", 
                    flavorProfile: "Botanical gin with a sharp, sweet kick of anise licorice herbs.", 
                    recipe: ["Rinse of Pernod", "1.5 oz Gin", "0.5 oz Lime Juice", "Top with Tonic Water"], 
                    story: "Phantom Shift: Named for the 'phantom' expenses that keep appearing on the club's credit card. We know who's doing it. And their time is short.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/f2a6114d2d00087a3f9192fc5cc74614.jpg", 
                    cardHook: "For the gears that aren't there.",
                    pours: ["Tanqueray Gin", "Sloe Gin", "Pernod"]
                },
                { 
                    name: "Dirty Martini", 
                    flavorProfile: "A crisp, highly savory, and salty glass of chilled vodka.", 
                    recipe: ["2 oz Vodka", "1.0 oz Dirty Martini Mix"], 
                    story: "The Diplomat: Our version of a sophisticated classic. We keep the brine in a repurposed oil can. Tastes like a secret handshake—smooth, salty, and a little dangerous.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/il_fullxfull.1268185178_a000.webp", 
                    cardHook: "Shaken or stirred, never noticed.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka"]
                },
                { 
                    name: "Vodka Sour", 
                    flavorProfile: "Chilled vodka balanced with intense sweet and sour elements.", 
                    recipe: ["1.5 oz Vodka", "Fill with Sweet and Sour Mix", "Splash of Lime Juice"], 
                    story: "Catalyst: This drink doesn't cause problems. It's just... present when they happen. It's the catalyst for bar fights, terrible ideas, and waking up with a brand new tattoo.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7999.jpg", 
                    cardHook: "The start of a great story.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka"]
                },
                { 
                    name: "Orchard Whiskey Kick", 
                    flavorProfile: "Smooth whiskey, sour apple, and sweet Sprite. Like apple pie with a punch.", 
                    recipe: ["2 oz Bourbon", "1 oz Apple Pucker", "2 dashes Angostura Bitters", "Top with Sprite"], 
                    story: "Finn's Orchard Kick: Finn, our resident genius, tried to make 'artisanal applejack' in the clubhouse radiator. The radiator exploded. This drink is a much safer tribute to his ambition.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/8152e3c111a698e2a7f072b33b5662906e08d17d/mannart12.jpg", 
                    cardHook: "A tribute to spectacular failures.",
                    pours: ["Woodford Reserve", "WhistlePig", "Michter's", "Jameson Irish Whiskey", "Maker's Mark", "Crown Royal", "Bulleit Bourbon", "Southern Comfort", "Old Grand-Dad Whiskey", "Jim Beam Bourbon"]
                },
                { 
                    name: "Scotch Amaretto Coke", 
                    flavorProfile: "Smoky scotch paired with rich amaretto and refreshing Coke.", 
                    recipe: ["2 oz Scotch Whisky", "1 oz Amaretto", "Fill glass with Coke"], 
                    story: "Crossroads Deal: At the crossroads, you can sell your soul for talent. Or, if you're like Mike, you can accidentally trade it for a half-empty bottle of amaretto. This drink commemorates his poor negotiating skills.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7992.jpg", 
                    cardHook: "To making good deals.",
                    pours: ["Dewars Scotch", "Johnnie Walker Red Label", "Amaretto"]
                },
                { 
                    name: "Purple Hooter", 
                    flavorProfile: "Sweet raspberry, sharp citrus, and a refreshing, bubbling club soda lift.", 
                    recipe: ["1 oz Vodka", "1 oz Raspberry Schnapps", "2 dashes Peychaud's Bitters", "Splash of Lime Juice", "Fill with Club Soda"], 
                    story: "The Night Owl: We're not legally allowed to say why it's called this. Just know that it involves our least-favorite rival club, a gallon of purple paint, and a very surprised owl mascot.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/b53f3ec4d921fabea10c455c27ae09cee7e30d79/aaalchemistsbrew.jpg", 
                    cardHook: "To our purple owl.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka"]
                },
                { 
                    name: "Tequila Elderflower", 
                    flavorProfile: "Agave spirits balanced with floral sweet elderflowers and citrus.", 
                    recipe: ["1.5 oz Tequila", "1 oz Aperol", "0.5 oz St-Germain", "1 oz Lemon Juice"], 
                    story: "High Noon: This one's for when the sun is high and mercy is low. It's sharp, it's bittersweet, and it's got the kick you need to face the rest of the day. We call it the 'Duelist's Drink'.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/271d97ccf4324f5c3e3d7ec301c4fcc8.jpg", 
                    cardHook: "The drink of champions. And losers.",
                    pours: ["El Mayor Tequila", "Jose Cuervo Silver Tequila"]
                },
                { 
                    name: "Mudslide", 
                    flavorProfile: "Rich coffee, sweet cream, and chocolate textures. A decadent dessert pour.", 
                    recipe: ["1 oz Vodka", "1 oz Kahlúa", "1 oz Baileys Irish Cream"], 
                    story: "The Spillway: We once tried to ride our choppers through an active muddy spillway. It was a terrible idea. This drink is a much better, and cleaner, version of that experience.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7997.jpg", 
                    cardHook: "To the shortcuts that weren't.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka"]
                },
                { 
                    name: "Spiced Bourbon Buck", 
                    flavorProfile: "A rich, woody bourbon paired with stone fruits and sharp Sprite.", 
                    recipe: ["2 oz Bourbon", "0.75 oz Lime Juice", "0.5 oz Apricot Brandy", "Top with Sprite", "2 dashes Orange Bitters"], 
                    story: "Turkey Buck: Named for our club secretary, who can talk for three hours without taking a single breath. The drink is dry, spicy, and will leave you speechless. We wish he would try one.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7998.jpg", 
                    cardHook: "For stories that go on too long.",
                    pours: ["Woodford Reserve", "WhistlePig", "Michter's", "Jameson Irish Whiskey", "Maker's Mark", "Crown Royal", "Bulleit Bourbon", "Southern Comfort", "Old Grand-Dad Whiskey", "Jim Beam Bourbon"]
                },
                { 
                    name: "Citrus Elderflower", 
                    flavorProfile: "Rich floral elderflower balanced with sweet cranberry and vodka.", 
                    recipe: ["1.5 oz Vodka", "0.5 oz St-Germain", "Fill with Cranberry Juice"], 
                    story: "Oracle's Kiss: Some lady at a carnival gave our treasurer a 'kiss for good luck.' He woke up three hours later with his wallet gone and a lingering taste of cranberry. We made this to remember.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_8297.jpg", 
                    cardHook: "The future is sweet and flowery.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka", "St-Germain"]
                }, 
                { 
                    name: "Stone Sour", 
                    flavorProfile: "A classic sweet whiskey sour, rounded out with sweet stone fruits.", 
                    recipe: ["1.5 oz Bourbon", "0.5 oz Apricot Brandy", "0.75 oz Lemon Juice", "0.5 oz Orange Juice", "0.5 oz Simple Syrup"], 
                    story: "Desert Wind: Named after the feeling you get after riding through a dust storm in the desert, this drink is sharp, sweet, and requires a little grit to appreciate. For riders who handle challenges.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/c4fb2c246219d2590f58d5805883750a9dc0df86/mannart16.jpg", 
                    cardHook: "Sharp, sweet, and complex.",
                    pours: ["Woodford Reserve", "WhistlePig", "Michter's", "Jameson Irish Whiskey", "Maker's Mark", "Crown Royal", "Bulleit Bourbon", "Southern Comfort", "Old Grand-Dad Whiskey", "Jim Beam Bourbon"]
                },
                { 
                    name: "Blue Lagoon", 
                    flavorProfile: "Electric blue, citrusy, and sweet. Tastes like a 1980s summer beach weekend.", 
                    recipe: ["1 oz Vodka", "1 oz Blue Curacao", "Top with Sweet and Sour Mix"], 
                    story: "The Oasis: We saw this in a fancy magazine and decided to make it our own. Our version is stronger, more questionable, and is best consumed in a garage, not a poolside cabana.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/09df49098aac18eadeeb826a6e5a1f2d.jpg", 
                    cardHook: "Find your oasis.",
                    pours: ["Grey Goose Vodka", "Ketel One Vodka", "Stolichnaya Citros Vodka", "Blue Curacao"]
                },
                { 
                    name: "New York", 
                    flavorProfile: "Clean whiskey sweetened with pomegranate syrup and sharp lime citrus.", 
                    recipe: ["2 oz Bourbon", "0.75 oz Lime Juice", "0.75 oz Grenadine"], 
                    story: "The New Yorker: Named after the city, but probably invented in a basement in Jersey. It's whiskey trying to be a fruit punch, and surprisingly, it pulls it off. Respect the hustle.", 
                    image: "https://raw.githubusercontent.com/aarmax8/Nomads/39a5b0f2968c010f345e51cecd3ad4f3b6f40692/mannart10.jpg", 
                    cardHook: "Start spreading the news.",
                    pours: ["Woodford Reserve", "WhistlePig", "Michter's", "Jameson Irish Whiskey", "Maker's Mark", "Crown Royal", "Bulleit Bourbon", "Southern Comfort", "Old Grand-Dad Whiskey", "Jim Beam Bourbon"]
                }
            ];
        }

        /**
         * Dynamic Ingredient category definitions
         */
        function getIngredientCategories() {
            return {
                'Spirits': {
                    'High-End Whiskey': ['Woodford Reserve', 'WhistlePig', 'Michter\'s'],
                    'Mid-Range Whiskey': ['Jameson Irish Whiskey', 'Maker\'s Mark', 'Travellers Whiskey', 'Wild Turkey 101', 'Crown Royal', 'Bulleit Bourbon'],
                    'Low-End Whiskey': ['Southern Comfort', 'Old Grand-Dad Whiskey', 'Jim Beam Bourbon'],
                    'Scotch': ['Drambuie', 'Johnnie Walker Red Label', 'Dewars Scotch'],
                    'Vodka': ['Grey Goose Vodka', 'Ketel One Vodka', 'Stolichnaya Citros Vodka'], 
                    'Gin': ['Tanqueray Gin'],
                    'Rum': ['Bacardi Rum', 'Captain Morgan Spiced Rum', 'Kraken Black Spiced Rum', 'Malibu Rum'],
                    'Tequila': ['El Mayor Tequila', 'Jose Cuervo Silver Tequila'], 
                    'Brandy': ['E&J Brandy', 'Apricot Brandy']
                },
                'Liqueurs & Schnapps': {
                    'Fruit Liqueurs': ['Sloe Gin', 'Apple Pucker', 'Blue Curacao', 'Cherry Schnapps', 'Cointreau', 'Heering Cherry liqueur', 'Peach Schnapps', 'Raspberry Schnapps', 'Triple Sec', 'Peach Liqueur'], 
                    'Herbal': ['Aperol', 'Jägermeister', 'Pernod', 'St-Germain'],
                    'Cream & Coffee': ['Amaretto', 'Baileys Irish Cream', 'Kahlúa'],
                    'Other': ['Butterscotch Schnapps', 'Root Beer Schnapps']
                },
                'Mixers & Bitters': {
                    'Juices & Sodas': ['Club Soda', 'Coke', 'Cranberry Juice', 'Sprite', 'Lemon Juice', 'Lime Juice', 'Orange Juice', 'Pineapple Juice', 'Tonic Water', 'Sweet and Sour Mix', 'Dirty Martini Mix'],
                    'Bitters': ['Angostura Bitters', 'Orange Bitters', 'Peychaud\'s Bitters', 'Rosemary Lavender Bitters'],
                    'Syrups': ['Grenadine', 'Simple Syrup', 'Passion Fruit Syrup'],
                    'Garnish': ['Cherries']
                }
            };
        }

        const titleFonts = [
            'Rye', 
            'Cinzel', 
            'Black Ops One', 
            'IM Fell DW Pica', 
            'Roboto Condensed'
        ];

        function parseIngredientName(ingStr) {
            if (typeof ingStr !== 'string') return null;
            let name = ingStr.replace(/^[\d./\s-]+(oz|dashes|dash|garnish)\s*/i, '');
            const instructionalPhrases = [ 'Fill glass with ', 'Fill a tall glass with ', 'Fill with ', 'Top with ', 'Splash of ', 'Splash ', '1 teaspoon ', 'Rinse of '];
            for (const phrase of instructionalPhrases) {
                if (name.toLowerCase().startsWith(phrase.toLowerCase())) {
                    name = name.substring(phrase.length);
                    const inIndex = name.toLowerCase().indexOf(' in a');
                    if (inIndex > -1) name = name.substring(0, inIndex);
                    break;
                }
            }
            if(name.toLowerCase().trim().includes('serve on the rocks')) return null;
            return name.trim();
        }
        
        function getIngredientInfo(ingredientName) {
            if (!ingredientName) {
                return { icon: 'fa-cube', colorClass: 'text-gray-400', colorHex: '#9ca3af' };
            }
            const lowerIng = ingredientName.toLowerCase();

            if (['woodford', 'whistlepig', 'michter', 'jameson', 'whiskey', 'bourbon', 'scotch', 'dewar', 'drambuie', 'southern comfort', 'maker', 'grand-dad', 'turkey', 'royal', 'bulleit', 'beam', 'walker', 'roses', 'travellers'].some(s => lowerIng.includes(s))) return { icon: 'fa-whiskey-glass', colorClass: 'text-orange-500', colorHex: '#FF4500' };
            if (['vodka'].some(s => lowerIng.includes(s))) return { icon: 'fa-skull-crossbones', colorClass: 'text-blue-300', colorHex: '#93c5fd' };
            if (['gin'].some(s => lowerIng.includes(s))) return { icon: 'fa-leaf', colorClass: 'text-green-400', colorHex: '#4ade80' };
            if (['rum', 'malibu'].some(s => lowerIng.includes(s))) return { icon: 'fa-anchor', colorClass: 'text-amber-500', colorHex: '#f59e0b' };
            if (['tequila'].some(s => lowerIng.includes(s))) return { icon: 'fa-hat-cowboy-side', colorClass: 'text-amber-400', colorHex: '#fbbf24' };
            if (['brandy'].some(s => lowerIng.includes(s))) return { icon: 'fa-wine-glass', colorClass: 'text-purple-400', colorHex: '#d8b4fe' };
            if (['sloe gin', 'schnapps', 'pucker', 'jägermeister', 'liqueur', 'baileys', 'pernod', 'kahlúa', 'st-germain', 'cointreau', 'amaretto', 'campari', 'blue curacao', 'aperol'].some(l => lowerIng.includes(l))) return { icon: 'fa-mortar-pestle', colorClass: 'text-pink-500', colorHex: '#f472b6' };
            if (lowerIng.includes('bitters')) return { icon: 'fa-eye-dropper', colorClass: 'text-red-500', colorHex: '#ef4444' };
            if (['juice', 'sour mix'].some(j => lowerIng.includes(j))) return { icon: 'fa-lemon', colorClass: 'text-yellow-400', colorHex: '#facc15' };
            if (['syrup', 'grenadine'].some(s => lowerIng.includes(s))) return { icon: 'fa-prescription-bottle', colorClass: 'text-pink-400', colorHex: '#f472b6' };
            return { icon: 'fa-cube', colorClass: 'text-gray-400', colorHex: '#9ca3af' };
        }

        function isDrinkMakeable(drink) {
            return drink.recipe.every(ingStr => {
                const ingName = parseIngredientName(ingStr);
                return ingName === null || barStock[ingName] !== false;
            });
        }

        function setupCocktailData() {
            const initialCocktails = getInitialCocktailData();
            const ingredientCategories = getIngredientCategories();

            const processedCocktails = initialCocktails.map((cocktail) => {
                const categories = new Set();
                const recipeString = cocktail.recipe.join(' ').toLowerCase();
                
                if (recipeString.includes('juice') || recipeString.includes('sour mix')) categories.add('Brunch');
                if (recipeString.includes('club soda') || recipeString.includes('tonic water')) categories.add('Lunch');
                if (recipeString.includes('coke') || recipeString.includes('sprite')) categories.add('Dinner');
                if (recipeString.includes('baileys') || recipeString.includes('kahlúa') || recipeString.includes('cream')) categories.add('Desert');
                
                if (categories.size === 0) categories.add('Lunch'); 

                let titleColor = '#f59e0b';
                let primarySpirit = 'Other';

                // Map main spirit category
                const spiritOrder = ['High-End Whiskey', 'Mid-Range Whiskey', 'Low-End Whiskey', 'Scotch', 'Vodka', 'Gin', 'Rum', 'Tequila', 'Brandy'];
                let mainIngredient = null;

                for (const spiritType of spiritOrder) {
                    const spirits = ingredientCategories.Spirits[spiritType];
                    const foundSpirit = cocktail.recipe.map(parseIngredientName).find(ing => ing && spirits.includes(ing));
                    if (foundSpirit) {
                        mainIngredient = foundSpirit;
                        primarySpirit = spiritType;
                        break;
                    }
                }
                
                if (mainIngredient) titleColor = getIngredientInfo(mainIngredient).colorHex;

                if (primarySpirit.includes('Whiskey')) {
                    titleColor = '#FF4500';
                }

                return { ...cocktail, category: Array.from(categories), titleColor, primarySpirit };
            });

            cocktails = processedCocktails;
            cocktails.sort((a, b) => a.name.localeCompare(b.name));

            const barcodeCard = {
                name: "Scan to Connect",
                isBarcode: true,
                image: 'https://raw.githubusercontent.com/aarmax8/Nomads/e4ef12fb2bff260fe0d7de78741a3ec2307e381d/3dbarcode.JPG?raw=true',
                recipe: [],
                flavorProfile: "A gateway to the digital road.",
                cardHook: "Point your camera here.",
                category: [],
                titleColor: '#f59e0b',
                primarySpirit: 'Barcode',
                pours: []
            };
            cocktails.unshift(barcodeCard);
        }

        function renderMenu(itemsToRender) {
            menuGrid.innerHTML = '';
            if (itemsToRender.length === 0) {
                menuGrid.innerHTML = `
                    <div class="text-center w-full p-10">
                        <h3 class="text-2xl font-cinzel text-amber-400">No Matching Drinks</h3>
                        <p class="text-gray-400 mt-2">Try adjusting your filters in the Browse panel.</p>
                    </div>`;
                return;
            }

            itemsToRender.forEach((item, index) => {
                if (item.isBarcode) {
                    renderBarcodeCard(item, index);
                } else {
                    renderDrinkCard(item, index);
                }
            });
        }

        function renderBarcodeCard(item, index) {
            const nonBarcodeCocktails = cocktails.filter(c => !c.isBarcode);
            const spiritGroups = {};
            nonBarcodeCocktails.forEach(drink => {
                const groupName = drink.primarySpirit;
                if (!spiritGroups[groupName]) {
                    spiritGroups[groupName] = [];
                }
                spiritGroups[groupName].push(drink);
            });

            const displayOrder = ['High-End Whiskey', 'Mid-Range Whiskey', 'Low-End Whiskey', 'Scotch', 'Vodka', 'Gin', 'Rum', 'Tequila', 'Brandy', 'Other'];
            let listHtml = '';
            
            displayOrder.forEach(spiritCategory => {
                const drinksInGroup = spiritGroups[spiritCategory];
                if (drinksInGroup && drinksInGroup.length > 0) {
                    listHtml += `<div class="toc-category-header">${spiritCategory}</div>`;
                    drinksInGroup.sort((a, b) => a.name.localeCompare(b.name));
                    
                    drinksInGroup.forEach(drink => {
                        const originalIndex = cocktails.findIndex(c => c.name === drink.name); 
                        const tocFont = titleFonts[originalIndex % titleFonts.length];
                        
                        listHtml += `
                            <div class="toc-item" 
                                data-name="${drink.name}" 
                                style="color: ${drink.titleColor}; 
                                        border-color: ${drink.titleColor}80;
                                        font-family: '${tocFont}', sans-serif;">
                                ${drink.name}
                            </div>`;
                    });
                }
            });

            const cardHtml = `
                <div class="drink-card" data-is-barcode="true">
                    <div class="drink-card-inner">
                        <div class="drink-card-front">
                            <div class="text-center">
                                <p class="text-md text-amber-400 font-cinzel">
                                    <i class="fas fa-undo-alt mr-2"></i> **Flip Card for Deck Index**
                                </p>
                            </div>
                            <img src="${item.image}" alt="3D Barcode">
                            <div class="text-center mt-2">
                                <h3 class="drink-card-title">${item.name}</h3>
                                <div class="card-footer text-xs">
                                    <p class="mb-2 text-amber-500">${item.cardHook}</p>
                                    <p class="font-normal not-italic leading-tight text-gray-400"><strong class="text-gray-300">To Install:</strong> Tap Share then 'Add to Home Screen'.</p>
                                </div>
                            </div>
                        </div>
                        <div class="drink-card-back">
                            <div class="card-header-front" style="border-bottom: 2px double rgba(133, 77, 14, 0.5); padding-top: 1rem; padding-bottom: 0.5rem;">
                                <h3 class="drink-card-title" style="font-family: 'Cinzel', cursive; font-size: 1.75rem; color: #f59e0b;">The Full Deck</h3>
                            </div>
                            <div class="barcode-back-content">
                                ${listHtml}
                            </div>
                            <div class="card-footer-back" style="min-height: 40px; font-size: 0.8rem; font-style: italic; color: #8e8e93; border-top: 1px solid rgba(133, 77, 14, 0.5);">
                                Tap a name to jump to the card
                            </div>
                        </div>
                    </div>
                </div>`;
            menuGrid.insertAdjacentHTML('beforeend', cardHtml);
        }

        function renderDrinkCard(item, index) {
            const isUnavailable = !isDrinkMakeable(item);
            const titleFont = titleFonts[index % titleFonts.length];
            const drinkFavoriteClass = favoriteDrinks.includes(item.name) ? 'is-favorite' : '';

            const recipeHtml = item.recipe.map(r => {
                const ingName = parseIngredientName(r) || r;
                const ingInfo = getIngredientInfo(ingName);
                return `<li><i class="fas ${ingInfo.icon} ${ingInfo.colorClass}"></i><span>${r}</span></li>`;
            }).join('');

            // Format premium pour options badges on the front of the cards
            let poursHtml = '';
            if (item.pours && item.pours.length > 0) {
                const filteredPours = item.pours.filter(p => barStock[p] !== false);
                if (filteredPours.length > 0) {
                    const badges = filteredPours.map(p => `<span class="card-pour-badge">${p}</span>`).join('');
                    poursHtml = `
                        <div class="card-pour-options">
                            <p class="text-gray-400 text-[10px] uppercase font-bold tracking-wider mb-1">Pour Options:</p>
                            <div class="flex flex-wrap">${badges}</div>
                        </div>`;
                }
            }

            const cardHtml = `
                <div class="drink-card ${isUnavailable ? 'is-unavailable' : ''}" data-name="${item.name}">
                    <div class="drink-card-inner">
                        <div class="drink-card-front">
                             <div class="card-header-front">
                                 <h3 class="drink-card-title" style="font-family: '${titleFont}', sans-serif; line-height: 1.1; color: ${item.titleColor};">${item.name}</h3>
                                 <button class="favorite-btn ${drinkFavoriteClass}" data-type="drink"><i class="fas fa-heart"></i></button>
                             </div>
                             <div class="px-6 pt-2 text-center flex-shrink-0">
                                 <p class="text-[13px] font-cinzel text-gray-300 leading-snug">${item.flavorProfile}</p>
                             </div>
                             <div class="recipe-content">
                                 <ul class="recipe-list-front">${recipeHtml}</ul>
                             </div>
                             ${poursHtml}
                             <div class="card-hook-tagline">${item.cardHook}</div>
                             <div class="card-footer"></div>
                        </div>
                        <div class="drink-card-back lazy-bg ${!item.image ? 'no-image' : ''}" ${item.image ? `data-bg="url('${item.image}')"` : ''}>
                           <div class="card-back-content">
                                <p class="story-text">${item.story}</p>
                           </div>
                            <div class="card-footer-back">Origin: ${item.name}</div>
                        </div>
                    </div>
                </div>`;
            menuGrid.insertAdjacentHTML('beforeend', cardHtml);
        }

        function setupLazyLoading() {
            if ("IntersectionObserver" in window) {
                const imageObserver = new IntersectionObserver((entries) => {
                    entries.forEach(entry => {
                        const card = entry.target;
                        const imageContainer = card.querySelector('.lazy-bg');
                        if (!imageContainer) return;

                        if (entry.isIntersecting) {
                            const imageUrl = imageContainer.dataset.bg;
                            if (imageUrl) {
                                imageContainer.style.setProperty('--bg-image', imageUrl);
                            }
                        } else {
                            imageContainer.style.removeProperty('--bg-image');
                        }
                    });
                }, { 
                    root: menuGrid, 
                    rootMargin: "300px 0px"
                }); 
                
                const lazyCards = document.querySelectorAll('.drink-card:not([data-is-barcode="true"])');
                lazyCards.forEach(card => imageObserver.observe(card));
            } else {
                document.querySelectorAll('.lazy-bg').forEach(img => {
                    const imageUrl = img.dataset.bg;
                    if (imageUrl) {
                        img.style.setProperty('--bg-image', imageUrl);
                    }
                });
            }
        }

        function renderFavoritesModal() {
            const container = document.getElementById('favorites-list-container');
            if (!container) return;
            
            if (favoriteDrinks.length === 0) {
                container.innerHTML = `<p class="text-gray-400 italic text-center">Tap the heart on any card to add it to your favorites.</p>`;
                return;
            }

            const itemsHtml = favoriteDrinks.map(name => {
                const cardData = cocktails.find(c => c.name === name);
                if (!cardData) return '';
                const iconInfo = getIngredientInfo(parseIngredientName(cardData.recipe[0] || ''));
                return `
                    <div class="favorite-item" data-name="${cardData.name}" data-view="drink">
                        <i class="fas ${iconInfo.icon} text-xl w-10 text-center ${iconInfo.colorClass}"></i>
                        <div class="ml-4">
                            <h4 class="font-bold text-lg text-white">${cardData.name}</h4>
                            <p class="text-sm text-gray-400">${cardData.flavorProfile}</p>
                        </div>
                    </div>`;
            }).join('<div class="h-3"></div>');

            container.innerHTML = itemsHtml;
        }

        function renderBarStockModal() {
            const contentContainer = document.getElementById('bar-stock-content');
            if (!contentContainer) return;
            contentContainer.innerHTML = '';
            
            const ingredientCategories = getIngredientCategories();

            const renderButtonsForStatus = (status) => {
                let html = `<h3 class="text-xl ${status ? 'text-green-400' : 'text-red-400'} mb-4 font-black-ops">${status ? 'IN STOCK' : 'OUT OF STOCK'}</h3>`;
                let hasAnyContent = false;
                
                Object.keys(ingredientCategories).forEach(mainCategoryName => {
                    let mainCategoryHtml = ''; 
                    let hasContentInMainCategory = false;
                    
                    Object.keys(ingredientCategories[mainCategoryName]).forEach(subCategoryName => {
                        const subCategoryIngredients = ingredientCategories[mainCategoryName][subCategoryName]
                            .filter(ing => barStock[ing] === status)
                            .map(ing => `<button data-ingredient="${ing}" class="ingredient-btn text-sm text-white py-1 px-4 transition-colors bg-white/5 border border-white/10 hover:bg-white/15 rounded-lg">${ing}</button>`)
                            .join('');
                        
                        if (subCategoryIngredients.length > 0) {
                            hasContentInMainCategory = true;
                            hasAnyContent = true;
                            mainCategoryHtml += `
                                <div class="mb-3">
                                    <h5 class="text-md font-bold text-gray-400 mb-2">${subCategoryName}</h5>
                                    <div class="flex flex-wrap gap-2">${subCategoryIngredients}</div>
                                </div>`;
                        }
                    });
                    
                    if (hasContentInMainCategory) {
                         html += `
                            <div class="mb-6">
                                <h4 class="text-xl font-rye text-amber-500 mb-3 border-b-2 border-gray-600 pb-2">${mainCategoryName}</h4>
                                ${mainCategoryHtml}
                            </div>`;
                    }
                });
                
                if (!hasAnyContent) { 
                    html += `<p class="text-gray-500 italic">No ingredients match this status.</p>`; 
                }
                return html;
            };
            
            contentContainer.innerHTML = renderButtonsForStatus(true) + '<div class="border-t border-white/10 my-6"></div>' + renderButtonsForStatus(false);
            
            contentContainer.querySelectorAll('.ingredient-btn').forEach(btn => {
                btn.addEventListener('click', () => toggleStock(btn.dataset.ingredient));
            });
        }

        function initializeFilterModal() {
            const filterModalContent = document.getElementById('filter-modal-content');
            if (!filterModalContent) return;

            const ingredientCategories = getIngredientCategories();
            
            const favoritesFilter = `
                <div class="flex items-center justify-between bg-black/20 p-3 rounded-lg">
                    <h3 class="text-lg text-amber-500 font-rye tracking-wider">Show Favorites Only</h3>
                    <label class="relative inline-flex items-center cursor-pointer">
                        <input type="checkbox" id="favorites-filter-toggle" class="sr-only peer">
                        <div class="w-11 h-6 bg-gray-600 rounded-full peer peer-focus:ring-2 peer-focus:ring-amber-500 peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-0.5 after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-amber-600"></div>
                    </label>
                </div>`;

             const categoryFilters = `
                 <div>
                     <h3 class="text-lg text-amber-500 mb-2 font-rye tracking-wider">Food Pairing</h3>
                     <div id="filter-group-category" class="flex flex-wrap gap-3">
                          <button data-category="all" class="filter-pill">The Full Deck</button>
                          <button data-category="Brunch" class="filter-pill">Brunch</button>
                          <button data-category="Lunch" class="filter-pill">Lunch</button>
                          <button data-category="Dinner" class="filter-pill">Dinner</button>
                          <button data-category="Desert" class="filter-pill">Desert</button>
                     </div>
                 </div>`;
            
            const spiritCategories = Object.keys(ingredientCategories.Spirits);
            const spiritFilters = `
                 <div>
                     <h3 class="text-lg text-amber-500 mb-2 font-rye tracking-wider">Spirit</h3>
                     <div id="filter-group-spirit" class="flex flex-wrap gap-3">
                          ${spiritCategories.map(spirit => `<button data-spirit="${spirit}" class="filter-pill">${spirit}</button>`).join('')}
                     </div>
                 </div>`;

            const allIngredients = Object.values(ingredientCategories)
                .flatMap(mainCat => Object.values(mainCat).flat())
                .sort();
            
            const ingredientFilter = `
                 <div>
                     <h3 class="text-lg text-amber-500 mb-2 font-rye tracking-wider">Contains Ingredient</h3>
                     <select id="ingredient-filter-select" class="w-full bg-gray-800 border border-gray-600 rounded-lg p-2 text-white focus:outline-none focus:ring-2 focus:ring-amber-500">
                          <option value="">Any Ingredient</option>
                          ${allIngredients.map(ing => `<option value="${ing}">${ing}</option>`).join('')}
                     </select>
                 </div>`;

            filterModalContent.innerHTML = `
                 <div class="space-y-4">
                      ${favoritesFilter}
                      <div class="border-t border-white/10 my-4"></div>
                      ${categoryFilters}
                      ${spiritFilters}
                      ${ingredientFilter}
                 </div>`;
            
            updatePillsFromState();
        }

        function updatePillsFromState() {
            document.querySelectorAll('#filter-modal .filter-pill').forEach(p => p.classList.remove('is-active'));
            document.querySelector(`#filter-group-category .filter-pill[data-category="${activeFilters.category}"]`)?.classList.add('is-active');
            if(activeFilters.spirit) {
                document.querySelector(`#filter-group-spirit .filter-pill[data-spirit="${activeFilters.spirit}"]`)?.classList.add('is-active');
            }
            const ingredientSelect = document.getElementById('ingredient-filter-select');
            if (ingredientSelect) {
                ingredientSelect.value = activeFilters.ingredient || '';
            }
            const favToggle = document.getElementById('favorites-filter-toggle');
            if (favToggle) {
                favToggle.checked = activeFilters.showFavoritesOnly;
            }
        }

        function initializeFavorites() {
            const savedDrinkFavs = localStorage.getItem(DRINKS_FAVORITES_KEY);
            if (savedDrinkFavs) {
                try {
                    favoriteDrinks = JSON.parse(savedDrinkFavs);
                } catch (e) {
                    favoriteDrinks = [];
                }
            }
        }

        function toggleFavorite(cardName, starButton) {
            const index = favoriteDrinks.indexOf(cardName);
            if (index > -1) {
                favoriteDrinks.splice(index, 1); 
                starButton.classList.remove('is-favorite');
            } else {
                favoriteDrinks.push(cardName); 
                starButton.classList.add('is-favorite');
            }
            localStorage.setItem(DRINKS_FAVORITES_KEY, JSON.stringify(favoriteDrinks));
            updateFilterMenuButtonState();
        }
        
        function initializeBarStock() {
            const savedStockJSON = localStorage.getItem(STOCK_STORAGE_KEY);
            const allIngredients = Object.values(getIngredientCategories())
                .flatMap(mainCat => Object.values(mainCat).flat());
            
            let savedStock = {};
            if (savedStockJSON) {
                try {
                    savedStock = JSON.parse(savedStockJSON);
                } catch (e) {
                    savedStock = {};
                }
            }

            const newStock = {};
            allIngredients.forEach(ing => {
                newStock[ing] = savedStock.hasOwnProperty(ing) ? savedStock[ing] : true;
            });
            
            barStock = newStock;
            localStorage.setItem(STOCK_STORAGE_KEY, JSON.stringify(barStock));
        }

        function toggleStock(ingredient) {
            if (barStock.hasOwnProperty(ingredient)) {
                 barStock[ingredient] = !barStock[ingredient];
            } else {
                 barStock[ingredient] = true;
            }
            localStorage.setItem(STOCK_STORAGE_KEY, JSON.stringify(barStock));
            renderBarStockModal();
            applyAndRenderFilters();
        }

        function applyAndRenderFilters() {
            const barcodeCard = cocktails.find(c => c.isBarcode);
            let drinkableCocktails = cocktails.filter(c => !c.isBarcode);
            const ingredientCategories = getIngredientCategories();

            if (activeFilters.category && activeFilters.category !== 'all') {
                drinkableCocktails = drinkableCocktails.filter(item => item.category.includes(activeFilters.category));
            }

            if (activeFilters.spirit) {
                const spiritsInFamily = ingredientCategories.Spirits[activeFilters.spirit] || [];
                drinkableCocktails = drinkableCocktails.filter(drink =>
                    drink.recipe.some(recipeLine => {
                        const ingredientName = parseIngredientName(recipeLine);
                        return ingredientName && spiritsInFamily.includes(ingredientName);
                    })
                );
            }

            if (activeFilters.ingredient) {
                 drinkableCocktails = drinkableCocktails.filter(drink =>
                     drink.recipe.some(recipeLine => {
                         const ingredientName = parseIngredientName(recipeLine);
                         return ingredientName === activeFilters.ingredient;
                     })
                 );
            }
            
            if (activeFilters.showFavoritesOnly) {
                drinkableCocktails = drinkableCocktails.filter(drink => favoriteDrinks.includes(drink.name));
            }

            const itemsToRender = barcodeCard ? [barcodeCard, ...drinkableCocktails] : drinkableCocktails;

            renderMenu(itemsToRender);
            setupLazyLoading(); 
            setCardView(isGlobalTarotView); 
            updateActiveCard(); 
            updateFilterMenuButtonState(); 
        }

        function setCardView(isStoryView) {
            const cards = document.querySelectorAll('#menu-grid .drink-card');
            const toggleBtn = document.getElementById('toggle-view-btn-main'); 
            const storyToggleLabel = document.getElementById('story-toggle-label');
            
            isGlobalTarotView = isStoryView; 

            if (storyToggleLabel) {
                storyToggleLabel.textContent = isGlobalTarotView ? "Recipe View" : "Story View";
            }

            if (toggleBtn) {
                const icon = toggleBtn.querySelector('i');
                if (icon) {
                    if (isGlobalTarotView) {
                        icon.className = 'fas fa-scroll';
                    } else {
                        icon.className = 'fas fa-book-open';
                    }
                }
            }

            cards.forEach(card => {
                if (card.dataset && !card.dataset.isBarcode) {
                    card.classList.toggle('is-flipped', isGlobalTarotView);
                }
            });
        }

        function toggleLayoutMode() {
            isDesktopLayout = !isDesktopLayout;
            const menuGridEl = document.getElementById('menu-grid');
            const layoutBtnLabel = document.getElementById('layout-btn-label');
            const layoutIcon = document.querySelector('#action-layout-btn i');

            if (isDesktopLayout) {
                menuGridEl.className = 'grid-view';
                if (layoutBtnLabel) layoutBtnLabel.textContent = "Swipe View";
                if (layoutIcon) layoutIcon.className = 'fas fa-sliders';
            } else {
                menuGridEl.className = 'carousel-view';
                if (layoutBtnLabel) layoutBtnLabel.textContent = "Desktop View";
                if (layoutIcon) layoutIcon.className = 'fas fa-grip';
            }
            
            applyAndRenderFilters();
        }

        function updateActiveCard() {
            if (isDesktopLayout) return null; 

            const containerRect = menuGrid.getBoundingClientRect();
            const containerCenter = containerRect.left + containerRect.width / 2;
            let closestCard = null;
            let minDistance = Infinity;

            menuGrid.querySelectorAll('.drink-card').forEach(card => {
                const cardRect = card.getBoundingClientRect();
                const cardCenter = cardRect.left + cardRect.width / 2;
                const distance = Math.abs(containerCenter - cardCenter);

                if (distance < minDistance) {
                    minDistance = distance;
                    closestCard = card;
                }
            });
            
            if (closestCard) {
                menuGrid.querySelectorAll('.drink-card.is-active').forEach(c => c.classList.remove('is-active'));
                closestCard.classList.add('is-active');
                return closestCard;
            }
            return null;
        }

        function getCurrentActiveCard() {
            if (isDesktopLayout) return document.querySelector('.drink-card');
            
            const cards = menuGrid.querySelectorAll('.drink-card');
            const containerRect = menuGrid.getBoundingClientRect();
            const containerCenter = containerRect.left + containerRect.width / 2;
            let closestCard = null;
            let minDistance = Infinity;

            cards.forEach(card => {
                const cardRect = card.getBoundingClientRect();
                const cardCenter = cardRect.left + cardRect.width / 2;
                const distance = Math.abs(containerCenter - cardCenter);

                if (distance < minDistance) {
                    minDistance = distance;
                    closestCard = card;
                }
            });
            return closestCard;
        }

        function highlightAndScrollToCard(card) {
            card.scrollIntoView({ behavior: 'smooth', block: 'nearest', inline: 'center' });
            document.querySelectorAll('.is-highlighted').forEach(c => c.classList.remove('is-highlighted'));
            card.classList.add('is-highlighted');
            setTimeout(() => card.classList.remove('is-highlighted'), 2000);
        }
        
        function updateFilterMenuButtonState() {
            const filtersBtn = document.getElementById('action-filters-btn');
            if (filtersBtn) {
                const isFilterActive = activeFilters.category !== 'all' || 
                                       activeFilters.spirit !== null || 
                                       activeFilters.ingredient !== null || 
                                       activeFilters.showFavoritesOnly;
                filtersBtn.classList.toggle('is-active-filter', isFilterActive);
            }
            
            const favoritesBtn = document.getElementById('action-favorites-btn');
            if (favoritesBtn) {
                favoritesBtn.classList.toggle('is-active', favoriteDrinks.length > 0);
            }
        }

        function closeModal(modalElement) {
            if (!modalElement) return;
            modalElement.classList.add('opacity-0');
            setTimeout(() => {
                modalElement.classList.add('hidden');
            }, 300); 
        }
        
        function handleToggleViewClick() {
             if (isToggleThrottled) return;

             const cardToRestore = getCurrentActiveCard(); 
             if (!cardToRestore) return; 

             if (!isDesktopLayout) {
                 menuGrid.style.scrollSnapType = 'none';
                 menuGrid.classList.add('disable-animation');
             }
             
             isToggleThrottled = true;
             setCardView(!isGlobalTarotView);

             if (!isDesktopLayout) {
                 cardToRestore.scrollIntoView({ behavior: 'instant', block: 'nearest', inline: 'center' });
             }
             
             setTimeout(() => {
                 if (!isDesktopLayout) {
                     menuGrid.classList.remove('disable-animation');
                     menuGrid.style.scrollSnapType = 'x mandatory';
                 }
                 isToggleThrottled = false;
             }, 100);
        }

        function addSplashEventListeners() {
            const splashScreen = document.getElementById('splash-screen');
            const splashSeenKey = 'nomads_splash_seen_v3';
            
            if (splashScreen) {
                if (sessionStorage.getItem(splashSeenKey) === 'true') {
                    splashScreen.style.transition = 'none'; 
                    splashScreen.classList.add('is-hidden');
                } else {
                    splashScreen.addEventListener('click', () => {
                        splashScreen.classList.add('is-hidden');
                        sessionStorage.setItem(splashSeenKey, 'true');
                    }, { once: true }); 
                }
            }
        }

        function addMenuGridEventListeners() {
            menuGrid.addEventListener('click', e => {
                const favoriteButton = e.target.closest('.favorite-btn');
                if (favoriteButton) {
                    e.stopPropagation(); 
                    const cardName = e.target.closest('.drink-card').dataset.name;
                    toggleFavorite(cardName, favoriteButton);
                    return;
                }
                
                const tocItem = e.target.closest('.toc-item');
                if (tocItem) {
                    e.stopPropagation(); 
                    const cardName = tocItem.dataset.name;
                    const cardToScroll = menuGrid.querySelector(`.drink-card[data-name="${cardName}"]`);
                    if (cardToScroll) {
                        if (!isDesktopLayout) {
                            menuGrid.style.scrollSnapType = 'none'; 
                        }
                        
                        const barcodeCard = tocItem.closest('.drink-card');
                        if (barcodeCard) {
                            barcodeCard.classList.remove('is-flipped');
                        }
                        
                        highlightAndScrollToCard(cardToScroll);
                        cardToScroll.classList.remove('is-flipped');
                        setCardView(false); 
                        
                        if (!isDesktopLayout) {
                            setTimeout(() => {
                                menuGrid.style.scrollSnapType = 'x mandatory';
                            }, 800);
                        }
                    }
                    return;
                }

                const cardInner = e.target.closest('.drink-card-inner');
                 if (cardInner) {
                     const card = cardInner.closest('.drink-card');
                     if(card) {
                         card.classList.toggle('is-flipped');
                     }
                 }
            });

            let scrollTimeout;
            menuGrid.addEventListener('scroll', () => {
                if (isDesktopLayout) return;
                clearTimeout(scrollTimeout);
                scrollTimeout = setTimeout(updateActiveCard, 150);
            });
        }

        function addActionBarEventListeners() {
            document.getElementById('action-filters-btn')?.addEventListener('click', () => {
                updatePillsFromState(); 
                filterModal.classList.remove('hidden');
                setTimeout(() => filterModal.classList.remove('opacity-0'), 10);
            });
            
            document.getElementById('action-favorites-btn')?.addEventListener('click', () => {
                renderFavoritesModal(); 
                favoritesModal.classList.remove('hidden');
                setTimeout(() => favoritesModal.classList.remove('opacity-0'), 10);
            });

            document.getElementById('action-layout-btn')?.addEventListener('click', () => {
                toggleLayoutMode();
            });
            
            document.getElementById('action-stock-btn')?.addEventListener('click', () => {
                renderBarStockModal();
                barStockModal.classList.remove('hidden');
                setTimeout(() => barStockModal.classList.remove('opacity-0'), 10);
            });

            randomDrinkBtn?.addEventListener('click', () => {
                const allDrinkCards = document.querySelectorAll('.drink-card:not([data-is-barcode="true"])');
                if (allDrinkCards.length === 0) return; 
                const randomIndex = Math.floor(Math.random() * allDrinkCards.length);
                const randomCard = allDrinkCards[randomIndex];
                randomCard.classList.remove('is-flipped'); 
                highlightAndScrollToCard(randomCard);
            });
        }

        function addModalEventListeners() {
            document.querySelectorAll('.modal').forEach(modal => {
                modal.addEventListener('click', (e) => {
                    if (e.target === modal) {
                        closeModal(modal);
                    }
                });
            });

            document.getElementById('close-favorites-btn')?.addEventListener('click', () => closeModal(favoritesModal));
            document.getElementById('favorites-list-container').addEventListener('click', (e) => {
                 const favoriteItem = e.target.closest('.favorite-item');
                 if (favoriteItem) {
                     const cardName = favoriteItem.dataset.name;
                     const cardEl = document.querySelector(`.drink-card[data-name="${cardName}"]`);
                     if (cardEl) {
                         if (favoriteItem.dataset.view === 'drink') {
                             cardEl.classList.remove('is-flipped');
                         }
                         highlightAndScrollToCard(cardEl);
                     }
                     closeModal(favoritesModal);
                 }
            });

            document.getElementById('close-stock-btn')?.addEventListener('click', () => closeModal(barStockModal));
            document.getElementById('close-filter-btn')?.addEventListener('click', () => closeModal(filterModal));
            
            document.getElementById('apply-filters-btn')?.addEventListener('click', () => {
                applyAndRenderFilters();
                closeModal(filterModal);
            });
            
            document.getElementById('reset-filters-btn')?.addEventListener('click', () => {
                activeFilters = { category: 'all', spirit: null, ingredient: null, showFavoritesOnly: false };
                updatePillsFromState();
                applyAndRenderFilters();
            });
            
            const filterContent = document.getElementById('filter-modal-content');
            if (filterContent) {
                filterContent.addEventListener('click', (e) => {
                    const pill = e.target.closest('.filter-pill');
                    if (!pill) return;
                    const categoryGroup = e.target.closest('#filter-group-category');
                    const spiritGroup = e.target.closest('#filter-group-spirit');
                    
                    if (categoryGroup) {
                        activeFilters.category = pill.dataset.category;
                        categoryGroup.querySelectorAll('.filter-pill').forEach(p => p.classList.remove('is-active'));
                        pill.classList.add('is-active');
                    } else if (spiritGroup) {
                        const spirit = pill.dataset.spirit;
                        if (activeFilters.spirit === spirit) {
                            activeFilters.spirit = null;
                            pill.classList.remove('is-active');
                        } else {
                            activeFilters.spirit = spirit;
                            spiritGroup.querySelectorAll('.filter-pill').forEach(p => p.classList.remove('is-active'));
                            pill.classList.add('is-active');
                        }
                    }
                });
                
                filterContent.addEventListener('change', (e) => {
                    if (e.target.id === 'ingredient-filter-select') {
                        activeFilters.ingredient = e.target.value || null;
                    } else if (e.target.id === 'favorites-filter-toggle') {
                        activeFilters.showFavoritesOnly = e.target.checked;
                    }
                });
            }
        }

        function addFooterEventListeners() {
            document.getElementById('scroll-home-btn')?.addEventListener('click', () => {
                if (isDesktopLayout) {
                    const firstCard = document.querySelector('.drink-card');
                    if (firstCard) firstCard.scrollIntoView({ behavior: 'smooth' });
                } else {
                    menuGrid.scrollTo({ left: 0, behavior: 'smooth' });
                }
                setTimeout(updateActiveCard, 600);
            });

            document.getElementById('scroll-prev-btn')?.addEventListener('click', () => {
                const cards = Array.from(menuGrid.querySelectorAll('.drink-card'));
                if (cards.length === 0) return;
                const activeCard = getCurrentActiveCard() || cards[0];
                const activeIndex = cards.indexOf(activeCard);
                const targetIndex = Math.max(0, activeIndex - 1); 
                if (activeIndex !== targetIndex) {
                    cards[targetIndex].scrollIntoView({ behavior: 'smooth', block: 'nearest', inline: 'center' });
                }
            });

            document.getElementById('scroll-next-btn')?.addEventListener('click', () => {
                const cards = Array.from(menuGrid.querySelectorAll('.drink-card'));
                if (cards.length === 0) return;
                const activeCard = getCurrentActiveCard() || cards[0];
                const activeIndex = cards.indexOf(activeCard);
                const targetIndex = Math.min(cards.length - 1, activeIndex + 1); 
                if (activeIndex !== targetIndex) {
                    cards[targetIndex].scrollIntoView({ behavior: 'smooth', block: 'nearest', inline: 'center' });
                }
            });
            
            document.getElementById('toggle-view-btn-main')?.addEventListener('click', handleToggleViewClick);
        }

        function initApp() {
            menuGrid = document.getElementById('menu-grid');
            barStockModal = document.getElementById('bar-stock-modal');
            filterModal = document.getElementById('filter-modal');
            favoritesModal = document.getElementById('favorites-modal');
            randomDrinkBtn = document.getElementById('action-random-btn');

            // Detect wide layouts on initialize
            if (window.innerWidth >= 1024) {
                isDesktopLayout = true;
                menuGrid.className = 'grid-view';
                const layoutBtnLabel = document.getElementById('layout-btn-label');
                const layoutIcon = document.querySelector('#action-layout-btn i');
                if (layoutBtnLabel) layoutBtnLabel.textContent = "Swipe View";
                if (layoutIcon) layoutIcon.className = 'fas fa-sliders';
            }

            try {
                setupCocktailData();
                initializeFavorites();
                initializeBarStock();
                initializeFilterModal(); 
                applyAndRenderFilters(); 
                updateFilterMenuButtonState(); 
            } catch (error) {
                console.error("Critical Application Setup Failure:", error);
                menuGrid.innerHTML = `
                    <div class="text-center w-full p-10">
                        <h3 class="text-2xl font-cinzel text-red-400">Application Error</h3>
                        <p class="text-gray-400 mt-2">Could not properly load menu data modules.</p>
                    </div>`;
                return;
            }
            
            addSplashEventListeners();
            addMenuGridEventListeners();
            addModalEventListeners();
            addActionBarEventListeners();
            addFooterEventListeners();
        }

        document.addEventListener('DOMContentLoaded', initApp);
    </script>
</body>
</html>
