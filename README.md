<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>DILLIGAF Menu Studio</title>

<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-title" content="Nomad's">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<link rel="apple-touch-icon" href="https://raw.githubusercontent.com/aarmax8/Nomads/b15a4394afade6bb543c1ece00102771641d1c82/Nicon5.png">

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

    #action-bar .footer-btn { width: 80px; }
    #action-bar .footer-btn i { font-size: 1.5rem; margin-bottom: 0.2rem; }
    #action-bar .footer-btn span { font-size: 0.8rem; font-weight: 700; }

    #action-bar .footer-btn.is-active-filter { color: #f59e0b; }
    #action-bar .footer-btn.is-active-filter i { color: #f59e0b; }
    #action-bar #action-favorites-btn.is-active { color: #f59e0b; }
    #action-bar #action-favorites-btn.is-active i { color: #f59e0b; }
    #action-bar .footer-btn:not(#action-favorites-btn) { color: #f59e0b; }
    #action-bar .footer-btn:not(#action-favorites-btn) i { color: #f59e0b; }

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

    #menu-grid.disable-animation .drink-card-inner { transition: none !important; }

    #menu-grid::-webkit-scrollbar { width: 8px; height: 8px; }
    #menu-grid::-webkit-scrollbar-track { background: rgba(0,0,0,0.5); border-radius: 4px; }
    #menu-grid::-webkit-scrollbar-thumb {
        background-color: #f59e0b;
        border-radius: 4px;
        border: 2px solid rgba(0,0,0,0.5);
    }
    #menu-grid::-webkit-scrollbar-thumb:hover { background-color: #fbbf24; }
    #menu-grid { scrollbar-width: thin; scrollbar-color: #f59e0b rgba(0,0,0,0.5); }

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

    .carousel-view .drink-card {
        flex: 0 0 80%;
        scroll-snap-align: center;
        margin-left: auto;
        margin-right: auto;
    }
    .carousel-view > .drink-card:first-child { margin-left: calc((100% - 80%) / 2); }
    .carousel-view > .drink-card:last-child { margin-right: calc((100% - 80%) / 2); }

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

    .drink-card.is-flipped .drink-card-inner { transform: rotateY(180deg); }
    .drink-card.is-active .drink-card-inner { box-shadow: 0 0 25px 8px rgba(45, 212, 191, 0.5); }
    .drink-card.is-active.is-flipped .drink-card-inner { box-shadow: 0 0 25px 8px rgba(245, 158, 11, 0.5); }
    .drink-card.is-highlighted .drink-card-inner { box-shadow: 0 0 30px 10px rgba(245, 158, 11, 0.8); }

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
    .recipe-list-front li.is-missing { color: #6b7280; text-decoration: line-through; }

    /* Pour Option Badges Area */
    .card-pour-options {
        padding: 0.5rem 1.25rem;
        background: rgba(0, 0, 0, 0.3);
        border-top: 1px solid rgba(255, 255, 255, 0.05);
        font-family: 'Roboto Condensed', sans-serif;
        font-size: 0.8rem;
        flex-shrink: 0;
        max-height: 132px;
        overflow-y: auto;
    }
    .card-pour-options::-webkit-scrollbar { width: 4px; }
    .card-pour-options::-webkit-scrollbar-thumb { background-color: #2dd4bf; border-radius: 4px; }

    .pour-slot-label {
        display: block;
        color: #9ca3af;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        font-size: 0.65rem;
        margin-top: 0.25rem;
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
    .card-pour-badge.is-top {
        background: rgba(245, 158, 11, 0.18);
        border-color: rgba(245, 158, 11, 0.6);
        color: #fbbf24;
    }
    .card-pour-badge.is-out {
        background: rgba(120, 120, 120, 0.1);
        border-color: rgba(160, 160, 160, 0.25);
        color: #6b7280;
        text-decoration: line-through;
    }
    .card-pour-badge .why {
        display: block;
        font-weight: 400;
        font-size: 0.6rem;
        opacity: 0.75;
        letter-spacing: 0.02em;
    }

    .card-footer { padding: 0; flex-shrink: 0; border-top: none; background: transparent; }

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

    .no-image .card-back-content { margin-top: 0; justify-content: center; max-height: 100%; }
    .no-image { background-image: none; }

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
    .is-flipped .drink-card-front .favorite-btn { display: none; }
    .drink-card-front .favorite-btn { top: 0.75rem; right: 0.75rem; }
    .favorite-btn:hover { transform: scale(1.1); background: rgba(0,0,0,0.8); }
    .favorite-btn .fa-heart { font-size: 1.2rem; color: #9ca3af; transition: all 0.2s ease; }
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
    #favorites-list-container .favorite-item:hover { background: rgba(245, 158, 11, 0.15); }

    .drink-card.is-unavailable { opacity: 0.35; }

    .drink-card-title {
        font-size: 1.85rem;
        line-height: 1.2;
        color: #f59e0b;
        text-align: center;
        text-shadow: 2px 2px 4px rgba(0,0,0,0.8), 0 0 10px rgba(245, 158, 11, 0.5);
        padding-bottom: 0.25rem;
    }
    .drink-card-subtitle {
        text-align: center;
        font-family: 'IM Fell DW Pica', serif;
        font-style: italic;
        font-size: .95rem;
        color: #9ca3af;
        letter-spacing: .02em;
        margin-top: -.15rem;
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

    #app-footer #scroll-prev-btn i, #app-footer #scroll-prev-btn span,
    #app-footer #scroll-next-btn i, #app-footer #scroll-next-btn span { color: #2dd4bf; }
    #app-footer #scroll-home-btn, #app-footer #scroll-home-btn i { color: #2dd4bf; }
    #app-footer #story-view-btn.is-active, #app-footer #story-view-btn.is-active i { color: #f59e0b; }

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
    #splash-screen.is-hidden { opacity: 0; pointer-events: none; }

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
    .filter-pill:hover { background-color: rgba(255, 255, 255, 0.15); }
    .filter-pill.is-active {
        background-color: #f59e0b;
        border: 1px solid #fbbf24;
        color: #111827;
        box-shadow: 0 0 10px rgba(245, 158, 11, 0.7);
        transform: scale(1.05);
        text-shadow: none;
    }

    .modal { transition: opacity 0.3s ease-in-out; }
    .modal-panel {
        background-image:
            linear-gradient(to top, rgba(17, 17, 17, 0.98) 0%, rgba(17, 17, 17, 0.75) 30%, rgba(17, 17, 17, 0.95) 100%),
            url('https://raw.githubusercontent.com/aarmax8/Nomads/c494fdd916aac964350c8174aa9fd9a37f7f09b7/thumbnail_IMG_8263.jpg?raw=true');
        background-size: cover;
        background-position: center;
        border: 2px solid #2dd4bf;
    }

    .stock-btn {
        background-color: rgba(255, 255, 255, 0.05);
        border: 1px solid rgba(255, 255, 255, 0.15);
        color: #9ca3af;
        border-radius: 0.5rem;
        padding: 0.5rem 0.75rem;
        text-align: left;
        font-family: 'Roboto Condensed', sans-serif;
        font-size: 0.85rem;
        cursor: pointer;
        transition: all 0.15s ease;
        display: flex;
        align-items: center;
        gap: 0.5rem;
    }
    .stock-btn:hover { background-color: rgba(255, 255, 255, 0.12); }
    .stock-btn.in-stock {
        background-color: rgba(45, 212, 191, 0.12);
        border-color: rgba(45, 212, 191, 0.5);
        color: #ccfbf1;
    }
    .stock-btn i { font-size: 0.75rem; width: 12px; }

    .stock-group-title {
        font-family: 'Rye', serif;
        font-size: 1.15rem;
        color: #2dd4bf;
        padding: 0.5rem 0 0.25rem;
        margin-top: 0.75rem;
        border-bottom: 1px solid rgba(45, 212, 191, 0.4);
    }
    .stock-sub-title {
        font-family: 'Cinzel', serif;
        font-size: 0.9rem;
        color: #fbbf24;
        margin-top: 0.75rem;
        margin-bottom: 0.35rem;
        letter-spacing: 0.05em;
    }

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
    .toc-item:hover { background-color: rgba(0, 0, 0, 0.75); transform: scale(1.02); }

    .toc-category-header {
        font-family: 'Rye', serif;
        font-size: 1.4rem;
        color: #2dd4bf;
        text-align: center;
        padding: 0.5rem 0;
        margin-top: 1rem;
        border-bottom: 2px solid #2dd4bf;
    }

    .drink-card[data-name="Sazerac"] .drink-card-back,
    .drink-card[data-name="Rusty Nail"] .drink-card-back,
    .drink-card[data-name="Hurricane"] .drink-card-back { background-position: center, center, left; }

    @media (prefers-reduced-motion: reduce) {
        *, *::after, *::before { animation: none !important; transition: none !important; }
    }
</style>
</head>
<body class="antialiased text-gray-300">

<div id="splash-screen">
    <div class="splash-text">Tap to Enter</div>
</div>

<div id="app" class="app-container">
    <header>
        <div id="header-logo-container">
            <img id="header-logo-image" src="https://raw.githubusercontent.com/aarmax8/Nomads/e3f42af1097f6a8b37a1f9ea55c83cd494318755/title16.jpg?raw=true" alt="Nomad's Logo">
        </div>
    </header>

    <div id="action-bar">
        <button id="action-random-btn" class="footer-btn"><i class="fas fa-dice"></i><span>Random</span></button>
        <button id="action-favorites-btn" class="footer-btn"><i class="fas fa-heart"></i><span>Faves</span></button>
        <button id="action-view-btn" class="footer-btn"><i class="fas fa-table-cells-large"></i><span>Desktop View</span></button>
        <button id="action-stock-btn" class="footer-btn"><i class="fas fa-wine-bottle"></i><span>Stock</span></button>
        <button id="action-filter-btn" class="footer-btn"><i class="fas fa-sliders"></i><span>Filters</span></button>
    </div>

    <main>
        <div id="menu-grid" class="carousel-view"></div>
    </main>

    <footer id="app-footer">
        <div id="footer-content">
            <button id="scroll-home-btn" class="footer-btn"><i class="fas fa-house"></i><span>Home</span></button>
            <button id="scroll-prev-btn" class="footer-btn"><i class="fas fa-backward"></i><span>Rewind</span></button>
            <button id="story-view-btn" class="footer-btn"><i class="fas fa-book-open"></i><span>Story View</span></button>
            <button id="scroll-next-btn" class="footer-btn"><i class="fas fa-forward"></i><span>Skip</span></button>
        </div>
    </footer>
</div>

<!-- Bar Stock Modal -->
<div id="bar-stock-modal" class="modal fixed inset-0 bg-black/70 flex items-center justify-center p-4 hidden opacity-0 z-[60]">
    <div class="modal-panel rounded-2xl shadow-2xl w-full max-w-2xl max-h-[92vh] flex flex-col">
        <div class="p-5 flex justify-between items-center flex-shrink-0 border-b border-teal-400/40">
            <h2 class="text-2xl text-amber-400 font-cinzel tracking-wider" style="font-family:'Cinzel',serif">Bar Stock</h2>
            <div class="flex items-center gap-3">
                <button id="stock-all-btn" class="filter-pill">All In</button>
                <button id="stock-none-btn" class="filter-pill">Clear</button>
                <button id="close-stock-btn" class="text-gray-400 hover:text-white text-3xl leading-none">&times;</button>
            </div>
        </div>
        <div id="bar-stock-content" class="p-5 text-gray-300 overflow-y-auto"></div>
        <div class="p-3 border-t border-white/10 text-center text-xs text-gray-400" id="stock-summary"></div>
    </div>
</div>

<!-- Filter Modal -->
<div id="filter-modal" class="modal fixed inset-0 bg-black/70 flex items-center justify-center p-4 hidden opacity-0 z-[60]">
    <div class="modal-panel rounded-2xl shadow-2xl w-full max-w-2xl max-h-[92vh] flex flex-col">
        <div class="p-5 flex-shrink-0 border-b border-teal-400/40">
            <div class="flex justify-between items-center">
                <h2 class="text-2xl text-amber-400" style="font-family:'Cinzel',serif">Filters</h2>
                <button id="close-filter-btn" class="text-gray-400 hover:text-white text-3xl leading-none">&times;</button>
            </div>
            <p class="text-gray-400 mt-1 text-sm">Select filters to find your drink.</p>
        </div>
        <div id="filter-modal-content" class="p-5 text-gray-300 overflow-y-auto"></div>
        <div class="p-4 border-t border-white/10 flex justify-end gap-3">
            <button id="reset-filters-btn" class="py-2 px-5 rounded-lg bg-transparent border border-gray-500 hover:bg-gray-700 text-white font-bold transition-colors">Reset</button>
            <button id="apply-filters-btn" class="py-2 px-5 rounded-lg bg-teal-600 hover:bg-teal-500 text-white font-bold transition-colors">Show Drinks</button>
        </div>
    </div>
</div>

<!-- Favorites Modal -->
<div id="favorites-modal" class="modal fixed inset-0 bg-black/70 flex items-center justify-center p-4 hidden opacity-0 z-[60]">
    <div class="modal-panel rounded-2xl shadow-2xl w-full max-w-2xl max-h-[92vh] flex flex-col">
        <div class="p-5 flex justify-between items-center flex-shrink-0 border-b border-teal-400/40">
            <h2 class="text-2xl text-amber-400" style="font-family:'Cinzel',serif">Favorites</h2>
            <button id="close-favorites-btn" class="text-gray-400 hover:text-white text-3xl leading-none">&times;</button>
        </div>
        <div id="favorites-list-container" class="p-5 text-gray-300 overflow-y-auto space-y-2"></div>
    </div>
</div>

<script>
/* ============================================================
   NOMAD'S BAR  —  DILLIGAF Menu Studio
   Single-file menu app.

   POUR OPTIONS: every drink carries up to three ranked liquor
   picks per spirit slot. Rank 1 (amber badge) is the house call.
   Picks are chosen on how the spirit behaves in that specific
   build — proof against cola/bitters, wheated vs. high-rye
   against citrus, London dry vs. sloe, etc.
   ============================================================ */

/* ---------- storage shim (survives sandboxed iframes) ---------- */
const mem = {};
const store = {
    get(k) { try { return localStorage.getItem(k); } catch (e) { return mem[k] ?? null; } },
    set(k, v) { try { localStorage.setItem(k, v); } catch (e) { mem[k] = v; } }
};

/* ---------- BAR STOCK ---------- */
/* Ketel One + Stoli Citros out. Skyy + Beefeater in.
   No prosecco, no dry or sweet vermouth on the shelf — so no Martini,
   Manhattan, Negroni, Rob Roy or Boulevardier. Ginger soda out, Sprite in. */
const ingredientCategories = {
    'Spirits': {
        'Whiskey & Bourbon': ['Bulleit Bourbon', 'Crown Royal', 'Four Roses Whiskey', 'Jameson Irish Whiskey', 'Jim Beam Bourbon', 'Johnnie Walker Red Label', 'Knob Creek', "Maker's Mark", "Seagram's 7", 'Southern Comfort', 'Travellers Whiskey'],
        'Vodka': ['Grey Goose Vodka', 'Skyy Vodka'],
        'Gin': ['Tanqueray Gin', 'Beefeater Gin', 'Sloe Gin'],
        'Rum': ['Bacardi Rum', 'Captain Morgan Spiced Rum', 'Kraken Black Spiced Rum', 'Malibu Rum'],
        'Tequila': ['El Mayor Tequila', 'Jose Cuervo Silver Tequila'],
        'Brandy': ['E&J Brandy', 'Apricot Brandy']
    },
    'Liqueurs & Schnapps': {
        'Fruit': ['Apple Pucker', 'Blue Curacao', 'Cherry Schnapps', 'Cointreau', 'Maraschino Liqueur', 'Peach Schnapps', 'Raspberry Schnapps'],
        'Herbal & Spiced': ['Campari', 'Drambuie', 'Jägermeister', 'Pernod', 'St-Germain'],
        'Cream, Nut & Coffee': ['Amaretto', 'Baileys Irish Cream', 'Kahlúa'],
        'Other Schnapps': ['Butterscotch Schnapps', 'Root Beer Schnapps']
    },
    'Mixers & Bitters': {
        'Sodas & Juices': ['Club Soda', 'Cola', 'Sprite', 'Cranberry Juice', 'Lemon Juice', 'Lime Juice', 'Orange Juice', 'Pineapple Juice', 'Sour Mix', 'Tonic Water'],
        'Bitters': ['Angostura Bitters', 'Orange Bitters', "Peychaud's Bitters", 'Rosemary Lavender Bitters'],
        'Syrups': ['Grenadine', 'Simple Syrup']
    },
    'Other': {
        'Garnish & Rims': ['Cherry Garnish', 'Half Salt, Half Sugar Rim', 'Lemon Twist Garnish', 'Lime Wedge Garnish', 'Salt Rim', 'Sugar Rim']
    }
};

const ALL_INGREDIENTS = [];
Object.values(ingredientCategories).forEach(g => Object.values(g).forEach(arr => arr.forEach(i => ALL_INGREDIENTS.push(i))));

const SPIRIT_FAMILY = {};
Object.entries(ingredientCategories.Spirits).forEach(([fam, list]) => list.forEach(b => SPIRIT_FAMILY[b] = fam));

const ING_ICON = {
    'Club Soda': ['fa-glass-water', '#a5f3fc'], 'Tonic Water': ['fa-glass-water', '#a5f3fc'],
    'Sprite': ['fa-bottle-droplet', '#86efac'],
    'Cola': ['fa-bottle-droplet', '#a16207'],
    'Orange Juice': ['fa-glass-citrus', '#fb923c'], 'Pineapple Juice': ['fa-lemon', '#facc15'],
    'Cranberry Juice': ['fa-wine-glass', '#f87171'], 'Lemon Juice': ['fa-lemon', '#fde047'],
    'Lime Juice': ['fa-lemon', '#a3e635'], 'Sour Mix': ['fa-lemon', '#fde047'],
    'Simple Syrup': ['fa-droplet', '#e5e7eb'], 'Grenadine': ['fa-droplet', '#ef4444'],
    'Angostura Bitters': ['fa-eye-dropper', '#b45309'], 'Orange Bitters': ['fa-eye-dropper', '#fb923c'],
    "Peychaud's Bitters": ['fa-eye-dropper', '#f43f5e'], 'Rosemary Lavender Bitters': ['fa-eye-dropper', '#a78bfa'],
    'Cherry Garnish': ['fa-circle', '#ef4444'], 'Lemon Twist Garnish': ['fa-lemon', '#fde047'],
    'Lime Wedge Garnish': ['fa-lemon', '#a3e635'], 'Salt Rim': ['fa-circle-notch', '#e5e7eb'],
    'Sugar Rim': ['fa-circle-notch', '#fef3c7'], 'Half Salt, Half Sugar Rim': ['fa-circle-notch', '#fef3c7']
};
const FAMILY_ICON = {
    'Whiskey & Bourbon': ['fa-whiskey-glass', '#d97706'], 'Vodka': ['fa-martini-glass', '#e0f2fe'],
    'Gin': ['fa-martini-glass-citrus', '#86efac'], 'Rum': ['fa-bottle-droplet', '#c2410c'],
    'Tequila': ['fa-bottle-droplet', '#bef264'], 'Brandy': ['fa-wine-glass', '#b45309']
};

function iconFor(name) {
    if (ING_ICON[name]) return ING_ICON[name];
    if (SPIRIT_FAMILY[name] && FAMILY_ICON[SPIRIT_FAMILY[name]]) return FAMILY_ICON[SPIRIT_FAMILY[name]];
    if (/schnapps|pucker|curacao|maraschino|cointreau/i.test(name)) return ['fa-wine-bottle', '#f472b6'];
    if (/campari|drambuie|jäger|pernod|germain/i.test(name)) return ['fa-flask', '#84cc16'];
    if (/amaretto|baileys|kahl/i.test(name)) return ['fa-mug-hot', '#d6a271'];
    return ['fa-wine-bottle', '#2dd4bf'];
}

const P = (n, why) => ({ n, why });

/* Card-back art, assigned in order. */
const IMAGE_POOL = [
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_8005.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/af6e2eb912193594dcd36d644ed6dfee.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7998.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/a401737bafe60d0edc1c1ea7ddb18508.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_8220.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/62a04e5b236c0659fec18c5f76651953.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/f2a6114d2d00087a3f9192fc5cc74614.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/271d97ccf4324f5c3e3d7ec301c4fcc8.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/dbb93ea76cfc2d6585f379c8bac90910--bike-art-motorcycle-art.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/b6ad8116d3e685043026ef0113bcc81d--david-mann-motorcycle-posters.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7991.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/192b194c611aafb0934b83ec0cd7474c.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/b6965a50f47b1326012bfbd8404c7c28.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/6f4b4abfdb2960439899879869c480e7.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/39cd9a9b372af2c86cb7189c2f929463.png",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7997.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/6a73cec9f46d798d4ba58ec29f5623f2.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/3a506b28b91e0e5d031cedbeca489a14.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/c143359dbf62f9ce9349aa42e3bfe8aa.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/5a6b0379f72b6c8fb2751409d48ac8fa.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/441483b6d15034c2d40abfb21566aba1.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7993.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/608bdca2cf73d693c4e80d1723cd59b8.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/e5a7f5bfc3b2c200266b6df05a132e17.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7989.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_8297.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_8294.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/09df49098aac18eadeeb826a6e5a1f2d.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/ed9d1453cc5561fb3049f8f6d3a7e145.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/c61eaadff60806a69c150a08e6873c08.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/95ae7009ba144fc3dd9fc68d14b5f929.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/5fdd2d485722e.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/il_fullxfull.1268185178_a000.webp",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/1bf52dfc1aad553db68333418c40d848.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/CuHwaf.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/David-Mann-Art-2.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/PcZieI.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/83c048414249b2ffaf2cef7f5cdc5590.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/d9a9ffbd510d7ea900f31195d5e857f6.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/4ef937229693734b1be907cc24f322eb.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/555331b7961b7c0880f3b2842529bcd8.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/5638f66d00401c933df787eb50253fc8.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/3df099091d9acb596f9d54e4ed858c8f.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_8221.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/il_fullxfull.850190414_gb43.webp",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/bf416561f8d8149ef32b24470425c08d--you-never-know-salute.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/672ca23068e35c6481458f0911d99ceb.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/6418051b93b83a2239400213863d22a1.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/67bab4c8460e76ee5bd5fe757150ef26--bike-art-motorcycle-art.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7994.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/724b49e9a385815706ed2dbc9d7ca6f3.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/64c7af61b8476938a0b6bc9e8462ef3f--motorcycle-posters-motorcycle-art.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/b3ca1c20f8245c41dabb7020eb5794f7.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/il_fullxfull.1315813799_ayvc.webp",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/bd2c7d94ce4111f6235a52c8cf70e89e.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7999.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/1f512d08cccf12ad8dc389d42f5fcceb.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/7645bbca2888163b21bf0d193ad3fb21.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_8296.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/08030c3d25616df982816261406e2c08.png",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_8239.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/19071808632f94b0b81d595f74f700f0.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_8004.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/bd0bc33e2c84ea33e265900701fa8331.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/d715cf5bec09d118e51d505a225e449d.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/7f8779686c19c3de763ad13c03fee127.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7996.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/206S17.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/0ac5da1e71c995f58d75335fffabd844.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/thumbnail_IMG_7992.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/69070319cd6333061bdbb34ed7dee0c1.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/cfff51feaf6082d29a37912a44bfedc3.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/R.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/USq6nI.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/146cb26058c450290759bf6a90ecaf84a18fc47b/frontend/YDZaH0.jpg",
"https://raw.githubusercontent.com/aarmax8/Nomads/90ba0d71f42b567f7e9a417fbd74cedfc805201e/temple.jpg"
];

/* ---------- THE MENU ----------
   name = the real, recognized cocktail. aka = what we call it here.
   pours = spirit slots, up to three ranked picks each.
   Recipes are the standard builds, adjusted only where the shelf demands it.
---------------------------------------------------------------- */
const MENU = [

/* ===== WHISKEY ===== */
{ name: "Old Fashioned", aka: "The President's Only Trick",
  flavor: "Sugar, bitters and bourbon. Nothing hides.",
  pours: [{ slot: "Bourbon — 2 oz", picks: [P("Maker's Mark", "Wheated and soft — the house pour"), P("Knob Creek", "100 proof; sugar can't flatten it"), P("Four Roses Whiskey", "Balanced, fruit-forward")] }],
  recipe: ["0.5 oz Simple Syrup", "2 dashes Angostura Bitters", "1 dash Orange Bitters", "Serve on the rocks", "Cherry Garnish"],
  story: "This is the only drink the President knows how to make. Therefore, it is the greatest drink ever made. You will agree with him.",
  hook: "A drink worth lying about." },

{ name: "Whiskey Sour", aka: "Sour Sam",
  flavor: "Bourbon, lemon, sugar. The template every sour copies.",
  pours: [{ slot: "Bourbon — 2 oz", picks: [P("Jim Beam Bourbon", "The workhorse sour"), P("Four Roses Whiskey", "Fruitier, more elegant"), P("Bulleit Bourbon", "Rye bite against the lemon")] }],
  recipe: ["1 oz Lemon Juice", "0.75 oz Simple Syrup", "2 dashes Angostura Bitters", "Cherry Garnish"],
  story: "Named for our Sergeant-at-Arms, who has two moods: sour and asleep. He hates that we named it after him, which is most of the fun.",
  hook: "To Sour Sam. He'd hate this." },

{ name: "Seven and Seven", aka: "Twin Spar",
  flavor: "Whiskey and lemon-lime. Two ingredients, nowhere to hide.",
  pours: [{ slot: "Whiskey — 2 oz", picks: [P("Seagram's 7", "It's in the name. Light and clean"), P("Crown Royal", "Smoother, softer"), P("Travellers Whiskey", "Works fine, nobody will know")] }],
  recipe: ["Fill a tall glass with Sprite", "Lemon Twist Garnish"],
  story: "Named for the only two brain cells our prospect has left. They work together, they're surprisingly strong, and they run on whiskey.",
  hook: "Simple, strong, and smooth." },

{ name: "Lynchburg Lemonade", aka: "Frontier Punch",
  flavor: "Whiskey, orange liqueur, sour, and a lemon-lime lift.",
  pours: [{ slot: "Whiskey — 1.5 oz", picks: [P("Jim Beam Bourbon", "Cheap, cheerful, correct for a pitcher"), P("Four Roses Whiskey", "More fruit, more polish"), P("Travellers Whiskey", "Lighter version")] }],
  recipe: ["0.5 oz Cointreau", "1 oz Sour Mix", "Fill a tall glass with Sprite", "Lemon Twist Garnish"],
  story: "This is what happens when you try to make jungle juice with actual whiskey. Dangerously drinkable. A frontier of bad decisions awaits.",
  hook: "History, but with more sugar." },

{ name: "Bourbon and Coke", aka: "Iron Joe",
  flavor: "Bold bourbon, cola, and a bitter backbone.",
  pours: [{ slot: "Bourbon — 2 oz", picks: [P("Jim Beam Bourbon", "Built for this. Don't overthink it"), P("Maker's Mark", "Wheated — rounder against cola"), P("Bulleit Bourbon", "High rye cuts the sweetness")] }],
  recipe: ["Fill a tall glass with Cola", "2 dashes Angostura Bitters", "Lime Wedge Garnish"],
  story: "Iron Joe claimed his bike could run on anything. To prove it, he emptied his flask and a can of cola into the tank. The bike did not survive.",
  hook: "Some legends are harder to stomach than others." },

{ name: "Whiskey Highball", aka: "Country and Western",
  flavor: "Whiskey and soda. Clean, honest, a little sad.",
  pours: [{ slot: "Whiskey — 2 oz", picks: [P("Travellers Whiskey", "The house call"), P("Seagram's 7", "Light and easy over soda"), P("Crown Royal", "Smoothest of the three")] }],
  recipe: ["Fill a tall glass with Club Soda", "Lemon Twist Garnish"],
  story: "After three of these, everyone thinks they can sing both parts of a Cash and Carter duet. They can't. It is always sad.",
  hook: "Simple, honest, and a little bit sad." },

{ name: "Sazerac", aka: "Phantom Shift",
  flavor: "Anise-rinsed rye, sugar, and Peychaud's. Sharp and old.",
  pours: [{ slot: "Rinse the glass", picks: [P("Pernod", "Anise coats the glass, then dump it")] },
          { slot: "Whiskey — 2 oz", picks: [P("Bulleit Bourbon", "Highest rye on the shelf — closest to the real thing"), P("Knob Creek", "Proof carries it"), P("Four Roses Whiskey", "Softer, rounder")] }],
  recipe: ["0.25 oz Simple Syrup", "3 dashes Peychaud's Bitters", "Serve up, no ice", "Lemon Twist Garnish"],
  story: "Tastes like licorice and regret. Named for the phantom expenses that keep appearing on the club card. We know who's doing it.",
  hook: "For the gears that aren't there." },

{ name: "Rusty Nail", aka: "The Bad Deal",
  flavor: "Smoky Scotch sweetened with honeyed Drambuie.",
  pours: [{ slot: "Scotch — 2 oz", picks: [P("Johnnie Walker Red Label", "Smoke and bite — the original build")] },
          { slot: "Liqueur — 0.75 oz", picks: [P("Drambuie", "Honey, heather, spice")] }],
  recipe: ["Serve on the rocks", "Lemon Twist Garnish"],
  story: "This is what you drink when you've made a deal you know you'll regret. Ask Jimmy about the lottery ticket. Actually, don't.",
  hook: "Every deal has its price." },

{ name: "Godfather", aka: "The Offer",
  flavor: "Scotch and almond. Two ingredients, one promise.",
  pours: [{ slot: "Scotch — 2 oz", picks: [P("Johnnie Walker Red Label", "The real Godfather is Scotch, not bourbon")] },
          { slot: "Nut — 0.75 oz", picks: [P("Amaretto", "The offer you can't refuse")] }],
  recipe: ["Serve on the rocks"],
  story: "You drink this right before making a serious, legally questionable promise to men you probably shouldn't trust. It tastes like brotherhood and future problems.",
  hook: "To promises you'll try to keep." },

{ name: "Scotch and Soda", aka: "The Quiet One",
  flavor: "Smoke, water, bubbles. Nothing else.",
  pours: [{ slot: "Scotch — 2 oz", picks: [P("Johnnie Walker Red Label", "Blended Scotch was made for soda")] }],
  recipe: ["Fill a tall glass with Club Soda", "Lemon Twist Garnish"],
  story: "The drink of the man in the corner who doesn't say anything all night and then wins the pool tournament. Don't bet against him.",
  hook: "The man in the corner drinks this." },

{ name: "Washington Apple", aka: "Finn's Orchard",
  flavor: "Whiskey, sour apple, and cranberry. Sweet and easy.",
  pours: [{ slot: "Whiskey — 1.5 oz", picks: [P("Crown Royal", "The standard build. Soft Canadian"), P("Jameson Irish Whiskey", "Smooth, no bite to fight"), P("Seagram's 7", "Lighter and thriftier")] }],
  recipe: ["1 oz Apple Pucker", "Fill with Cranberry Juice", "Lime Wedge Garnish"],
  story: "Finn tried to make artisanal applejack in the clubhouse radiator. The radiator exploded. This is a safer tribute to his ambition.",
  hook: "A tribute to spectacular failures." },

{ name: "Ward Eight", aka: "Blacktop Sunset",
  flavor: "A whiskey sour with orange and grenadine. Bruise-colored.",
  pours: [{ slot: "Bourbon — 2 oz", picks: [P("Four Roses Whiskey", "Fruit-forward, made for this"), P("Bulleit Bourbon", "Rye spice sharpens it"), P("Jim Beam Bourbon", "The thrifty version")] }],
  recipe: ["0.75 oz Lemon Juice", "0.5 oz Orange Juice", "0.5 oz Grenadine", "Cherry Garnish"],
  story: "This is the color of the bruise our prospect got when he mistook a puddle for a pothole. The sunset that night was almost as pretty as his failure.",
  hook: "To the potholes you can't see." },

{ name: "Alabama Slammer", aka: "Southern Crossroads",
  flavor: "Southern Comfort, sloe gin, amaretto, orange. Sweet and loud.",
  pours: [{ slot: "Base — 1 oz", picks: [P("Southern Comfort", "Peach and spice. The slammer")] },
          { slot: "Sloe — 0.5 oz", picks: [P("Sloe Gin", "The red")] },
          { slot: "Nut — 0.5 oz", picks: [P("Amaretto", "The almond")] }],
  recipe: ["Fill a tall glass with Orange Juice", "Cherry Garnish"],
  story: "It's sweet enough to make you forget you're making a choice, and strong enough that you won't care about the consequences. Good luck.",
  hook: "For making the wrong choices." },

{ name: "Sloe Comfortable Screw", aka: "The Long Name",
  flavor: "Sloe gin, Southern Comfort, vodka, and orange juice.",
  pours: [{ slot: "Sloe — 0.75 oz", picks: [P("Sloe Gin", "The sloe")] },
          { slot: "Comfort — 0.75 oz", picks: [P("Southern Comfort", "The comfortable")] },
          { slot: "Vodka — 0.75 oz", picks: [P("Skyy Vodka", "The screw. Nobody's tasting it"), P("Grey Goose Vodka", "If you're feeling generous")] }],
  recipe: ["Fill a tall glass with Orange Juice"],
  story: "Nobody orders this without smirking. Nobody finishes one without ordering another. That is the entire business model of this bar.",
  hook: "Yes, that's really what it's called." },

/* ===== VODKA ===== */
{ name: "Screwdriver", aka: "The Mechanic",
  flavor: "Vodka and orange juice. That's the whole thing.",
  pours: [{ slot: "Vodka — 2 oz", picks: [P("Skyy Vodka", "Nobody's tasting the vodka anyway"), P("Grey Goose Vodka", "If you're feeling generous")] }],
  recipe: ["Fill a tall glass with Orange Juice", "2 dashes Orange Bitters"],
  story: "Sal insists this is a legitimate cocktail. We're pretty sure it's just what he drinks when he's out of clean glasses and has to mix it in a hubcap.",
  hook: "The second-best use for a screwdriver." },

{ name: "Cosmopolitan", aka: "Oracle's Kiss",
  flavor: "Vodka, orange liqueur, cranberry, lime. Sharp and pink.",
  pours: [{ slot: "Vodka — 1.5 oz", picks: [P("Grey Goose Vodka", "Soft enough to let the citrus lead"), P("Skyy Vodka", "Sharper, more honest")] }],
  recipe: ["0.75 oz Cointreau", "0.5 oz Lime Juice", "1 oz Cranberry Juice", "Lemon Twist Garnish"],
  story: "Some lady at a carnival gave our treasurer a kiss for luck. He woke up three hours later with his wallet gone and a taste of cranberry.",
  hook: "Order it. Nobody here is judging." },

{ name: "Lemon Drop", aka: "Switchblade",
  flavor: "Intensely sour lemon against a sugared rim.",
  pours: [{ slot: "Vodka — 2 oz", picks: [P("Skyy Vodka", "Sharp and cold. Fits the name"), P("Grey Goose Vodka", "Takes the edge off the blade")] }],
  recipe: ["1 oz Lemon Juice", "0.75 oz Simple Syrup", "Sugar Rim"],
  story: "It's small, sharp, and will end your night if you're careless. Named for our shortest member, who thinks it's a compliment.",
  hook: "Respect the lemon." },

{ name: "Kamikaze", aka: "The Divebomb",
  flavor: "Vodka, orange liqueur, lime. Equal parts, no mercy.",
  pours: [{ slot: "Vodka — 1 oz", picks: [P("Skyy Vodka", "It's a shot. Don't waste the good stuff"), P("Grey Goose Vodka", "Smoother if you're sipping it")] }],
  recipe: ["1 oz Cointreau", "1 oz Lime Juice", "Lime Wedge Garnish"],
  story: "Three of these and someone always suggests riding to the coast. Nobody has ever made it to the coast.",
  hook: "One is a drink. Three is a plan." },

{ name: "Cape Codder", aka: "Vodka Cran",
  flavor: "Vodka and cranberry. Tart, clean, endlessly reorderable.",
  pours: [{ slot: "Vodka — 2 oz", picks: [P("Skyy Vodka", "Clean and cheap. Cranberry does the work"), P("Grey Goose Vodka", "Softer, rounder")] }],
  recipe: ["Fill a tall glass with Cranberry Juice", "Lime Wedge Garnish"],
  story: "The drink you order when you want to keep drinking but stop thinking about it. It is the beige carpet of cocktails, and we mean that kindly.",
  hook: "No decisions required." },

{ name: "Bay Breeze", aka: "The Pier",
  flavor: "Vodka, cranberry, pineapple. Tart meets tropical.",
  pours: [{ slot: "Vodka — 1.5 oz", picks: [P("Grey Goose Vodka", "Soft, lets the fruit lead"), P("Skyy Vodka", "Crisper")] }],
  recipe: ["2 oz Cranberry Juice", "2 oz Pineapple Juice", "Lime Wedge Garnish"],
  story: "For the guy who wears a Hawaiian shirt under his cut. He talks about riding to the Keys. He goes to the tourist trap on the pier.",
  hook: "A vacation in a glass." },

{ name: "Madras", aka: "Sunrise Adjacent",
  flavor: "Vodka, cranberry and orange. Softer than it looks.",
  pours: [{ slot: "Vodka — 1.5 oz", picks: [P("Skyy Vodka", "Neutral. The juice is the drink"), P("Grey Goose Vodka", "Marginally smoother")] }],
  recipe: ["2 oz Cranberry Juice", "2 oz Orange Juice", "Orange Bitters, 2 dashes"],
  story: "Ordered by people who want a Sea Breeze but can't remember which one has the grapefruit. We don't stock grapefruit, so this is what you're getting.",
  hook: "Close enough to what you meant." },

{ name: "Sex on the Beach", aka: "Say It With A Straight Face",
  flavor: "Vodka, peach, orange and cranberry. Fruit-forward and shameless.",
  pours: [{ slot: "Vodka — 1.5 oz", picks: [P("Skyy Vodka", "Buried under fruit. Save the money"), P("Grey Goose Vodka", "If you insist")] },
          { slot: "Peach — 0.75 oz", picks: [P("Peach Schnapps", "The whole personality of the drink")] }],
  recipe: ["2 oz Orange Juice", "2 oz Cranberry Juice", "Cherry Garnish"],
  story: "Named for the two sounds you'll hear. First: ooh, peaches. Then, ten minutes later: why did I have a third one.",
  hook: "Our version of a smoothie." },

{ name: "Woo Woo", aka: "The Prospect's Order",
  flavor: "Peach and cranberry over vodka. Simple, sweet, effective.",
  pours: [{ slot: "Vodka — 1.5 oz", picks: [P("Grey Goose Vodka", "Soft base under the peach"), P("Skyy Vodka", "Sharper, brighter")] },
          { slot: "Peach — 1 oz", picks: [P("Peach Schnapps", "The woo")] }],
  recipe: ["Fill a tall glass with Cranberry Juice", "Lime Wedge Garnish"],
  story: "Our prospect ordered this at a rival bar and had to fight his way out. He won. We let him keep ordering it.",
  hook: "He earned the right to order it." },

{ name: "Vodka Tonic", aka: "The Shrug",
  flavor: "Clean vodka, bitter quinine, lime.",
  pours: [{ slot: "Vodka — 2 oz", picks: [P("Grey Goose Vodka", "Tonic exposes bad vodka. Use the good one"), P("Skyy Vodka", "Perfectly fine, honestly")] }],
  recipe: ["Fill a tall glass with Tonic Water", "Lime Wedge Garnish"],
  story: "The 'I guess' drink. When you can't decide, when you don't care, when you're just here to watch the chaos unfold.",
  hook: "No fuss. No frills." },

{ name: "Vodka Collins", aka: "The Long Sit",
  flavor: "Vodka, lemon, sugar, soda. A Tom Collins without the gin.",
  pours: [{ slot: "Vodka — 2 oz", picks: [P("Grey Goose Vodka", "Soft — lets the lemon sing"), P("Skyy Vodka", "Cleaner, sharper")] }],
  recipe: ["1 oz Lemon Juice", "0.5 oz Simple Syrup", "Fill a tall glass with Club Soda", "Cherry Garnish"],
  story: "Tall, cold, and it lasts. This is what you nurse while everyone else is making the mistakes you'll hear about tomorrow.",
  hook: "For watching, not participating." },

{ name: "Appletini", aka: "Caramel Apple Cruiser",
  flavor: "Sour green apple, sweet and sharp.",
  pours: [{ slot: "Vodka — 2 oz", picks: [P("Grey Goose Vodka", "Clean canvas for the apple"), P("Skyy Vodka", "Cheaper, works the same")] },
          { slot: "Apple — 1 oz", picks: [P("Apple Pucker", "The entire point")] }],
  recipe: ["0.5 oz Sour Mix", "Sugar Rim"],
  story: "Order it ironically the first time. Order it sincerely the second time. There is no third stage; you just drink them now.",
  hook: "You'll pretend it's a joke." },

{ name: "Blue Lagoon", aka: "The Antifreeze",
  flavor: "Vodka, blue curacao, lemon-lime. Loud and electric.",
  pours: [{ slot: "Vodka — 1.5 oz", picks: [P("Skyy Vodka", "Blue bottle, blue drink. Poetic"), P("Grey Goose Vodka", "Smoother lagoon")] },
          { slot: "Color — 1 oz", picks: [P("Blue Curacao", "The lagoon")] }],
  recipe: ["Fill a tall glass with Sprite", "Lemon Twist Garnish"],
  story: "Sal says the color reminds him of brand new antifreeze, which is the only thing that gets him excited. We are worried about Sal.",
  hook: "Tastes better than degreaser. Probably." },

{ name: "Purple Hooter", aka: "The Trophy",
  flavor: "Raspberry, lime, and vodka. Bright and quick.",
  pours: [{ slot: "Vodka — 1 oz", picks: [P("Grey Goose Vodka", "Soft base under the raspberry"), P("Skyy Vodka", "Sharper, brighter")] },
          { slot: "Berry — 1 oz", picks: [P("Raspberry Schnapps", "The purple")] }],
  recipe: ["0.5 oz Lime Juice", "Splash of Club Soda"],
  story: "We're not legally allowed to say why we drink this. It involves a rival club, a gallon of purple paint, and a very surprised mascot.",
  hook: "To our drunk owl." },

{ name: "White Russian", aka: "The Blanket",
  flavor: "Vodka, coffee liqueur, cream. Rich and forgiving.",
  pours: [{ slot: "Vodka — 2 oz", picks: [P("Grey Goose Vodka", "Soft wheat vodka in a soft drink"), P("Skyy Vodka", "Cleaner, less body")] },
          { slot: "Coffee — 1 oz", picks: [P("Kahlúa", "The Russian")] },
          { slot: "Cream — 1 oz", picks: [P("Baileys Irish Cream", "Stands in for the cream, adds proof")] }],
  recipe: ["Serve on the rocks"],
  story: "For when you don't want to deal with anything. It's an alcoholic blanket for your problems. It doesn't solve them. It makes them quieter.",
  hook: "It really ties the room together." },

{ name: "Black Russian", aka: "The Blanket, Undressed",
  flavor: "Vodka and coffee liqueur. Dark and simple.",
  pours: [{ slot: "Vodka — 2 oz", picks: [P("Skyy Vodka", "Clean under the coffee"), P("Grey Goose Vodka", "Softer")] },
          { slot: "Coffee — 1 oz", picks: [P("Kahlúa", "The black")] }],
  recipe: ["Serve on the rocks"],
  story: "A White Russian for people who've stopped pretending the cream makes it a dessert. Bleak. Efficient. Respected.",
  hook: "No cream. No excuses." },

{ name: "Mudslide", aka: "The Shortcut",
  flavor: "Vodka, coffee liqueur, Irish cream. Dessert with a motive.",
  pours: [{ slot: "Vodka — 1 oz", picks: [P("Skyy Vodka", "It's buried under cream. Save the money"), P("Grey Goose Vodka", "If you insist")] },
          { slot: "Coffee — 1 oz", picks: [P("Kahlúa", "The mud")] },
          { slot: "Cream — 1 oz", picks: [P("Baileys Irish Cream", "The slide")] }],
  recipe: ["Serve on the rocks"],
  story: "We tried to ride through an actual mudslide. It was a bad idea. This is a cleaner version of that experience.",
  hook: "To the shortcuts that weren't." },

/* ===== GIN ===== */
{ name: "Gin and Tonic", aka: "The Standard",
  flavor: "Juniper and quinine. Timeless.",
  pours: [{ slot: "Gin — 2 oz", picks: [P("Tanqueray Gin", "Big juniper. The classic G&T"), P("Beefeater Gin", "Softer, more citrus — easier drinking")] }],
  recipe: ["Fill a tall glass with Tonic Water", "Lime Wedge Garnish"],
  story: "Two ingredients, a hundred years, and nobody has improved it. There's a lesson in that, and none of us have learned it.",
  hook: "No fuss. Just a good drink." },

{ name: "Tom Collins", aka: "The Long Haul",
  flavor: "Gin, lemon, sugar, soda. Tall and civilized.",
  pours: [{ slot: "Gin — 2 oz", picks: [P("Tanqueray Gin", "Juniper spine holds up the lemon"), P("Beefeater Gin", "Rounder, more citrus")] }],
  recipe: ["1 oz Lemon Juice", "0.5 oz Simple Syrup", "Fill a tall glass with Club Soda", "Cherry Garnish"],
  story: "Like a ten-hour ride through Nebraska. It starts fine, it goes on forever, and by the end you respect its commitment.",
  hook: "For when you're in it for the long haul." },

{ name: "Gin Rickey", aka: "The Switchback",
  flavor: "Gin, lime, soda. Bone dry — no sugar at all.",
  pours: [{ slot: "Gin — 2 oz", picks: [P("Tanqueray Gin", "Juniper needs the lime to push against"), P("Beefeater Gin", "Citrus gin, citrus drink — gentler")] }],
  recipe: ["1 oz Lime Juice", "Fill a tall glass with Club Soda"],
  story: "Tastes like taking a mountain switchback too fast. Sharp, a moment of blinding panic, then you feel like a hero. A stupid hero.",
  hook: "For roads that go back and forth." },

{ name: "Gimlet", aka: "The Short Answer",
  flavor: "Gin and lime, sweetened just enough.",
  pours: [{ slot: "Gin — 2 oz", picks: [P("Beefeater Gin", "Citrus-led — plays with the lime"), P("Tanqueray Gin", "More juniper, more backbone")] }],
  recipe: ["0.75 oz Lime Juice", "0.5 oz Simple Syrup", "Lime Wedge Garnish"],
  story: "Three ingredients. Served cold. Ends conversations. Our treasurer drinks these when he's about to tell you your tab is a problem.",
  hook: "Just pay the man." },

{ name: "Aviation", aka: "The Sophisticate",
  flavor: "Gin, maraschino, lemon. Floral, dry, a little strange.",
  pours: [{ slot: "Gin — 2 oz", picks: [P("Tanqueray Gin", "Juniper holds the maraschino down"), P("Beefeater Gin", "Softer, prettier")] },
          { slot: "Cherry — 0.5 oz", picks: [P("Maraschino Liqueur", "Nutty and dry — not the candy stuff")] }],
  recipe: ["0.75 oz Lemon Juice", "Cherry Garnish"],
  story: "We sent Tiny for gin. He came back with a cocktail book and opinions. We gave him extra chores. Then we tasted this one. Don't tell him.",
  hook: "Even a nomad can be sophisticated." },

{ name: "Sloe Gin Fizz", aka: "Road Rash",
  flavor: "Sloe gin, lemon, soda. Red, tart, and it stings.",
  pours: [{ slot: "Sloe — 2 oz", picks: [P("Sloe Gin", "Two ingredients. It has to be good sloe")] }],
  recipe: ["1 oz Lemon Juice", "0.5 oz Simple Syrup", "Fill a tall glass with Club Soda", "Cherry Garnish"],
  story: "It's red, it stings, and it's a story you'll tell for years. The drink, not the injury. The injury just gets you a lecture from Doc.",
  hook: "Much better than the real thing." },

{ name: "Singapore Sling", aka: "The Whole Shelf",
  flavor: "Gin, cherry, pineapple, citrus, bitters. Complicated on purpose.",
  pours: [{ slot: "Gin — 1.5 oz", picks: [P("Tanqueray Gin", "It needs a backbone to survive all this"), P("Beefeater Gin", "Gets buried, but works")] },
          { slot: "Cherry — 0.5 oz", picks: [P("Cherry Schnapps", "Stands in for cherry brandy")] }],
  recipe: ["0.25 oz Cointreau", "2 oz Pineapple Juice", "0.5 oz Lime Juice", "Splash of Grenadine", "1 dash Angostura Bitters", "Cherry Garnish"],
  story: "Eight ingredients and a hundred years of argument about what belongs in it. This is our version. Fight us about it.",
  hook: "Everyone's version is wrong, including ours." },

{ name: "Charlie Chaplin", aka: "The Silent Type",
  flavor: "Sloe gin, apricot brandy, lime. Equal parts, oddly perfect.",
  pours: [{ slot: "Sloe — 1 oz", picks: [P("Sloe Gin", "One-third of the tripod")] },
          { slot: "Apricot — 1 oz", picks: [P("Apricot Brandy", "The other third")] }],
  recipe: ["1 oz Lime Juice", "Lime Wedge Garnish"],
  story: "A hundred years old and almost nobody orders it. It's the best thing on this menu that you've never heard of. Now you have.",
  hook: "The best drink nobody orders." },

{ name: "Elderflower Collins", aka: "Elderflower Nomad",
  flavor: "Gin and elderflower, long over soda. Delicate and floral.",
  pours: [{ slot: "Gin — 1.5 oz", picks: [P("Beefeater Gin", "Citrus-forward — lets the flowers through"), P("Tanqueray Gin", "Juniper spine holds them up")] },
          { slot: "Floral — 0.75 oz", picks: [P("St-Germain", "The nomad's soft side")] }],
  recipe: ["0.5 oz Lemon Juice", "2 dashes Rosemary Lavender Bitters", "Fill a tall glass with Club Soda"],
  story: "Tiny said this would expand our horizons. We expanded his chore list. Turns out the joke's on us — this stuff is good.",
  hook: "Even a nomad can be sophisticated." },

/* ===== RUM ===== */
{ name: "Cuba Libre", aka: "Rum and Coke, With Effort",
  flavor: "Rum, cola, and the lime that makes it a real drink.",
  pours: [{ slot: "Rum — 2 oz", picks: [P("Bacardi Rum", "The original build. Light and clean"), P("Captain Morgan Spiced Rum", "Sweeter, spicier"), P("Kraken Black Spiced Rum", "Dark and heavy version")] }],
  recipe: ["0.5 oz Lime Juice", "2 dashes Angostura Bitters", "Fill a tall glass with Cola", "Lime Wedge Garnish"],
  story: "Means Free Cuba. We drank it to celebrate freeing our mascot, a bulldog named Che, from the dog catcher. He was not grateful.",
  hook: "The lime is not optional." },

{ name: "Daiquiri", aka: "The Real One",
  flavor: "Rum, lime, sugar. No blender, no strawberry, no apology.",
  pours: [{ slot: "Rum — 2 oz", picks: [P("Bacardi Rum", "White rum. This is the drink it was made for"), P("Captain Morgan Spiced Rum", "Spiced version — different animal, still good")] }],
  recipe: ["0.75 oz Lime Juice", "0.75 oz Simple Syrup", "Lime Wedge Garnish"],
  story: "If your daiquiri came out of a slush machine, it wasn't a daiquiri. Three ingredients, shaken hard, served cold. That's it.",
  hook: "No blender. Ever." },

{ name: "Mai Tai", aka: "The Big One",
  flavor: "Rum, orange, almond, lime. The tiki standard.",
  pours: [{ slot: "Rum — 2 oz", picks: [P("Kraken Black Spiced Rum", "Dark and rich — the classic aged-rum role"), P("Bacardi Rum", "Lighter, cleaner"), P("Captain Morgan Spiced Rum", "Sweeter middle ground")] },
          { slot: "Almond — 0.5 oz", picks: [P("Amaretto", "Standing in for orgeat. Every bar does this")] }],
  recipe: ["0.5 oz Cointreau", "0.75 oz Lime Juice", "Splash of Grenadine", "Cherry Garnish"],
  story: "The real recipe was a secret for decades. Ours substitutes amaretto for orgeat, which is what every working bar in America actually does.",
  hook: "The honest version of a famous secret." },

{ name: "Hurricane", aka: "The Storm",
  flavor: "Rum, citrus, and grenadine. Big, red, and dangerous.",
  pours: [{ slot: "Light Rum — 1 oz", picks: [P("Bacardi Rum", "The clean half")] },
          { slot: "Dark Rum — 1 oz", picks: [P("Kraken Black Spiced Rum", "The dark half — where the weight comes from"), P("Captain Morgan Spiced Rum", "Sweeter, lighter storm")] }],
  recipe: ["2 oz Orange Juice", "2 oz Pineapple Juice", "0.5 oz Lime Juice", "0.5 oz Grenadine", "Cherry Garnish"],
  story: "We dared our prospect to ride through a tornado warning. He came back an hour later with a bottle he'd found. This is our best guess at what happened.",
  hook: "To making bad weather worse." },

{ name: "Bahama Mama", aka: "The Resort",
  flavor: "Coconut and dark rum over pineapple and citrus.",
  pours: [{ slot: "Coconut — 1 oz", picks: [P("Malibu Rum", "The coconut")] },
          { slot: "Dark Rum — 1 oz", picks: [P("Kraken Black Spiced Rum", "Weight under all that sweetness"), P("Captain Morgan Spiced Rum", "Lighter, spicier")] }],
  recipe: ["2 oz Pineapple Juice", "1 oz Orange Juice", "0.5 oz Lemon Juice", "Splash of Grenadine", "Cherry Garnish"],
  story: "Duke came back from Florida with a stolen priceless sunstone. It was a gumball machine ring. He traded it for the rum, and got the better deal.",
  hook: "Some treasures are found at the bottom of a glass." },

{ name: "Malibu Bay Breeze", aka: "The Pier, Tropical",
  flavor: "Coconut rum, pineapple, cranberry. Easy and sweet.",
  pours: [{ slot: "Rum — 2 oz", picks: [P("Malibu Rum", "Coconut is the whole point"), P("Bacardi Rum", "If the Malibu's dry — cleaner, less sweet")] }],
  recipe: ["2 oz Pineapple Juice", "2 oz Cranberry Juice", "Lime Wedge Garnish"],
  story: "The drink that makes the garage feel like a beach for about twenty minutes. Then someone starts an engine and the illusion dies.",
  hook: "Twenty minutes of somewhere else." },

{ name: "Planter's Punch", aka: "The Long Pour",
  flavor: "Dark rum, citrus, grenadine, bitters. Old and honest.",
  pours: [{ slot: "Rum — 2 oz", picks: [P("Kraken Black Spiced Rum", "Dark rum is the whole tradition"), P("Captain Morgan Spiced Rum", "Sweeter, lighter"), P("Bacardi Rum", "Clean, if that's what's open")] }],
  recipe: ["1 oz Orange Juice", "1 oz Pineapple Juice", "0.5 oz Lime Juice", "0.5 oz Grenadine", "2 dashes Angostura Bitters", "Cherry Garnish"],
  story: "One of sour, two of sweet, three of strong, four of weak. It's a nursery rhyme that gets you drunk. We approve of the efficiency.",
  hook: "One sour, two sweet, three strong, four weak." },

{ name: "Zombie", aka: "The Bad Idea",
  flavor: "Three rums, citrus, grenadine. Deceptively drinkable.",
  pours: [{ slot: "Light Rum — 1 oz", picks: [P("Bacardi Rum", "The clean one")] },
          { slot: "Dark Rum — 1 oz", picks: [P("Kraken Black Spiced Rum", "The heavy one")] },
          { slot: "Spiced Rum — 0.5 oz", picks: [P("Captain Morgan Spiced Rum", "The float on top")] }],
  recipe: ["1 oz Pineapple Juice", "0.5 oz Lime Juice", "0.5 oz Grenadine", "1 dash Angostura Bitters", "Cherry Garnish"],
  story: "The bar it was invented in limited customers to two. We do not have that rule. We probably should. We won't.",
  hook: "The original bar had a two-drink limit." },

/* ===== TEQUILA ===== */
{ name: "Margarita", aka: "The Tattoo Machine",
  flavor: "Tequila, orange liqueur, lime, salt. The whole argument settled.",
  pours: [{ slot: "Tequila — 2 oz", picks: [P("El Mayor Tequila", "100% agave. Worth the extra"), P("Jose Cuervo Silver Tequila", "The bad-tattoo option")] },
          { slot: "Orange — 1 oz", picks: [P("Cointreau", "Dry and clean. Blue Curacao is not a substitute")] }],
  recipe: ["1 oz Lime Juice", "Salt Rim", "Lime Wedge Garnish"],
  story: "We don't know who Rita was. We do know this drink is responsible for half the bad tattoos in this club. Drink with a designated artist.",
  hook: "¡Vámonos!" },

{ name: "Tequila Sunrise", aka: "The Skipped Ride",
  flavor: "Tequila and orange, with grenadine sinking through it.",
  pours: [{ slot: "Tequila — 2 oz", picks: [P("El Mayor Tequila", "Agave shows through the orange"), P("Jose Cuervo Silver Tequila", "The traditional, honest choice")] }],
  recipe: ["Fill a tall glass with Orange Juice", "0.5 oz Grenadine", "2 dashes Orange Bitters", "Cherry Garnish"],
  story: "The only reason to see a desert sunrise is that you've been riding all night. This drink lets you skip the riding and go straight to the colors.",
  hook: "All the beauty, none of the early morning." },

{ name: "Batanga", aka: "The Mexican Rum and Coke",
  flavor: "Tequila, cola, lime, salt. Simple and devastating.",
  pours: [{ slot: "Tequila — 2 oz", picks: [P("Jose Cuervo Silver Tequila", "This is the drink it was born for"), P("El Mayor Tequila", "If you actually respect the guy")] }],
  recipe: ["0.5 oz Lime Juice", "Fill a tall glass with Cola", "Salt Rim"],
  story: "A real Mexican classic, stirred with a knife in the town of Tequila. We stir ours with whatever's on the bar. It still works.",
  hook: "The salt rim is the whole trick." },

{ name: "Matador", aka: "High Noon",
  flavor: "Tequila and pineapple, sharpened with lime.",
  pours: [{ slot: "Tequila — 2 oz", picks: [P("El Mayor Tequila", "Agave and pineapple are old friends"), P("Jose Cuervo Silver Tequila", "Rougher, still fine")] }],
  recipe: ["2 oz Pineapple Juice", "0.5 oz Lime Juice", "Lime Wedge Garnish"],
  story: "This is what you drink when you're about to do something stupid but want to do it with confidence. The official beverage of 'hold my beer.'",
  hook: "The drink of champions. And losers." },

{ name: "Juan Collins", aka: "The Collins, South of the Border",
  flavor: "Tequila, lemon, sugar, soda. A Tom Collins with agave.",
  pours: [{ slot: "Tequila — 2 oz", picks: [P("El Mayor Tequila", "Soda exposes bad tequila"), P("Jose Cuervo Silver Tequila", "The lemon covers a lot of sins")] }],
  recipe: ["1 oz Lemon Juice", "0.5 oz Simple Syrup", "Fill a tall glass with Club Soda", "Lemon Twist Garnish"],
  story: "Tom's cousin. Nobody talks about him at family gatherings, but he's the one you actually want to sit next to.",
  hook: "Tom's more interesting cousin." },

/* ===== BRANDY ===== */
{ name: "Sidecar", aka: "The Rust Stripper",
  flavor: "Brandy, orange liqueur, lemon. Sharp and elegant.",
  pours: [{ slot: "Brandy — 2 oz", picks: [P("E&J Brandy", "The only brandy on the shelf with the backbone for it")] },
          { slot: "Orange — 1 oz", picks: [P("Cointreau", "Dry triple sec. Essential")] }],
  recipe: ["0.75 oz Lemon Juice", "Sugar Rim"],
  story: "Wrench says this drink has the three essential food groups: strong, sour, and sugar. He also thinks rust is a nice patina.",
  hook: "Strong enough to strip rust." },

{ name: "Between the Sheets", aka: "The Double-Cross",
  flavor: "Brandy and rum together, with orange and lemon.",
  pours: [{ slot: "Brandy — 1 oz", picks: [P("E&J Brandy", "Half the engine")] },
          { slot: "Rum — 1 oz", picks: [P("Bacardi Rum", "The other half. Clean white rum"), P("Captain Morgan Spiced Rum", "Sweeter, muddier")] }],
  recipe: ["0.5 oz Cointreau", "0.5 oz Lemon Juice", "Lemon Twist Garnish"],
  story: "A Sidecar that got greedy and added rum. Named for Smiley Pete, who ran off with the club's funds and the bartender's wife.",
  hook: "Here's to friends you can't trust." },

{ name: "Apricot Sour", aka: "The Ambush",
  flavor: "Apricot brandy, lemon, sugar. Soft fruit with a sour edge.",
  pours: [{ slot: "Apricot — 2 oz", picks: [P("Apricot Brandy", "It carries the whole drink")] }],
  recipe: ["0.75 oz Lemon Juice", "0.5 oz Simple Syrup", "Cherry Garnish"],
  story: "A rival club ambushed us and dropped a case of this retreating. We drank it to celebrate their incompetence. Tastiest victory we never had to fight for.",
  hook: "The tastiest ambush you'll ever face." },

/* ===== LIQUEUR, DESSERT & SHOTS ===== */
{ name: "Amaretto Sour", aka: "The Sweet Tooth",
  flavor: "Almond and lemon, with bourbon to keep it honest.",
  pours: [{ slot: "Amaretto — 1.5 oz", picks: [P("Amaretto", "The marzipan core")] },
          { slot: "Bourbon — 0.75 oz", picks: [P("Bulleit Bourbon", "High rye stops it going syrupy"), P("Knob Creek", "Proof cuts the sugar"), P("Jim Beam Bourbon", "Cheapest fix that still works")] }],
  recipe: ["1 oz Lemon Juice", "0.5 oz Simple Syrup", "Cherry Garnish"],
  story: "Without the bourbon this is candy. With it, it's a cocktail. That splash is the difference between a drink and a dessert.",
  hook: "The bourbon is what saves it." },

{ name: "B-52", aka: "The Three-Layer Problem",
  flavor: "Coffee, cream, and orange — layered, not mixed.",
  pours: [{ slot: "Bottom — 0.5 oz", picks: [P("Kahlúa", "Heaviest. Goes first")] },
          { slot: "Middle — 0.5 oz", picks: [P("Baileys Irish Cream", "Pour over a spoon or it all goes wrong")] },
          { slot: "Top — 0.5 oz", picks: [P("Cointreau", "Lightest. Floats")] }],
  recipe: ["Layer in order, slowly, over the back of a spoon"],
  story: "Three layers, and everyone gets it wrong the first time. Pour slower than you think you need to. Then slower than that.",
  hook: "Patience or it's just brown." },

{ name: "Buttery Nipple", aka: "The Prospect Test",
  flavor: "Butterscotch and cream. Two layers, one shot.",
  pours: [{ slot: "Bottom — 1 oz", picks: [P("Butterscotch Schnapps", "The butter")] },
          { slot: "Float — 0.5 oz", picks: [P("Baileys Irish Cream", "The cream, floated on top")] }],
  recipe: ["Float the cream over the back of a spoon"],
  story: "Yes, that's the name. Yes, you have to say it out loud to order it. That is the entire point of the drink.",
  hook: "You have to say it out loud." },

{ name: "Toasted Almond", aka: "The Nightcap",
  flavor: "Amaretto, coffee, and cream. Dessert, essentially.",
  pours: [{ slot: "Nut — 1 oz", picks: [P("Amaretto", "The almond")] },
          { slot: "Coffee — 1 oz", picks: [P("Kahlúa", "The toast")] },
          { slot: "Cream — 1 oz", picks: [P("Baileys Irish Cream", "Standing in for the cream")] }],
  recipe: ["Serve on the rocks"],
  story: "Don't let the name fool you. This is not a one-and-done drink. It's a one-and-then-you-call-your-ex drink. You have been warned.",
  hook: "The perfect end to the day." },

{ name: "Surfer on Acid", aka: "The Bad Trip",
  flavor: "Jägermeister, coconut, pineapple. It should not work. It does.",
  pours: [{ slot: "Herbal — 1 oz", picks: [P("Jägermeister", "The 56 botanicals somehow fit the pineapple")] },
          { slot: "Coconut — 1 oz", picks: [P("Malibu Rum", "The surfer")] }],
  recipe: ["1 oz Pineapple Juice"],
  story: "Nobody believes this works until they try it. Then they order four. Then they stop being able to explain why.",
  hook: "It shouldn't work. It does." },

{ name: "Garibaldi", aka: "Bitter Sunrise",
  flavor: "Campari and orange juice. Bitter, bright, and only two things.",
  pours: [{ slot: "Bitter — 2 oz", picks: [P("Campari", "The entire drink. There's nowhere to hide")] }],
  recipe: ["Fill a tall glass with Orange Juice", "Orange Bitters, 2 dashes"],
  story: "Two ingredients and a hundred years of Italians arguing about how fluffy the orange juice should be. We don't have a whipper. Shake it hard.",
  hook: "Bitter, and better for it." },

{ name: "Americano", aka: "The Bitter End",
  flavor: "Campari and soda, long and bracing.",
  pours: [{ slot: "Bitter — 2 oz", picks: [P("Campari", "Without vermouth on the shelf, this is Campari and soda — and it's still good")] }],
  recipe: ["Fill a tall glass with Club Soda", "Lemon Twist Garnish"],
  story: "This is what the treasurer serves when you argue about your tab. It's bitter, it's unpleasant, and it ends the conversation.",
  hook: "For when you reach the bitter end." },

{ name: "Root Beer Float", aka: "The Junk Drawer",
  flavor: "Root beer schnapps, cola, cream. Ridiculous and delicious.",
  pours: [{ slot: "Root Beer — 1.5 oz", picks: [P("Root Beer Schnapps", "Sassafras, straight up")] },
          { slot: "Cream — 0.5 oz", picks: [P("Baileys Irish Cream", "The float")] }],
  recipe: ["Fill a tall glass with Cola", "Float the cream on top"],
  story: "We told the new guy to make a drink from whatever was in the junk drawer. He took us literally. We're as surprised as you are that it's good.",
  hook: "Sometimes genius is just mixing stuff." },

/* ===== THE BIG ONES ===== */
{ name: "Long Island Iced Tea", aka: "The Dare",
  flavor: "Five spirits, sour, and a splash of cola. Tastes like iced tea. Isn't.",
  pours: [{ slot: "Vodka — 0.5 oz", picks: [P("Skyy Vodka", "Nobody will know"), P("Grey Goose Vodka", "Nobody will know here either")] },
          { slot: "Gin — 0.5 oz", picks: [P("Beefeater Gin", "Won't dominate the glass"), P("Tanqueray Gin", "Juniper will punch through")] }],
  recipe: ["0.5 oz Bacardi Rum", "0.5 oz Jose Cuervo Silver Tequila", "0.5 oz Cointreau", "1 oz Sour Mix", "Splash of Cola", "Lemon Twist Garnish"],
  story: "This isn't a drink, it's a dare. The only tea involved is the trouble you'll be in tomorrow.",
  hook: "A beautiful, delicious lie." },

{ name: "Adios", aka: "The Blue Long Island",
  flavor: "The Long Island, but blue, and with lemon-lime instead of cola.",
  pours: [{ slot: "Vodka — 0.5 oz", picks: [P("Skyy Vodka", "Blue drink, blue bottle"), P("Grey Goose Vodka", "Smoother goodbye")] },
          { slot: "Gin — 0.5 oz", picks: [P("Beefeater Gin", "Stays out of the way"), P("Tanqueray Gin", "Makes itself known")] },
          { slot: "Color — 0.75 oz", picks: [P("Blue Curacao", "The reason anyone orders this")] }],
  recipe: ["0.5 oz Bacardi Rum", "0.5 oz Jose Cuervo Silver Tequila", "1 oz Sour Mix", "Fill a tall glass with Sprite", "Lime Wedge Garnish"],
  story: "The Long Island's louder cousin. If someone orders one of these at last call, say goodbye now. That's what it's named for.",
  hook: "Say your goodbyes early." },

/* ===== NO ALCOHOL ===== */
{ name: "Shirley Temple", aka: "Crusher's Order",
  flavor: "Lemon-lime, grenadine, cherry. Sweet and completely unashamed.",
  pours: [],
  recipe: ["Fill a tall glass with Sprite", "0.5 oz Grenadine", "Cherry Garnish"],
  story: "Our biggest, meanest member orders this. Not for his kid. For himself. He says it calms his inner rage. You WILL tell him it's a manly drink.",
  hook: "The toughest drink in the bar." },

{ name: "Roy Rogers", aka: "The Designated Rider",
  flavor: "Cola, grenadine, cherry. The other one.",
  pours: [],
  recipe: ["Fill a tall glass with Cola", "0.5 oz Grenadine", "Cherry Garnish"],
  story: "Somebody has to get everyone home. Whoever's holding this glass is the most important person in the room, and we make sure they know it.",
  hook: "The most important drink here." }
];

/* attach art */
MENU.forEach((d, i) => { d.image = IMAGE_POOL[i % IMAGE_POOL.length]; });

/* ---------- derive categories & availability ---------- */
function parseIngredient(line) {
    let name = line.replace(/^[\d./\s-]+(oz|dashes|dash)\s*/i, '');
    const phrases = ['Fill a tall glass with ', 'Fill with ', 'Top with ', 'Float the ', 'Splash of ', 'Splash ', 'Dash of '];
    for (const p of phrases) {
        if (name.toLowerCase().startsWith(p.toLowerCase())) {
            name = name.substring(p.length);
            const i = name.toLowerCase().indexOf(' in a');
            if (i > -1) name = name.substring(0, i);
            const j = name.toLowerCase().indexOf(' on top');
            if (j > -1) name = name.substring(0, j);
            break;
        }
    }
    name = name.replace(/,\s*\d+\s*dashes?$/i, '').trim();
    return ALL_INGREDIENTS.includes(name) ? name : null;
}

function allIngredientsOf(d) {
    const out = [];
    d.recipe.forEach(line => { const n = parseIngredient(line); if (n) out.push(n); });
    return out;
}

MENU.forEach(d => {
    const text = (d.recipe.join(' ') + ' ' + d.pours.map(p => p.slot).join(' ')).toLowerCase();
    const cats = new Set();
    if (/orange juice|pineapple juice|cranberry juice|sour mix/.test(text)) cats.add('Brunch');
    if (/club soda|tonic water|sprite/.test(text)) cats.add('Lunch');
    if (/cola/.test(text)) cats.add('Dinner');
    const dessert = d.pours.some(p => p.picks.some(k => /Baileys|Kahlúa|Amaretto|Butterscotch|Root Beer/.test(k.n)));
    if (dessert) cats.add('Dessert');
    if (cats.size === 0) cats.add('Dinner');
    d.category = Array.from(cats);

    const fams = new Set();
    d.pours.forEach(p => p.picks.forEach(k => { if (SPIRIT_FAMILY[k.n]) fams.add(SPIRIT_FAMILY[k.n]); }));
    d.recipe.forEach(l => { const n = parseIngredient(l); if (n && SPIRIT_FAMILY[n]) fams.add(SPIRIT_FAMILY[n]); });
    d.families = Array.from(fams);
    d.fixedIngredients = allIngredientsOf(d);
});

MENU.sort((a, b) => a.name.localeCompare(b.name));

/* barcode / table-of-contents card up front */
const BARCODE = {
    name: "Scan to Connect", isBarcode: true,
    image: 'https://raw.githubusercontent.com/aarmax8/Nomads/e4ef12fb2bff260fe0d7de78741a3ec2307e381d/3dbarcode.JPG?raw=true',
    recipe: [], pours: [], category: [], families: [], fixedIngredients: [],
    flavor: "A gateway to the digital road.", hook: "Point your camera here.", story: ""
};
const CARDS = [BARCODE, ...MENU];

/* ---------- STATE ---------- */
const STOCK_KEY = 'nomads_stock_v3';
const FAVES_KEY = 'nomads_faves_v3';

let barStock = {};
let favorites = [];
let filters = { category: 'all', family: null, favesOnly: false };
let storyView = false;

try { barStock = JSON.parse(store.get(STOCK_KEY)) || {}; } catch (e) { barStock = {}; }
if (!Object.keys(barStock).length) ALL_INGREDIENTS.forEach(i => barStock[i] = true);
try { favorites = JSON.parse(store.get(FAVES_KEY)) || []; } catch (e) { favorites = []; }

const saveStock = () => store.set(STOCK_KEY, JSON.stringify(barStock));
const saveFaves = () => store.set(FAVES_KEY, JSON.stringify(favorites));
const inStock = n => barStock[n] !== false;

/* A drink is makeable when every fixed ingredient is in stock AND
   every pour slot still has at least one pick on the shelf. */
function isMakeable(d) {
    if (d.isBarcode) return true;
    if (!d.fixedIngredients.every(inStock)) return false;
    return d.pours.every(p => p.picks.some(k => inStock(k.n)));
}

/* ---------- RENDER ---------- */
const menuGrid = document.getElementById('menu-grid');

function recipeLine(line) {
    const name = parseIngredient(line);
    const [icon, color] = iconFor(name || line);
    const missing = name && !inStock(name);
    return `<li class="${missing ? 'is-missing' : ''}"><i class="fas ${icon}" style="color:${color}"></i><span>${line}</span></li>`;
}

function pourBlock(d) {
    if (!d.pours.length) return '';
    const slots = d.pours.map(p => {
        const badges = p.picks.map((k, i) => {
            const out = !inStock(k.n);
            const cls = out ? 'is-out' : (i === 0 ? 'is-top' : '');
            const star = (i === 0 && !out) ? '★ ' : '';
            return `<span class="card-pour-badge ${cls}">${star}${k.n}<span class="why">${k.why}</span></span>`;
        }).join('');
        return `<span class="pour-slot-label">${p.slot}</span>${badges}`;
    }).join('');
    return `<div class="card-pour-options">${slots}</div>`;
}

function cardHTML(d, idx) {
    if (d.isBarcode) {
        const toc = CARDS.map((c, i) => c.isBarcode ? '' :
            `<div class="toc-item" data-goto="${i}" style="border-color:#f59e0b;color:#fbbf24">${c.name}</div>`).join('');
        return `
        <div class="drink-card" data-idx="${idx}" data-is-barcode="true" data-name="${d.name}">
          <div class="drink-card-inner">
            <div class="drink-card-front">
              <h3 class="drink-card-title">${d.name}</h3>
              <img src="${d.image}" alt="QR code">
              <div class="card-hook-tagline" style="border:none">${d.hook}</div>
              <div style="color:#9ca3af;font-family:'Roboto Condensed',sans-serif;font-size:.8rem">Tap for the full deck</div>
            </div>
            <div class="drink-card-back no-image">
              <div class="toc-category-header">The Deck</div>
              <div class="barcode-back-content">${toc}</div>
            </div>
          </div>
        </div>`;
    }

    const fav = favorites.includes(d.name);
    const bg = d.image ? `--bg-image:url('${d.image}')` : '';
    return `
    <div class="drink-card ${isMakeable(d) ? '' : 'is-unavailable'}" data-idx="${idx}" data-name="${d.name}">
      <div class="drink-card-inner">
        <div class="drink-card-front">
          <div class="card-header-front">
            <h3 class="drink-card-title">${d.name}</h3>
            ${d.aka ? `<div class="drink-card-subtitle">the ${d.aka}</div>` : ''}
            <button class="favorite-btn ${fav ? 'is-favorite' : ''}" data-fav="${d.name}" aria-label="Favorite ${d.name}">
              <i class="fas fa-heart"></i>
            </button>
          </div>
          <div class="recipe-content">
            <ul class="recipe-list-front">${d.recipe.map(recipeLine).join('')}</ul>
          </div>
          ${pourBlock(d)}
          <div class="card-footer"></div>
          <div class="card-hook-tagline">${d.hook}</div>
        </div>
        <div class="drink-card-back ${d.image ? '' : 'no-image'}" style="${bg}">
          <div class="card-back-content">
            <p class="story-text">${d.story}</p>
          </div>
          <div class="card-footer-back">${d.flavor}</div>
        </div>
      </div>
    </div>`;
}

function visibleCards() {
    return CARDS.filter(d => {
        if (d.isBarcode) return true;
        if (filters.favesOnly && !favorites.includes(d.name)) return false;
        if (filters.category !== 'all' && !d.category.includes(filters.category)) return false;
        if (filters.family && !d.families.includes(filters.family)) return false;
        return true;
    });
}

function render() {
    const list = visibleCards();
    menuGrid.innerHTML = list.map(d => cardHTML(d, CARDS.indexOf(d))).join('');
    if (storyView) menuGrid.querySelectorAll('.drink-card').forEach(c => c.classList.add('is-flipped'));
    updateActionBar();
}

function updateActionBar() {
    document.getElementById('action-favorites-btn').classList.toggle('is-active', filters.favesOnly);
    const active = filters.category !== 'all' || filters.family;
    document.getElementById('action-filter-btn').classList.toggle('is-active-filter', !!active);
    document.getElementById('story-view-btn').classList.toggle('is-active', storyView);
}

/* ---------- interactions ---------- */
menuGrid.addEventListener('click', e => {
    const favBtn = e.target.closest('.favorite-btn');
    if (favBtn) {
        e.stopPropagation();
        const n = favBtn.dataset.fav;
        const i = favorites.indexOf(n);
        if (i > -1) favorites.splice(i, 1); else favorites.push(n);
        saveFaves();
        favBtn.classList.toggle('is-favorite');
        if (filters.favesOnly) render();
        return;
    }
    const toc = e.target.closest('.toc-item');
    if (toc) {
        e.stopPropagation();
        const card = menuGrid.querySelector(`.drink-card[data-idx="${toc.dataset.goto}"]`);
        if (card) {
            menuGrid.querySelectorAll('.drink-card').forEach(c => c.classList.remove('is-highlighted'));
            card.scrollIntoView({ behavior: 'smooth', block: 'nearest', inline: 'center' });
            card.classList.add('is-highlighted');
            setTimeout(() => card.classList.remove('is-highlighted'), 2000);
        }
        return;
    }
    const card = e.target.closest('.drink-card');
    if (card) card.classList.toggle('is-flipped');
});

function snap(dir) {
    const cards = [...menuGrid.querySelectorAll('.drink-card')];
    if (!cards.length) return;
    const r = menuGrid.getBoundingClientRect();
    const mid = r.left + r.width / 2;
    let best = 0, min = Infinity;
    cards.forEach((c, i) => {
        const cr = c.getBoundingClientRect();
        const d = Math.abs(mid - (cr.left + cr.width / 2));
        if (d < min) { min = d; best = i; }
    });
    const t = cards[Math.max(0, Math.min(cards.length - 1, best + dir))];
    if (t) t.scrollIntoView({ behavior: 'smooth', block: 'nearest', inline: 'center' });
}

document.getElementById('scroll-next-btn').onclick = () => snap(1);
document.getElementById('scroll-prev-btn').onclick = () => snap(-1);
document.getElementById('scroll-home-btn').onclick = () => {
    const f = menuGrid.querySelector('.drink-card');
    if (f) f.scrollIntoView({ behavior: 'smooth', inline: 'center' });
};
document.getElementById('story-view-btn').onclick = () => {
    storyView = !storyView;
    menuGrid.querySelectorAll('.drink-card').forEach(c => c.classList.toggle('is-flipped', storyView));
    updateActionBar();
};
document.getElementById('action-random-btn').onclick = () => {
    const cards = [...menuGrid.querySelectorAll('.drink-card:not([data-is-barcode])')]
        .filter(c => !c.classList.contains('is-unavailable'));
    if (!cards.length) return;
    const c = cards[Math.floor(Math.random() * cards.length)];
    c.scrollIntoView({ behavior: 'smooth', block: 'nearest', inline: 'center' });
    c.classList.add('is-highlighted');
    setTimeout(() => c.classList.remove('is-highlighted'), 2000);
};
document.getElementById('action-favorites-btn').onclick = () => openModal('favorites-modal');

let isGrid = false;
document.getElementById('action-view-btn').onclick = e => {
    isGrid = !isGrid;
    menuGrid.className = isGrid ? 'grid-view' : 'carousel-view';
    const b = e.currentTarget;
    b.querySelector('span').textContent = isGrid ? 'Card View' : 'Desktop View';
    b.querySelector('i').className = isGrid ? 'fas fa-rectangle-list' : 'fas fa-table-cells-large';
};

/* ---------- modals ---------- */
function openModal(id) {
    const m = document.getElementById(id);
    m.classList.remove('hidden');
    requestAnimationFrame(() => m.classList.remove('opacity-0'));
}
function closeModal(id) {
    const m = document.getElementById(id);
    m.classList.add('opacity-0');
    setTimeout(() => m.classList.add('hidden'), 300);
}
['bar-stock-modal', 'filter-modal', 'favorites-modal'].forEach(id => {
    document.getElementById(id).addEventListener('click', e => { if (e.target.id === id) closeModal(id); });
});
document.getElementById('close-stock-btn').onclick = () => closeModal('bar-stock-modal');
document.getElementById('close-filter-btn').onclick = () => closeModal('filter-modal');
document.getElementById('close-favorites-btn').onclick = () => closeModal('favorites-modal');

/* Stock */
function renderStock() {
    const el = document.getElementById('bar-stock-content');
    el.innerHTML = Object.entries(ingredientCategories).map(([group, subs]) => `
        <div class="stock-group-title">${group}</div>
        ${Object.entries(subs).map(([sub, items]) => `
            <div class="stock-sub-title">${sub}</div>
            <div class="grid grid-cols-2 sm:grid-cols-3 gap-2">
                ${items.map(i => `
                    <button class="stock-btn ${inStock(i) ? 'in-stock' : ''}" data-ing="${i}">
                        <i class="fas ${inStock(i) ? 'fa-check' : 'fa-xmark'}"></i><span>${i}</span>
                    </button>`).join('')}
            </div>`).join('')}
    `).join('');
    const n = MENU.filter(isMakeable).length;
    document.getElementById('stock-summary').textContent = `${n} of ${MENU.length} drinks pourable with what's on the shelf.`;
}
document.getElementById('bar-stock-content').addEventListener('click', e => {
    const b = e.target.closest('.stock-btn');
    if (!b) return;
    const i = b.dataset.ing;
    barStock[i] = !inStock(i);
    saveStock(); renderStock(); render();
});
document.getElementById('stock-all-btn').onclick = () => { ALL_INGREDIENTS.forEach(i => barStock[i] = true); saveStock(); renderStock(); render(); };
document.getElementById('stock-none-btn').onclick = () => { ALL_INGREDIENTS.forEach(i => barStock[i] = false); saveStock(); renderStock(); render(); };
document.getElementById('action-stock-btn').onclick = () => { renderStock(); openModal('bar-stock-modal'); };

/* Filters */
const CATEGORIES = ['all', 'Brunch', 'Lunch', 'Dinner', 'Dessert'];
const FAMILIES = Object.keys(ingredientCategories.Spirits);

function renderFilters() {
    document.getElementById('filter-modal-content').innerHTML = `
        <div class="stock-sub-title">Time of Day</div>
        <div class="flex flex-wrap gap-2">
            ${CATEGORIES.map(c => `<button class="filter-pill ${filters.category === c ? 'is-active' : ''}" data-cat="${c}">${c === 'all' ? 'All' : c}</button>`).join('')}
        </div>
        <div class="stock-sub-title">Base Spirit</div>
        <div class="flex flex-wrap gap-2">
            ${FAMILIES.map(f => `<button class="filter-pill ${filters.family === f ? 'is-active' : ''}" data-fam="${f}">${f}</button>`).join('')}
        </div>
        <div class="stock-sub-title">Only</div>
        <div class="flex flex-wrap gap-2">
            <button class="filter-pill ${filters.favesOnly ? 'is-active' : ''}" data-faves="1">Favorites</button>
        </div>`;
}
document.getElementById('filter-modal-content').addEventListener('click', e => {
    const p = e.target.closest('.filter-pill');
    if (!p) return;
    if (p.dataset.cat) filters.category = p.dataset.cat;
    if (p.dataset.fam) filters.family = (filters.family === p.dataset.fam) ? null : p.dataset.fam;
    if (p.dataset.faves) filters.favesOnly = !filters.favesOnly;
    renderFilters();
});
document.getElementById('reset-filters-btn').onclick = () => {
    filters = { category: 'all', family: null, favesOnly: false };
    renderFilters(); render();
};
document.getElementById('apply-filters-btn').onclick = () => { render(); closeModal('filter-modal'); };
document.getElementById('action-filter-btn').onclick = () => { renderFilters(); openModal('filter-modal'); };

/* Favorites list */
function renderFavorites() {
    const el = document.getElementById('favorites-list-container');
    if (!favorites.length) {
        el.innerHTML = `<p class="text-gray-400 text-center py-8">No favorites yet. Tap the heart on any card.</p>`;
        return;
    }
    el.innerHTML = favorites.slice().sort().map(n =>
        `<div class="favorite-item" data-name="${n}"><i class="fas fa-heart text-amber-500 mr-3"></i><span>${n}</span></div>`).join('');
}
document.getElementById('favorites-list-container').addEventListener('click', e => {
    const it = e.target.closest('.favorite-item');
    if (!it) return;
    closeModal('favorites-modal');
    const card = menuGrid.querySelector(`.drink-card[data-name="${CSS.escape(it.dataset.name)}"]`);
    if (card) {
        card.scrollIntoView({ behavior: 'smooth', block: 'nearest', inline: 'center' });
        card.classList.add('is-highlighted');
        setTimeout(() => card.classList.remove('is-highlighted'), 2000);
    }
});
document.getElementById('action-favorites-btn').onclick = () => { renderFavorites(); openModal('favorites-modal'); };

/* Splash */
const splash = document.getElementById('splash-screen');
splash.addEventListener('click', () => {
    splash.classList.add('is-hidden');
    setTimeout(() => splash.remove(), 800);
});

/* Go */
render();
</script>
</body>
</html>
