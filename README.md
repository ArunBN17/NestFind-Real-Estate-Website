# NestFind-Real-Estate-Website
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>NestFinder — Find Your Perfect Home</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700;900&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet" />
<style>
  :root {
    --cream: #faf7f2;
    --dark: #1a1a2e;
    --charcoal: #2d2d3f;
    --gold: #c9963a;
    --gold-light: #e8b85a;
    --sage: #5a7a5e;
    --rust: #c0533a;
    --text: #3a3a4a;
    --muted: #8a8a9a;
    --border: rgba(0,0,0,0.08);
    --card-shadow: 0 4px 24px rgba(0,0,0,0.08), 0 1px 4px rgba(0,0,0,0.04);
    --card-hover: 0 12px 40px rgba(0,0,0,0.14), 0 2px 8px rgba(0,0,0,0.06);
  }
  * { margin:0; padding:0; box-sizing:border-box; }
  html { scroll-behavior: smooth; }
  body { font-family: 'DM Sans', sans-serif; background: var(--cream); color: var(--text); }

  /* ─── NAV ─────────────────────────────────────── */
  nav {
    position: fixed; top:0; left:0; right:0; z-index:100;
    background: rgba(250,247,242,0.92);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border);
    padding: 0 5%;
    display: flex; align-items: center; justify-content: space-between;
    height: 68px;
  }
  .nav-logo { font-family: 'Playfair Display', serif; font-size: 22px; font-weight: 700; color: var(--dark); letter-spacing: -0.02em; }
  .nav-logo span { color: var(--gold); }
  .nav-links { display:flex; gap:28px; list-style:none; }
  .nav-links a { text-decoration:none; color: var(--text); font-size:14px; font-weight:500; transition: color 0.2s; }
  .nav-links a:hover { color: var(--gold); }
  .nav-links a.nav-active { color: var(--gold); border-bottom: 2px solid var(--gold); padding-bottom: 2px; }
  .nav-cta { background: var(--dark); color: #fff; border:none; padding: 10px 22px; border-radius: 8px; font-size:14px; font-weight:500; cursor:pointer; transition: background 0.2s; font-family: 'DM Sans', sans-serif; }
  .nav-cta:hover { background: var(--charcoal); }

  /* ─── HERO ─────────────────────────────────────── */
  .hero {
    min-height: 100vh;
    background: linear-gradient(160deg, #1a1a2e 0%, #2d2d3f 40%, #3d3520 100%);
    display: flex; align-items: center;
    position: relative; overflow: hidden;
    padding: 100px 5% 60px;
  }
  .hero::before {
    content:'';
    position:absolute; inset:0;
    background: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23ffffff' fill-opacity='0.03'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
  }
  .hero-content { position:relative; z-index:2; max-width: 680px; }
  .hero-badge { display:inline-flex; align-items:center; gap:8px; background: rgba(201,150,58,0.15); border:1px solid rgba(201,150,58,0.3); color: var(--gold-light); padding:6px 14px; border-radius:20px; font-size:12px; font-weight:500; letter-spacing:0.08em; text-transform:uppercase; margin-bottom:24px; }
  .hero h1 { font-family:'Playfair Display', serif; font-size: clamp(38px, 5vw, 64px); font-weight:900; color:#fff; line-height:1.1; letter-spacing:-0.02em; margin-bottom:18px; }
  .hero h1 em { color: var(--gold-light); font-style:normal; }
  .hero p { color: rgba(255,255,255,0.6); font-size:17px; line-height:1.7; margin-bottom:40px; max-width:520px; font-weight:300; }

  /* Search box */
  .search-box {
    background: #fff;
    border-radius: 16px;
    padding: 8px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.3);
    display: flex; flex-direction: column; gap: 8px;
  }
  .search-tabs { display:flex; gap:4px; padding: 4px 4px 0; }
  .s-tab { background:none; border:none; padding:8px 18px; border-radius:8px; font-size:13px; font-weight:500; cursor:pointer; color: var(--muted); font-family:'DM Sans', sans-serif; transition: all 0.2s; }
  .s-tab.active { background: var(--dark); color:#fff; }
  .search-row { display:flex; gap:8px; padding: 4px; }
  .search-input { flex:1; display:flex; align-items:center; gap:10px; background: var(--cream); border-radius:10px; padding: 12px 16px; }
  .search-input input { border:none; background:none; font-family:'DM Sans',sans-serif; font-size:14px; color: var(--text); outline:none; width:100%; }
  .search-input input::placeholder { color: var(--muted); }
  .search-select { background: var(--cream); border:none; border-radius:10px; padding:12px 16px; font-family:'DM Sans',sans-serif; font-size:14px; color: var(--text); outline:none; cursor:pointer; min-width:130px; }
  .search-btn { background: var(--gold); color:#fff; border:none; padding:12px 28px; border-radius:10px; font-size:15px; font-weight:600; cursor:pointer; font-family:'DM Sans',sans-serif; white-space:nowrap; transition: background 0.2s; }
  .search-btn:hover { background: var(--gold-light); }
  .hero-stats { display:flex; gap:32px; margin-top:36px; }
  .h-stat { color:rgba(255,255,255,0.9); }
  .h-stat strong { display:block; font-size:22px; font-weight:700; color:#fff; }
  .h-stat span { font-size:12px; color:rgba(255,255,255,0.5); letter-spacing:0.05em; }

  /* ─── SECTIONS ─────────────────────────────────── */
  section { padding: 80px 5%; }
  .section-header { display:flex; align-items:flex-end; justify-content:space-between; margin-bottom:40px; }
  .section-title { font-family:'Playfair Display',serif; font-size: clamp(26px,3vw,38px); font-weight:700; color: var(--dark); letter-spacing:-0.02em; }
  .section-title span { color: var(--gold); }
  .section-sub { color: var(--muted); font-size:14px; margin-top:6px; }
  .view-all { color: var(--gold); font-size:14px; font-weight:500; text-decoration:none; border-bottom:1px solid var(--gold); padding-bottom:2px; cursor:pointer; transition: opacity 0.2s; }
  .view-all:hover { opacity:0.7; }

  /* ─── CATEGORIES ────────────────────────────────── */
  .cats-grid { display:grid; grid-template-columns: repeat(6, 1fr); gap:16px; }
  .cat-card {
    background:#fff; border-radius:14px; padding:24px 16px; text-align:center;
    border:1px solid var(--border); cursor:pointer;
    transition: all 0.25s; position:relative; overflow:hidden;
  }
  .cat-card::after { content:''; position:absolute; inset:0; background: var(--gold); opacity:0; transition:opacity 0.25s; }
  .cat-card:hover { transform: translateY(-4px); box-shadow: var(--card-hover); }
  .cat-card:hover::after { opacity:0.04; }
  .cat-icon { font-size:32px; margin-bottom:10px; display:block; }
  .cat-label { font-size:13px; font-weight:600; color: var(--dark); }
  .cat-count { font-size:11px; color: var(--muted); margin-top:3px; }

  /* ─── PROPERTY CARDS ────────────────────────────── */
  .props-grid { display:grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap:24px; }
  .prop-card {
    background:#fff; border-radius:16px; overflow:hidden;
    box-shadow: var(--card-shadow);
    transition: all 0.3s; cursor:pointer; position:relative;
  }
  .prop-card:hover { transform: translateY(-6px); box-shadow: var(--card-hover); }
  .prop-img {
    height: 200px; position:relative; overflow:hidden;
    background: linear-gradient(135deg, #e8e0d0, #d4c9b0);
  }
  .prop-img .img-fill { width:100%; height:100%; object-fit:cover; display:flex; align-items:center; justify-content:center; font-size:60px; }
  .prop-badge { position:absolute; top:12px; left:12px; padding:4px 12px; border-radius:6px; font-size:11px; font-weight:600; letter-spacing:0.05em; text-transform:uppercase; }
  .badge-sale { background: var(--dark); color:#fff; }
  .badge-rent { background: var(--sage); color:#fff; }
  .badge-new { background: var(--gold); color:#fff; }
  .badge-owner { background: var(--sage); color:#fff; }
  .prop-fav { position:absolute; top:12px; right:12px; width:32px; height:32px; border-radius:50%; background:rgba(255,255,255,0.9); border:none; cursor:pointer; display:flex; align-items:center; justify-content:center; font-size:15px; transition: transform 0.2s; }
  .prop-fav:hover { transform:scale(1.15); }
  .prop-body { padding:18px; }
  .prop-price { font-family:'Playfair Display',serif; font-size:22px; font-weight:700; color: var(--dark); }
  .prop-price sup { font-size:14px; font-weight:400; }
  .prop-name { font-size:15px; font-weight:600; color: var(--text); margin:6px 0 4px; }
  .prop-loc { font-size:13px; color: var(--muted); display:flex; align-items:center; gap:4px; }
  .prop-divider { height:1px; background: var(--border); margin:14px 0; }
  .prop-specs { display:flex; gap:16px; }
  .prop-spec { display:flex; align-items:center; gap:5px; font-size:12px; color: var(--muted); }
  .prop-spec strong { color: var(--text); font-weight:600; }
  .prop-tag-row { display:flex; gap:6px; margin-top:12px; flex-wrap:wrap; }
  .prop-tag { background: #f5f0e8; color: var(--gold); font-size:11px; padding:3px 10px; border-radius:20px; font-weight:500; }

  /* ─── FEATURED BANNER ───────────────────────────── */
  .featured-banner {
    background: linear-gradient(135deg, var(--dark) 0%, #2a2040 100%);
    border-radius:20px; padding:60px 48px;
    display:grid; grid-template-columns:1fr 1fr; gap:40px; align-items:center;
  }
  .fb-left h2 { font-family:'Playfair Display',serif; font-size: clamp(28px,3vw,44px); font-weight:900; color:#fff; line-height:1.15; margin-bottom:16px; }
  .fb-left h2 em { color: var(--gold-light); font-style:normal; }
  .fb-left p { color:rgba(255,255,255,0.55); font-size:15px; line-height:1.7; margin-bottom:28px; }
  .fb-btn { background: var(--gold); color:#fff; border:none; padding:14px 32px; border-radius:10px; font-size:15px; font-weight:600; cursor:pointer; font-family:'DM Sans',sans-serif; transition: background 0.2s; }
  .fb-btn:hover { background: var(--gold-light); }
  .fb-right { display:grid; grid-template-columns:1fr 1fr; gap:14px; }
  .fb-stat { background:rgba(255,255,255,0.06); border:1px solid rgba(255,255,255,0.08); border-radius:14px; padding:20px; }
  .fb-stat strong { display:block; font-size:28px; font-weight:700; color:#fff; font-family:'Playfair Display',serif; }
  .fb-stat span { font-size:12px; color:rgba(255,255,255,0.45); margin-top:4px; display:block; }

  /* ─── AGENTS ────────────────────────────────────── */
  .agents-grid { display:grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap:20px; }
  .agent-card { background:#fff; border-radius:16px; padding:28px 20px; text-align:center; border:1px solid var(--border); transition: all 0.25s; }
  .agent-card:hover { transform:translateY(-4px); box-shadow: var(--card-hover); }
  .agent-avatar { width:72px; height:72px; border-radius:50%; margin:0 auto 14px; display:flex; align-items:center; justify-content:center; font-size:28px; border:3px solid var(--gold); }
  .agent-name { font-weight:600; font-size:16px; color: var(--dark); }
  .agent-title { font-size:12px; color: var(--muted); margin-top:3px; }
  .agent-stats { display:flex; gap:16px; justify-content:center; margin-top:14px; padding-top:14px; border-top:1px solid var(--border); }
  .ag-stat strong { display:block; font-size:16px; font-weight:700; color: var(--dark); }
  .ag-stat span { font-size:11px; color: var(--muted); }
  .agent-btn { margin-top:16px; width:100%; padding:9px; border:1.5px solid var(--gold); border-radius:8px; background:none; color: var(--gold); font-size:13px; font-weight:600; cursor:pointer; font-family:'DM Sans',sans-serif; transition: all 0.2s; }
  .agent-btn:hover { background: var(--gold); color:#fff; }

  /* ─── HOW IT WORKS ───────────────────────────────── */
  .hiw-section { background: var(--dark); }
  .hiw-section .section-title { color:#fff; }
  .hiw-section .section-sub { color:rgba(255,255,255,0.4); }
  .hiw-grid { display:grid; grid-template-columns: repeat(4, 1fr); gap:24px; }
  .hiw-card { text-align:center; padding:24px 16px; position:relative; }
  .hiw-card::after { content: '→'; position:absolute; right:-12px; top:36px; color:rgba(255,255,255,0.15); font-size:20px; }
  .hiw-card:last-child::after { display:none; }
  .hiw-num { width:52px; height:52px; border-radius:50%; border:2px solid var(--gold); color: var(--gold); font-size:18px; font-weight:700; display:flex; align-items:center; justify-content:center; margin:0 auto 16px; font-family:'Playfair Display',serif; }
  .hiw-card h4 { font-size:16px; font-weight:600; color:#fff; margin-bottom:8px; }
  .hiw-card p { font-size:13px; color:rgba(255,255,255,0.45); line-height:1.6; }

  /* ─── TESTIMONIALS ───────────────────────────────── */
  .testimonials-grid { display:grid; grid-template-columns: repeat(3,1fr); gap:24px; }
  .test-card { background:#fff; border-radius:16px; padding:28px; border:1px solid var(--border); }
  .test-stars { color: var(--gold); font-size:14px; margin-bottom:14px; letter-spacing:2px; }
  .test-text { font-size:14px; line-height:1.7; color: var(--text); font-style:italic; margin-bottom:20px; }
  .test-user { display:flex; align-items:center; gap:12px; }
  .test-avatar { width:40px; height:40px; border-radius:50%; background: linear-gradient(135deg, var(--gold), var(--rust)); display:flex; align-items:center; justify-content:center; font-size:16px; }
  .test-name { font-weight:600; font-size:14px; }
  .test-role { font-size:12px; color: var(--muted); }

  /* ─── CTA STRIP ─────────────────────────────────── */
  .cta-strip { background: var(--gold); padding:40px 5%; display:flex; align-items:center; justify-content:space-between; }
  .cta-strip h3 { font-family:'Playfair Display',serif; font-size:26px; font-weight:700; color:#fff; }
  .cta-strip p { color:rgba(255,255,255,0.75); font-size:14px; margin-top:4px; }
  .cta-strip-btn { background:#fff; color: var(--gold); border:none; padding:14px 32px; border-radius:10px; font-size:15px; font-weight:600; cursor:pointer; font-family:'DM Sans',sans-serif; white-space:nowrap; transition: transform 0.2s; }
  .cta-strip-btn:hover { transform:scale(1.03); }

  /* ─── FOOTER ─────────────────────────────────────── */
  footer { background: var(--dark); color:rgba(255,255,255,0.5); padding:60px 5% 32px; }
  .footer-grid { display:grid; grid-template-columns:2fr 1fr 1fr 1fr; gap:40px; margin-bottom:48px; }
  .footer-brand .nav-logo { font-size:24px; display:block; margin-bottom:14px; }
  .footer-brand p { font-size:13px; line-height:1.7; max-width:260px; }
  .footer-col h5 { color:#fff; font-size:14px; font-weight:600; margin-bottom:16px; letter-spacing:0.03em; }
  .footer-col ul { list-style:none; display:flex; flex-direction:column; gap:10px; }
  .footer-col a { color:rgba(255,255,255,0.45); font-size:13px; text-decoration:none; transition: color 0.2s; }
  .footer-col a:hover { color: var(--gold-light); }
  .footer-bottom { border-top:1px solid rgba(255,255,255,0.08); padding-top:24px; display:flex; justify-content:space-between; font-size:12px; }

  /* Animations */
  @keyframes fadeUp { from { opacity:0; transform:translateY(20px); } to { opacity:1; transform:translateY(0); } }
  .hero-content > * { animation: fadeUp 0.6s ease both; }
  .hero-badge { animation-delay: 0.1s; }
  .hero h1 { animation-delay: 0.2s; }
  .hero p { animation-delay: 0.3s; }
  .search-box { animation-delay: 0.4s; }
  .hero-stats { animation-delay: 0.5s; }

  @media (max-width:768px) {
    .cats-grid { grid-template-columns: repeat(3,1fr); }
    .hiw-grid { grid-template-columns: repeat(2,1fr); }
    .testimonials-grid { grid-template-columns:1fr; }
    .featured-banner { grid-template-columns:1fr; }
    .footer-grid { grid-template-columns:1fr 1fr; }
    .nav-links { display:none; }
    .search-row { flex-wrap:wrap; }
    .hero-stats { gap:20px; }
    .cta-strip { flex-direction:column; gap:20px; text-align:center; }
  }

  /* ─── MOBILE RESPONSIVE ─────────────────────────── */
  @media (max-width: 768px) {
    nav { padding: 0 4%; height: 60px; }
    .nav-links { display: none; }
    .nav-cta { display: none; }
    nav .mobile-menu-btn { display: flex !important; }
    
    .hero { padding: 80px 4% 40px; min-height: auto; }
    .hero h1 { font-size: 32px !important; min-height: auto !important; }
    .hero p { font-size: 14px; margin-bottom: 24px; }
    .search-row { flex-direction: column; }
    .search-select { min-width: unset; }
    .hero-stats { gap: 16px; flex-wrap: wrap; }
    .h-stat strong { font-size: 18px; }
    
    .cats-grid { grid-template-columns: repeat(3, 1fr); gap: 10px; }
    .cat-card { padding: 16px 8px; }
    .cat-icon { font-size: 26px; }
    .cat-label { font-size: 11px; }
    .cat-count { font-size: 10px; }
    
    .props-grid { grid-template-columns: 1fr; }
    .agents-grid { grid-template-columns: 1fr 1fr; }
    
    section { padding: 50px 4%; }
    .section-header { flex-direction: column; align-items: flex-start; gap: 10px; }
    .section-title { font-size: 24px !important; }
    
    .footer-grid { grid-template-columns: 1fr 1fr; gap: 24px; }
    
    #mapModal .map-wrapper { height: 300px !important; }
    
    .modal-content { margin: 0; border-radius: 16px 16px 0 0; position: fixed; bottom: 0; width: 100%; max-height: 90vh; overflow-y: auto; }
    .modal { align-items: flex-end; }
  }
  @media (max-width: 480px) {
    .cats-grid { grid-template-columns: repeat(2, 1fr); }
    .agents-grid { grid-template-columns: 1fr; }
    .footer-grid { grid-template-columns: 1fr; }
    .hero-stats { gap: 12px; }
  }

  /* Mobile hamburger menu */
  .mobile-menu-btn { display: none; background: none; border: none; cursor: pointer; flex-direction: column; gap: 5px; padding: 4px; }
  .mobile-menu-btn span { display: block; width: 22px; height: 2px; background: var(--text); border-radius: 2px; transition: all 0.3s; }
  .mobile-nav-drawer { display: none; position: fixed; top: 60px; left: 0; right: 0; background: rgba(250,247,242,0.98); backdrop-filter: blur(20px); border-bottom: 1px solid var(--border); z-index: 99; padding: 16px 4%; flex-direction: column; gap: 4px; }
  .mobile-nav-drawer.open { display: flex; }
  .mobile-nav-drawer a { padding: 12px 16px; border-radius: 10px; font-size: 15px; font-weight: 500; color: var(--text); text-decoration: none; display: block; }
  .mobile-nav-drawer a:hover { background: #f0ece4; color: var(--gold); }
  .mobile-nav-drawer .mob-post-btn { margin-top: 8px; background: var(--dark); color: #fff; border: none; padding: 13px 16px; border-radius: 10px; font-size: 15px; font-weight: 600; cursor: pointer; font-family: 'DM Sans', sans-serif; text-align: left; }

  </style>

  <!-- Firebase SDK -->
  <script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-app.js";
    import { getAuth, createUserWithEmailAndPassword, signInWithEmailAndPassword, signOut, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-auth.js";
    import { getFirestore, collection, doc, setDoc, getDoc, getDocs, addDoc, updateDoc, deleteDoc, onSnapshot, serverTimestamp } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-firestore.js";
    window.__firebaseModules = { initializeApp, getAuth, createUserWithEmailAndPassword, signInWithEmailAndPassword, signOut, onAuthStateChanged, getFirestore, collection, doc, setDoc, getDoc, getDocs, addDoc, updateDoc, deleteDoc, onSnapshot, serverTimestamp };
  </script>
  <!-- Leaflet Maps -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"/>
  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
  <!-- Razorpay -->
  <script src="https://checkout.razorpay.com/v1/checkout.js"></script>
</head>
<body>

<!-- ── AUTH GATE OVERLAY ─────────────────────────────── -->
<div id="authGate" style="position:fixed;inset:0;z-index:2000;background:linear-gradient(135deg,#1a1a2e 0%,#2d2d3f 50%,#3d3520 100%);display:flex;align-items:center;justify-content:center;padding:20px;">
  <div style="background:#fff;border-radius:24px;width:100%;max-width:460px;overflow:hidden;box-shadow:0 32px 80px rgba(0,0,0,0.4);">

    <!-- Auth Header Tabs -->
    <div style="display:flex;align-items:center;background:#f9f7f3;border-bottom:1px solid rgba(0,0,0,0.07);position:relative;">
      <button id="tabLogin" onclick="switchAuth('login')" style="flex:1;padding:18px;border:none;background:none;font-family:'DM Sans',sans-serif;font-size:15px;font-weight:600;color:#1a1a2e;cursor:pointer;border-bottom:3px solid #c9963a;">Login</button>
      <button id="tabSignup" onclick="switchAuth('signup')" style="flex:1;padding:18px;border:none;background:none;font-family:'DM Sans',sans-serif;font-size:15px;font-weight:600;color:#8a8a9a;cursor:pointer;border-bottom:3px solid transparent;">Sign Up</button>
    </div>

    <!-- Back Button (shown only on signup) -->
    <div id="backBtnRow" style="display:none;padding:16px 32px 0;">
      <button onclick="switchAuth('login')" style="display:flex;align-items:center;gap:8px;background:none;border:none;cursor:pointer;font-family:'DM Sans',sans-serif;font-size:14px;font-weight:600;color:#1a1a2e;padding:0;">
        <span style="width:32px;height:32px;border-radius:50%;background:#f5f0e8;border:1.5px solid #e0ddd6;display:flex;align-items:center;justify-content:center;font-size:16px;">←</span>
        Back to Login
      </button>
    </div>

    <div style="padding:32px;">
      <!-- Logo -->
      <div style="text-align:center;margin-bottom:24px;">
        <div style="font-family:'Playfair Display',serif;font-size:26px;font-weight:700;color:#1a1a2e;">Nest<span style="color:#c9963a;">Finder</span></div>
        <div id="authSubtitle" style="font-size:13px;color:#8a8a9a;margin-top:4px;">Welcome back! Login to continue</div>
      </div>

      <!-- Role Selector -->
      <div style="margin-bottom:20px;">
        <div style="font-size:12px;font-weight:600;color:#1a1a2e;letter-spacing:0.1em;text-transform:uppercase;margin-bottom:10px;">I am a</div>
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;">
          <button id="roleBuyer"  onclick="selectRole('buyer')"  style="padding:11px 8px;border:2px solid #c9963a;border-radius:12px;background:#fff8f0;font-family:'DM Sans',sans-serif;font-size:12px;font-weight:600;color:#c9963a;cursor:pointer;transition:all 0.2s;">🏠 Buyer / Renter</button>
          <button id="roleSeller" onclick="selectRole('seller')" style="padding:11px 8px;border:2px solid #e0ddd6;border-radius:12px;background:#fff;font-family:'DM Sans',sans-serif;font-size:12px;font-weight:600;color:#8a8a9a;cursor:pointer;transition:all 0.2s;">🏷️ Seller / Owner</button>
          <button id="roleWebowner" onclick="selectRole('webowner')" style="padding:11px 8px;border:2px solid #e0ddd6;border-radius:12px;background:#fff;font-family:'DM Sans',sans-serif;font-size:12px;font-weight:600;color:#8a8a9a;cursor:pointer;transition:all 0.2s;">🌐 Website Owner</button>
          <button id="roleAgent"  onclick="selectRole('agent')"  style="padding:11px 8px;border:2px solid #e0ddd6;border-radius:12px;background:#fff;font-family:'DM Sans',sans-serif;font-size:12px;font-weight:600;color:#8a8a9a;cursor:pointer;transition:all 0.2s;">👨‍💼 Agent</button>
        </div>
      </div>

      <!-- Website Owner hint -->
      <div id="webownerHint" style="display:none;background:#fff8f0;border:1px solid #f0dcc0;border-radius:10px;padding:10px 14px;margin-bottom:12px;font-size:12px;color:#c9963a;">
        🔐 Website Owner login gives you full access to manage agents, listings and site content.
      </div>

      <!-- Form Fields -->
      <div style="display:flex;flex-direction:column;gap:13px;" id="authFields">
        <div id="nameField" style="display:none;">
          <input id="auth-name" type="text" placeholder="Full Name" style="width:100%;padding:13px 16px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;box-sizing:border-box;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
        </div>
        <div id="cityField" style="display:none;">
          <select id="auth-city" style="width:100%;padding:13px 16px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;background:#fff;box-sizing:border-box;">
            <option value="">Select Your City in Karnataka</option>
            <option>Bangalore</option><option>Mysuru</option><option>Mangaluru</option>
            <option>Hubli-Dharwad</option><option>Belagavi</option><option>Davanagere</option>
            <option>Ballari</option><option>Shivamogga</option><option>Tumakuru</option><option>Other</option>
          </select>
        </div>
        <input id="auth-email" type="email" placeholder="Email Address" style="width:100%;padding:13px 16px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;box-sizing:border-box;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
        <div style="position:relative;">
          <input id="auth-pass" type="password" placeholder="Password" style="width:100%;padding:13px 16px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;box-sizing:border-box;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
          <button onclick="togglePassVis()" style="position:absolute;right:14px;top:50%;transform:translateY(-50%);background:none;border:none;cursor:pointer;font-size:16px;" id="eyeBtn">👁️</button>
        </div>
        <div id="agentLicField" style="display:none;">
          <input id="auth-lic" type="text" placeholder="RERA Agent License Number" style="width:100%;padding:13px 16px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;box-sizing:border-box;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
        </div>
      </div>

      <!-- Error msg -->
      <div id="authError" style="display:none;color:#c0533a;font-size:13px;margin-top:10px;padding:10px 14px;background:#fff0ee;border-radius:8px;"></div>

      <!-- Submit -->
      <button id="authSubmitBtn" onclick="handleAuth()" style="width:100%;margin-top:18px;background:#1a1a2e;color:#fff;border:none;padding:15px;border-radius:12px;font-size:16px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;transition:background 0.2s;" onmouseover="this.style.background='#c9963a'" onmouseout="this.style.background='#1a1a2e'">Login →</button>

      <!-- Divider -->
      <div style="display:flex;align-items:center;gap:12px;margin:18px 0;">
        <div style="flex:1;height:1px;background:#e0ddd6;"></div>
        <span style="font-size:12px;color:#aaa;">or continue with</span>
        <div style="flex:1;height:1px;background:#e0ddd6;"></div>
      </div>

      <!-- Social Buttons -->
      <div style="display:flex;gap:10px;">
        <button onclick="socialLogin('Google')" style="flex:1;padding:11px;border:1.5px solid #e0ddd6;border-radius:10px;background:#fff;font-family:'DM Sans',sans-serif;font-size:13px;font-weight:500;cursor:pointer;transition:border-color 0.2s;" onmouseover="this.style.borderColor='#c9963a'" onmouseout="this.style.borderColor='#e0ddd6'">🌐 Google</button>
        <button onclick="socialLogin('Phone')" style="flex:1;padding:11px;border:1.5px solid #e0ddd6;border-radius:10px;background:#fff;font-family:'DM Sans',sans-serif;font-size:13px;font-weight:500;cursor:pointer;transition:border-color 0.2s;" onmouseover="this.style.borderColor='#c9963a'" onmouseout="this.style.borderColor='#e0ddd6'">📱 Phone OTP</button>
      </div>

      <div style="text-align:center;margin-top:16px;font-size:13px;color:#8a8a9a;">
        <span id="authToggleText">Don't have an account?</span>
        <button onclick="switchAuth(currentMode==='login'?'signup':'login')" style="background:none;border:none;color:#c9963a;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;font-size:13px;margin-left:4px;" id="authToggleBtn">Sign Up</button>
      </div>
    </div>
  </div>
</div>

<!-- NAV -->

<!-- SETUP BANNER -->
<div id="setupBanner" style="background:linear-gradient(90deg,#1a1a2e,#2d3748);color:#fff;padding:10px 5%;display:flex;align-items:center;justify-content:space-between;font-size:12px;gap:10px;position:relative;z-index:200;">
  <div style="display:flex;align-items:center;gap:8px;flex-wrap:wrap;">
    <span style="background:#c9963a;padding:2px 8px;border-radius:4px;font-weight:700;font-size:10px;">SETUP GUIDE</span>
    <span style="opacity:0.8;">🔐 Add <strong style="color:#e8b85a;">Firebase config</strong> for real login & database · 💳 Add <strong style="color:#e8b85a;">Razorpay key</strong> for payments · 🗺️ Map works now (OpenStreetMap, free!)</span>
  </div>
  <button onclick="this.parentElement.style.display='none'" style="background:rgba(255,255,255,0.1);border:none;color:#fff;padding:4px 10px;border-radius:6px;cursor:pointer;font-size:11px;white-space:nowrap;">Dismiss ✕</button>
</div>
<nav>
  <div class="nav-logo">Nest<span>Finder</span></div>
  <button class="mobile-menu-btn" onclick="toggleMobileNav()" id="mobileMenuBtn">
    <span></span><span></span><span></span>
  </button>
  <ul class="nav-links">
    <li><a href="#" id="navHome">🏠 Home</a></li>
    <li><a href="#">Buy</a></li>
    <li><a href="#">Rent</a></li>
    <li><a href="#">Sell</a></li>
    <li><a href="#">New Projects</a></li>
    <li><a href="#">Agents</a></li>
  </ul>
  <button class="nav-cta" id="navPostBtn">Post Property Free</button>
  <div id="navUser" style="display:none;align-items:center;gap:10px;">
    <button id="ownerEditBtn" onclick="openOwnerPanel()" style="display:none;background:#c9963a;color:#fff;border:none;padding:9px 16px;border-radius:8px;font-size:13px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;align-items:center;gap:6px;">⚙️ Edit Agents</button>
    <div id="navUserAvatar" style="width:36px;height:36px;border-radius:50%;background:linear-gradient(135deg,#c9963a,#e8b85a);display:flex;align-items:center;justify-content:center;font-size:15px;cursor:pointer;" onclick="toggleUserMenu()">👤</div>
    <div id="userMenu" style="display:none;position:absolute;top:60px;right:5%;background:#fff;border-radius:14px;padding:8px;box-shadow:0 8px 32px rgba(0,0,0,0.15);min-width:180px;z-index:200;">
      <div id="userMenuName" style="padding:10px 14px;font-weight:600;font-size:14px;color:#1a1a2e;border-bottom:1px solid #f0ece4;margin-bottom:4px;"></div>
      <button onclick="showToast('📋 My listings coming soon!')" style="width:100%;text-align:left;padding:10px 14px;border:none;background:none;font-family:'DM Sans',sans-serif;font-size:13px;cursor:pointer;border-radius:8px;color:#3a3a4a;" onmouseover="this.style.background='#f9f7f3'" onmouseout="this.style.background='none'">🏠 My Properties</button>
      <button onclick="showToast('❤️ Wishlist coming soon!')" style="width:100%;text-align:left;padding:10px 14px;border:none;background:none;font-family:'DM Sans',sans-serif;font-size:13px;cursor:pointer;border-radius:8px;color:#3a3a4a;" onmouseover="this.style.background='#f9f7f3'" onmouseout="this.style.background='none'">❤️ Wishlist</button>
      <button onclick="logout()" style="width:100%;text-align:left;padding:10px 14px;border:none;background:none;font-family:'DM Sans',sans-serif;font-size:13px;cursor:pointer;border-radius:8px;color:#c0533a;" onmouseover="this.style.background='#fff0ee'" onmouseout="this.style.background='none'">🚪 Logout</button>
    </div>
  </div>
</nav>

<!-- MOBILE NAV DRAWER -->
<div class="mobile-nav-drawer" id="mobileNavDrawer">
  <a href="#" onclick="closeMobileNav();window.scrollTo({top:0,behavior:'smooth'})">🏠 Home</a>
  <a href="#" onclick="closeMobileNav();filterNav('buy')">🏠 Buy</a>
  <a href="#" onclick="closeMobileNav();filterNav('rent')">🏡 Rent</a>
  <a href="#" onclick="closeMobileNav();openPostProperty()">💰 Sell</a>
  <a href="#" onclick="closeMobileNav();filterNav('new')">🏗️ New Projects</a>
  <a href="#" onclick="closeMobileNav();document.getElementById('agentsGrid').scrollIntoView({behavior:'smooth'})">👨‍💼 Agents</a>
  <button class="mob-post-btn" onclick="closeMobileNav();openPostProperty()">Post Property Free →</button>
</div>

<!-- HERO -->
<section class="hero">
  <div class="hero-content">
    <div class="hero-badge">🏆 Karnataka's #1 Real Estate Platform</div>
    <h1 id="heroHeadline" style="min-height:2.3em;transition:opacity 0.4s ease;">Find Your <em>Dream Home</em><br/>in Your Dream City</h1>
    <p>Discover thousands of verified properties for sale and rent across Bangalore, Mysuru, Mangaluru, Hubli and more. Expert guidance at every step.</p>

    <div class="search-box">
      <div class="search-tabs">
        <button class="s-tab active" onclick="setTab(this)">Buy</button>
        <button class="s-tab" onclick="setTab(this)">Rent</button>
        <button class="s-tab" onclick="setTab(this)">New Projects</button>
        <button class="s-tab" onclick="setTab(this)">Commercial</button>
        <button class="s-tab" onclick="setTab(this)">Plots</button>
      </div>
      <div class="search-row">
        <div class="search-input" style="flex:2">
          <span>📍</span>
          <input type="text" placeholder="Search Bangalore, Mysuru, Mangaluru, Hubli..." />
        </div>
        <select class="search-select">
          <option>Property Type</option>
          <option>Apartment</option>
          <option>Villa</option>
          <option>Plot</option>
          <option>Commercial</option>
        </select>
        <select class="search-select">
          <option>Budget</option>
          <option>Under ₹50L</option>
          <option>₹50L – ₹1Cr</option>
          <option>₹1Cr – ₹3Cr</option>
          <option>Above ₹3Cr</option>
        </select>
        <button class="search-btn" onclick="handleSearch()">Search</button>
      </div>
    </div>

    <div class="hero-stats">
      <div class="h-stat"><strong>1.2L+</strong><span>PROPERTIES</span></div>
      <div class="h-stat"><strong>8,000+</strong><span>VERIFIED AGENTS</span></div>
      <div class="h-stat"><strong>30+</strong><span>KA CITIES</span></div>
      <div class="h-stat"><strong>5L+</strong><span>HAPPY USERS</span></div>
    </div>
  </div>
</section>

<!-- CATEGORIES -->
<section style="padding:60px 5% 40px;">
  <div class="section-header">
    <div>
      <div class="section-title">Browse by <span>Category</span></div>
      <div class="section-sub">Find exactly what you're looking for</div>
    </div>
  </div>
  <div class="cats-grid">
    <div class="cat-card"><span class="cat-icon">🏢</span><div class="cat-label">Apartment</div><div class="cat-count">8,42,000+ listings</div></div>
    <div class="cat-card"><span class="cat-icon">🏡</span><div class="cat-label">Villa / House</div><div class="cat-count">3,18,000+ listings</div></div>
    <div class="cat-card"><span class="cat-icon">🌳</span><div class="cat-label">Plot / Land</div><div class="cat-count">5,60,000+ listings</div></div>
    <div class="cat-card"><span class="cat-icon">🏗️</span><div class="cat-label">New Projects</div><div class="cat-count">22,000+ projects</div></div>
    <div class="cat-card"><span class="cat-icon">🏬</span><div class="cat-label">Commercial</div><div class="cat-count">1,90,000+ listings</div></div>
    <div class="cat-card"><span class="cat-icon">🏘️</span><div class="cat-label">PG / Hostel</div><div class="cat-count">4,50,000+ listings</div></div>
  </div>
</section>

<!-- FEATURED PROPERTIES -->
<section>
  <div class="section-header">
    <div>
      <div class="section-title">Featured <span>Properties</span></div>
      <div class="section-sub">Hand-picked listings from verified sellers</div>
    </div>
    <a class="view-all">View All Properties →</a>
  </div>
  <div class="props-grid" id="propsGrid"></div>
</section>

<!-- FEATURED BANNER -->
<section style="padding:0 5% 80px;">
  <div class="featured-banner">
    <div class="fb-left">
      <h2>List Your Property &<br/><em>Reach Millions</em></h2>
      <p>Post your property for free and connect with genuine buyers and tenants across India. Verified leads, zero commissions.</p>
      <button class="fb-btn">Post Property Free →</button>
    </div>
    <div class="fb-right">
      <div class="fb-stat"><strong>2.4M+</strong><span>Active Listings</span></div>
      <div class="fb-stat"><strong>12M+</strong><span>Monthly Visitors</span></div>
      <div class="fb-stat"><strong>98%</strong><span>Verified Profiles</span></div>
      <div class="fb-stat"><strong>₹0</strong><span>Listing Cost</span></div>
    </div>
  </div>
</section>

<!-- HOW IT WORKS -->
<section class="hiw-section">
  <div class="section-header">
    <div>
      <div class="section-title">How It <span style="color:var(--gold-light)">Works</span></div>
      <div class="section-sub">Your journey to a new home in 4 simple steps</div>
    </div>
  </div>
  <div class="hiw-grid">
    <div class="hiw-card"><div class="hiw-num">1</div><h4>Search Properties</h4><p>Use smart filters to find properties that match your budget, location, and preferences.</p></div>
    <div class="hiw-card"><div class="hiw-num">2</div><h4>Shortlist & Compare</h4><p>Save your favorites, compare specs side by side and schedule site visits online.</p></div>
    <div class="hiw-card"><div class="hiw-num">3</div><h4>Connect with Owner</h4><p>Directly chat or call verified owners and agents — no middlemen, no hidden fees.</p></div>
    <div class="hiw-card"><div class="hiw-num">4</div><h4>Close the Deal</h4><p>Get legal assistance, loan support, and move-in coordination — all in one place.</p></div>
  </div>
</section>

<!-- TOP AGENTS -->
<section>
  <div class="section-header">
    <div>
      <div class="section-title">Top <span>Agents</span></div>
      <div class="section-sub">Work with the best in the business</div>
    </div>
    <div style="display:flex;gap:12px;align-items:center;">
      <a class="view-all">Find More Agents →</a>
    </div>
  </div>
  <div class="agents-grid" id="agentsGrid"></div>
</section>

<!-- TESTIMONIALS -->
<section style="background:#f5f0e8;">
  <div class="section-header">
    <div>
      <div class="section-title">What Our <span>Customers</span> Say</div>
      <div class="section-sub">Trusted by lakhs of happy Karnataka homeowners</div>
    </div>
  </div>
  <div class="testimonials-grid">
    <div class="test-card"><div class="test-stars">★★★★★</div><p class="test-text">"Found my dream 3BHK in Koramangala within a week! The filters are incredible and the agent was super responsive. Couldn't be happier."</p><div class="test-user"><div class="test-avatar">😊</div><div><div class="test-name">Aditya Gowda</div><div class="test-role">Bought in Bangalore</div></div></div></div>
    <div class="test-card"><div class="test-stars">★★★★★</div><p class="test-text">"As a first-time buyer in Mysuru, the home loan guidance was a lifesaver. The whole process from search to registration took just 6 weeks!"</p><div class="test-user"><div class="test-avatar">😍</div><div><div class="test-name">Sneha Kulkarni</div><div class="test-role">Bought in Mysuru</div></div></div></div>
    <div class="test-card"><div class="test-stars">★★★★☆</div><p class="test-text">"Listed my property in Mangaluru and had genuine inquiries within 24 hours. Sold above asking price thanks to the wide reach. Highly recommend."</p><div class="test-user"><div class="test-avatar">👍</div><div><div class="test-name">Ravi Shetty</div><div class="test-role">Sold in Mangaluru</div></div></div></div>
  </div>
</section>

<!-- CTA STRIP -->
<div class="cta-strip">
  <div><h3>Ready to Find Your Perfect Home in Karnataka?</h3><p>Join 5 lakh+ Karnataka residents who've found their dream property on NestFinder.</p></div>
  <button class="cta-strip-btn">Start Searching Now →</button>
</div>

<!-- FOOTER -->
<footer>
  <div class="footer-grid">
    <div class="footer-brand">
      <span class="nav-logo">Nest<span>Finder</span></span>
      <p>Karnataka's most trusted real estate platform. Buy, sell or rent properties across Bangalore, Mysuru, Mangaluru, Hubli & more.</p>
    </div>
    <div class="footer-col">
      <h5>Explore</h5>
      <ul>
        <li><a href="#" onclick="openPage('explore','sale')">Residential for Sale</a></li>
        <li><a href="#" onclick="openPage('explore','rent')">Residential for Rent</a></li>
        <li><a href="#" onclick="openPage('explore','commercial')">Commercial Spaces</a></li>
        <li><a href="#" onclick="openPage('explore','newprojects')">New Projects</a></li>
        <li><a href="#" onclick="openPage('explore','plots')">Plots & Land</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h5>Company</h5>
      <ul>
        <li><a href="#" onclick="openPage('company','about')">About Us</a></li>
        <li><a href="#" onclick="openPage('company','careers')">Careers</a></li>
        <li><a href="#" onclick="openPage('company','press')">Press</a></li>
        <li><a href="#" onclick="openPage('company','advertise')">Advertise</a></li>
        <li><a href="#" onclick="openPage('company','blog')">Blog</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h5>Support</h5>
      <ul>
        <li><a href="#" onclick="openPage('support','helpcenter')">Help Center</a></li>
        <li><a href="#" onclick="openPage('support','privacy')">Privacy Policy</a></li>
        <li><a href="#" onclick="openPage('support','terms')">Terms of Use</a></li>
        <li><a href="#" onclick="openPage('support','contact')">Contact Us</a></li>
        <li><a href="#" onclick="openPage('support','fraud')">Report Fraud</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <span>© 2026 NestFinder Pvt. Ltd. All rights reserved.</span>
    <span>Made with ❤️ in Karnataka</span>
  </div>
</footer>

<!-- MODAL OVERLAY -->
<div id="modal" style="display:none;position:fixed;inset:0;z-index:999;background:rgba(0,0,0,0.6);backdrop-filter:blur(4px);overflow-y:auto;" onclick="closeModal(event)">
  <div id="modalBox" style="background:#fff;border-radius:20px;max-width:620px;margin:60px auto;overflow:hidden;position:relative;" onclick="event.stopPropagation()">
    <div id="modalContent"></div>
  </div>
</div>

<!-- POST PROPERTY MODAL -->
<div id="postModal" style="display:none;position:fixed;inset:0;z-index:999;background:rgba(0,0,0,0.6);backdrop-filter:blur(4px);overflow-y:auto;" onclick="closePostModal(event)">
  <div style="background:#fff;border-radius:20px;max-width:500px;margin:80px auto;padding:40px;position:relative;" onclick="event.stopPropagation()">
    <button onclick="closePostModal()" style="position:absolute;top:16px;right:16px;background:none;border:none;font-size:22px;cursor:pointer;color:#888;">✕</button>
    <h2 style="font-family:'Playfair Display',serif;font-size:26px;margin-bottom:6px;color:#1a1a2e;">Post Your Property</h2>
    <p style="color:#8a8a9a;font-size:14px;margin-bottom:24px;">Reach millions of buyers & tenants for free</p>
    <div style="display:flex;flex-direction:column;gap:14px;">
      <input id="pp-name" type="text" placeholder="Property Name / Title" style="padding:12px 16px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
      <input id="pp-loc" type="text" placeholder="Locality, City (e.g. Koramangala, Bangalore)" style="padding:12px 16px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
      <div style="display:flex;gap:10px;">
        <select style="flex:1;padding:12px 16px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;">
          <option>Property Type</option><option>Apartment</option><option>Villa</option><option>Plot</option><option>Commercial</option>
        </select>
        <select style="flex:1;padding:12px 16px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;">
          <option>For Sale</option><option>For Rent</option>
        </select>
      </div>
      <input id="pp-price" type="text" placeholder="Price (e.g. ₹1.2 Cr)" style="padding:12px 16px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
      <input id="pp-phone" type="tel" placeholder="Your Phone Number" style="padding:12px 16px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
      <button onclick="submitPost()" style="background:#1a1a2e;color:#fff;border:none;padding:14px;border-radius:10px;font-size:15px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;transition:background 0.2s;" onmouseover="this.style.background='#c9963a'" onmouseout="this.style.background='#1a1a2e'">Submit Property →</button>
    </div>
  </div>
</div>

<!-- TOAST -->
<div id="toast" style="display:none;position:fixed;bottom:32px;left:50%;transform:translateX(-50%);background:#1a1a2e;color:#fff;padding:14px 24px;border-radius:16px;font-size:14px;font-weight:500;z-index:9999;box-shadow:0 8px 24px rgba(0,0,0,0.2);transition:opacity 0.3s;white-space:nowrap;max-width:90vw;text-align:center;"></div>

<style>
  .modal-hero { height:220px;display:flex;align-items:center;justify-content:center;font-size:80px;position:relative; }
  .modal-body { padding:28px 32px 32px; }
  .modal-price { font-family:'Playfair Display',serif;font-size:30px;font-weight:700;color:#1a1a2e; }
  .modal-name { font-size:18px;font-weight:600;margin:6px 0 4px; }
  .modal-loc { color:#8a8a9a;font-size:14px;display:flex;align-items:center;gap:4px; }
  .modal-specs { display:flex;gap:20px;padding:18px 0;border-top:1px solid rgba(0,0,0,0.07);border-bottom:1px solid rgba(0,0,0,0.07);margin:18px 0; }
  .modal-spec { text-align:center;flex:1; }
  .modal-spec strong { display:block;font-size:20px;font-weight:700;color:#1a1a2e; }
  .modal-spec span { font-size:11px;color:#8a8a9a;text-transform:uppercase;letter-spacing:0.08em; }
  .modal-section-title { font-size:13px;font-weight:600;color:#1a1a2e;letter-spacing:0.1em;text-transform:uppercase;margin-bottom:12px; }
  .modal-amenities { display:flex;flex-wrap:wrap;gap:8px;margin-bottom:20px; }
  .modal-amenity { background:#f5f0e8;color:#c9963a;padding:6px 14px;border-radius:20px;font-size:12px;font-weight:500; }
  .modal-agent { background:#f9f7f3;border-radius:14px;padding:16px;display:flex;align-items:center;gap:14px;margin-bottom:20px; }
  .modal-agent-avatar { width:48px;height:48px;border-radius:50%;background:linear-gradient(135deg,#c9963a,#e8b85a);display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0; }
  .modal-btns { display:flex;gap:10px; }
  .modal-btn-primary { flex:1;background:#1a1a2e;color:#fff;border:none;padding:14px;border-radius:10px;font-size:15px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;transition:background 0.2s; }
  .modal-btn-primary:hover { background:#c9963a; }
  .modal-btn-sec { flex:1;background:none;color:#1a1a2e;border:2px solid #1a1a2e;padding:14px;border-radius:10px;font-size:15px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;transition:all 0.2s; }
  .modal-btn-sec:hover { background:#1a1a2e;color:#fff; }
  .modal-close { position:absolute;top:14px;right:14px;background:rgba(255,255,255,0.9);border:none;width:34px;height:34px;border-radius:50%;font-size:16px;cursor:pointer;display:flex;align-items:center;justify-content:center;z-index:2; }
  .search-results { padding:24px 5%; }
  .search-results-grid { display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:20px;margin-top:16px; }
</style>

<script>
  const properties = [
    { id:1, name:"Prestige Lakeside Habitat", loc:"Whitefield, Bangalore", lat:12.9698, lng:77.7499,
      price:"₹1.2 Cr", beds:3, baths:2, area:"1,450 sq.ft", badge:"sale",
      img:"https://images.unsplash.com/photo-1545324418-cc1a3fa10c00?w=600&q=80",
      tags:["Gated Community","Swimming Pool","Gym","24/7 Security"],
      agent:"Suresh Kumar", agentPhone:"+91 98765 43210",
      desc:"A premium gated community in the heart of Whitefield, Bangalore. Surrounded by lush greenery with world-class amenities." },
    { id:2, name:"Brigade Orchards", loc:"Devanahalli, Bangalore", lat:13.2131, lng:77.7142,
      price:"₹2.8 Cr", beds:4, baths:3, area:"3,200 sq.ft", badge:"new",
      img:"https://images.unsplash.com/photo-1512917774080-9991f1c4c750?w=600&q=80",
      tags:["RERA Approved","Smart Home","Club House","EV Charging"],
      agent:"Kavitha Gowda", agentPhone:"+91 91234 56789",
      desc:"Brigade flagship township near Kempegowda Airport with panoramic views, smart home automation and resort-style living." },
    { id:3, name:"Gokulam Lake View Villa", loc:"Gokulam, Mysuru", lat:12.3178, lng:76.6340,
      price:"₹38,000/mo", beds:3, baths:2, area:"2,100 sq.ft", badge:"rent",
      img:"https://images.unsplash.com/photo-1600596542815-ffad4c1539a9?w=600&q=80",
      tags:["Lake Facing","Fully Furnished","Parking","Pet Friendly"],
      agent:"Kavitha Gowda", agentPhone:"+91 99887 76655",
      desc:"Stunning lake-facing villa in peaceful Gokulam, Mysuru. Fully furnished with modern interiors." },
    { id:4, name:"Sobha Silicon Oasis", loc:"Hosa Road, Bangalore", lat:12.8789, lng:77.6432,
      price:"₹72 L", beds:2, baths:2, area:"1,050 sq.ft", badge:"sale",
      img:"https://images.unsplash.com/photo-1580587771525-78b9dba3b914?w=600&q=80",
      tags:["Ready to Move","RERA","Vastu Compliant","Power Backup"],
      agent:"Suresh Kumar", agentPhone:"+91 90011 22334",
      desc:"Ready to move 2BHK in Sobha township near Electronic City. Vastu compliant with all modern conveniences." },
    { id:5, name:"Mangalore Pearl Heights", loc:"Bejai, Mangaluru", lat:12.8698, lng:74.8430,
      price:"₹95 L", beds:3, baths:2, area:"1,600 sq.ft", badge:"new",
      img:"https://images.unsplash.com/photo-1613490493576-7fde63acd811?w=600&q=80",
      tags:["New Launch","Sea Breeze","Green Building","Rooftop Garden"],
      agent:"Rajesh Shetty", agentPhone:"+91 91234 56789",
      desc:"Brand new sea-breeze apartments in Mangaluru with rooftop garden, sustainable architecture and panoramic views." },
    { id:6, name:"Hubli Central Park Residency", loc:"Vidyanagar, Hubli", lat:15.3647, lng:75.1240,
      price:"₹58 L", beds:3, baths:3, area:"1,850 sq.ft", badge:"sale",
      img:"https://images.unsplash.com/photo-1600585154340-be6161a56a0c?w=600&q=80",
      tags:["Gated","Club House","Park View","Power Backup"],
      agent:"Preethi Naidu", agentPhone:"+91 98765 43210",
      desc:"Spacious 3BHK in Hubli most sought-after residential zone with park views and top-class amenities." },
  ];

  let favorites = new Set();
  let currentTab = 'Buy';

  function renderProps(list) {
    const grid = document.getElementById('propsGrid');
    const arr = list || properties;
    grid.innerHTML = arr.map(p => `
      <div class="prop-card" onclick="viewProp(${p.id})">
        <div class="prop-img" style="background:#e0d8c8;overflow:hidden;">
          <img src="${p.img || 'https://images.unsplash.com/photo-1560518883-ce09059eeffa?w=600&q=80'}" alt="${p.name}" style="width:100%;height:100%;object-fit:cover;display:block;" onerror="this.style.display='none'"/>
          <span class="prop-badge badge-${p.isNew?'owner':p.badge}">${p.isNew?'✅ Your Listing':p.badge==='new'?'🔥 New':p.badge==='rent'?'For Rent':'For Sale'}</span>
          <button class="prop-fav" onclick="event.stopPropagation();toggleFav(this,${p.id})">${favorites.has(p.id)?'❤️':'🤍'}</button>
        </div>
        <div class="prop-body">
          <div class="prop-price">${p.price}</div>
          <div class="prop-name">${p.name}</div>
          <div class="prop-loc">📍 ${p.loc}</div>
          <div class="prop-divider"></div>
          <div class="prop-specs">
            <div class="prop-spec">🛏 <strong>${p.beds}</strong> Beds</div>
            <div class="prop-spec">🚿 <strong>${p.baths}</strong> Baths</div>
            <div class="prop-spec">📐 <strong>${p.area}</strong></div>
          </div>
          <div class="prop-tag-row">${p.tags.slice(0,3).map(t=>`<span class="prop-tag">${t}</span>`).join('')}</div>
        </div>
      </div>
    `).join('');
  }

  function toggleFav(btn, id) {
    if(favorites.has(id)) { favorites.delete(id); btn.textContent='🤍'; showToast('Removed from wishlist'); }
    else { favorites.add(id); btn.textContent='❤️'; showToast('❤️ Added to wishlist!'); }
  }

  function viewProp(id) {
    const p = properties.find(x=>x.id===id);
    document.getElementById('modalContent').innerHTML = `
      <div class="modal-hero" style="background:#1a1a2e;overflow:hidden;position:relative;">
        <img src="${p.img || 'https://images.unsplash.com/photo-1560518883-ce09059eeffa?w=800&q=80'}" alt="${p.name}" style="width:100%;height:100%;object-fit:cover;position:absolute;inset:0;"/>
        <button class="modal-close" onclick="document.getElementById('modal').style.display='none'">✕</button>
        <span class="prop-badge badge-${p.badge}" style="position:absolute;bottom:14px;left:14px;">${p.badge==='new'?'🔥 New':p.badge==='rent'?'For Rent':'For Sale'}</span>
      </div>
      <div class="modal-body">
        <div class="modal-price">${p.price}</div>
        <div class="modal-name">${p.name}</div>
        <div class="modal-loc">📍 ${p.loc}</div>
        <div class="modal-specs">
          <div class="modal-spec"><strong>${p.beds}</strong><span>Bedrooms</span></div>
          <div class="modal-spec"><strong>${p.baths}</strong><span>Bathrooms</span></div>
          <div class="modal-spec"><strong>${p.area}</strong><span>Area</span></div>
        </div>
        <p style="font-size:14px;color:#666;line-height:1.7;margin-bottom:20px;">${p.desc}</p>
        <div class="modal-section-title">Amenities</div>
        <div class="modal-amenities">${p.tags.map(t=>`<span class="modal-amenity">✓ ${t}</span>`).join('')}</div>
        <div class="modal-section-title">Listed By</div>
        <div class="modal-agent">
          <div class="modal-agent-avatar">👨‍💼</div>
          <div>
            <div style="font-weight:600;font-size:15px;">${p.agent}</div>
            <div style="font-size:13px;color:#8a8a9a;">Verified Agent · NestFinder Pro</div>
            <div style="font-size:13px;color:#c9963a;margin-top:2px;">⭐ 4.9 · 120+ deals closed</div>
          </div>
        </div>
        <div class="modal-btns">
          <button class="modal-btn-primary" onclick="contactAgent('${p.agent}','${p.agentPhone}')">📞 Contact Agent</button>
          <button class="modal-btn-sec" onclick="scheduleVisit('${p.name}')">🗓 Schedule Visit</button>
        </div>
        <button onclick="document.getElementById('modal').style.display='none';document.body.style.overflow='';openMapModal(properties.find(x=>x.id==${p.id}))" style="width:100%;margin-top:10px;background:#f0f7f0;color:#5a7a5e;border:1px solid #c0d8c0;padding:12px;border-radius:10px;font-size:14px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;">🗺️ View on Map</button>
        <button onclick="openPremiumModal(${p.id})" style="width:100%;margin-top:8px;background:linear-gradient(135deg,#c9963a,#e8b85a);color:#fff;border:none;padding:12px;border-radius:10px;font-size:14px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;">⭐ Boost this Listing (Premium)</button>
      </div>
    `;
    document.getElementById('modal').style.display='block';
    document.body.style.overflow='hidden';
  }

  function contactAgent(name, phone) {
    showToast(`📞 Connecting you to ${name} at ${phone}`);
    setTimeout(()=>{ document.getElementById('modal').style.display='none'; document.body.style.overflow=''; }, 800);
  }

  function scheduleVisit(name) {
    showToast(`🗓 Visit scheduled for "${name}"! Agent will confirm shortly.`);
    setTimeout(()=>{ document.getElementById('modal').style.display='none'; document.body.style.overflow=''; }, 800);
  }

  function closeModal(e) {
    document.getElementById('modal').style.display='none';
    document.body.style.overflow='';
  }

  function handleSearch() {
    const q = document.querySelector('.search-input input').value.toLowerCase().trim();
    const type = document.querySelectorAll('.search-select')[0].value;
    const budget = document.querySelectorAll('.search-select')[1].value;
    let results = properties;
    if(q) results = results.filter(p => p.name.toLowerCase().includes(q) || p.loc.toLowerCase().includes(q));
    if(type !== 'Property Type') results = results.filter(p => p.tags.some(t=>t.toLowerCase().includes(type.toLowerCase())) || p.name.toLowerCase().includes(type.toLowerCase()));

    // Scroll to properties section
    document.getElementById('propsGrid').scrollIntoView({behavior:'smooth', block:'start'});
    setTimeout(()=>{
      renderProps(results.length ? results : properties);
      showToast(results.length ? `🔍 Found ${results.length} properties${q?' in "'+q+'"':''}` : '🔍 Showing all properties');
    }, 400);
  }

  function setTab(el) {
    document.querySelectorAll('.s-tab').forEach(t=>t.classList.remove('active'));
    el.classList.add('active');
    currentTab = el.textContent;
    const filtered = currentTab === 'Rent'
      ? properties.filter(p=>p.badge==='rent')
      : currentTab === 'New Projects'
      ? properties.filter(p=>p.badge==='new')
      : properties.filter(p=>p.badge!=='rent');
    renderProps(filtered.length ? filtered : properties);
    showToast(`Showing ${el.textContent} listings`);
  }

  function openPostProperty() {
    document.getElementById('postModal').style.display='block';
    document.body.style.overflow='hidden';
  }
  function closePostModal(e) {
    if(!e || e.target===document.getElementById('postModal')) {
      document.getElementById('postModal').style.display='none';
      document.body.style.overflow='';
    }
  }
  function submitPost() {
    const name = document.getElementById('pp-name').value.trim();
    const loc  = document.getElementById('pp-loc').value.trim();
    const price= document.getElementById('pp-price').value.trim();
    const phone= document.getElementById('pp-phone').value.trim();
    const typeEl = document.querySelector('#postModal select:nth-of-type(1)');
    const saleEl = document.querySelector('#postModal select:nth-of-type(2)');
    if(!name || !phone) { showToast('⚠️ Please fill Property Name and Phone'); return; }

    const bgs = ["linear-gradient(135deg,#c8e8d8,#a8c8b8)","linear-gradient(135deg,#e8d8c8,#c8b8a8)","linear-gradient(135deg,#d8c8e8,#b8a8c8)"];
    const emojis = ["🏠","🏡","🏢","🏘️","🌳","🏬"];
    const isRent = saleEl.value === 'For Rent';
    const newProp = {
      id: Date.now(),
      name: name || 'My Property',
      loc: loc || 'India',
      price: price || 'Price on Request',
      beds: 2, baths: 2, area: 'N/A',
      badge: isRent ? 'rent' : 'new',
      emoji: emojis[Math.floor(Math.random()*emojis.length)],
      tags: [typeEl.value !== 'Property Type' ? typeEl.value : 'Residential', 'New Listing', 'Owner Posted'],
      agent: 'You (Owner)',
      agentPhone: phone,
      desc: `${name} is a newly listed property located in ${loc||'India'}. Posted directly by the owner. Contact for more details.`,
      bg: bgs[Math.floor(Math.random()*bgs.length)],
      isNew: true
    };

    properties.unshift(newProp);
    savePropertyToFirestore(newProp);

    // Clear form
    ['pp-name','pp-loc','pp-price','pp-phone'].forEach(id => document.getElementById(id).value='');
    closePostModal();
    renderProps();

    // Scroll to grid and highlight new card
    setTimeout(()=>{
      document.getElementById('propsGrid').scrollIntoView({behavior:'smooth', block:'start'});
      showToast('🎉 Your property is now live in the listings!');
    }, 300);
  }

  // Hook up all "Post Property" buttons
  document.addEventListener('DOMContentLoaded', ()=>{
    document.querySelectorAll('.nav-cta, .fb-btn, .cta-strip-btn').forEach(btn=>{
      btn.addEventListener('click', openPostProperty);
    });
    document.querySelectorAll('.agent-btn').forEach((btn,i)=>{
      const agents = ['Suresh Kumar +91 98765 43210','Kavitha Gowda +91 99887 76655','Rajesh Shetty +91 91234 56789','Preethi Naidu +91 90011 22334'];
      btn.addEventListener('click',()=>showToast(`📞 Connecting to ${agents[i]}`));
    });
    document.querySelectorAll('.cat-card').forEach(card=>{
      card.addEventListener('click',()=>{
        const label = card.querySelector('.cat-label').textContent;
        showToast(`🔍 Browsing ${label} listings...`);
        document.getElementById('propsGrid').scrollIntoView({behavior:'smooth'});
      });
    });
    document.querySelectorAll('.view-all').forEach(link=>{
      link.addEventListener('click',()=>showToast('📋 Loading all listings...'));
    });
    document.querySelectorAll('.nav-links a').forEach(a=>{
      a.addEventListener('click',e=>{
        e.preventDefault();
        // Highlight active nav link
        document.querySelectorAll('.nav-links a').forEach(x=>x.classList.remove('nav-active'));
        a.classList.add('nav-active');
        const label = a.textContent.trim();
        if(label === '🏠 Home') {
          // Scroll to very top, reset filters
          window.scrollTo({top:0, behavior:'smooth'});
          renderProps();
          document.querySelectorAll('.s-tab').forEach(t=>t.classList.remove('active'));
          document.querySelectorAll('.s-tab')[0].classList.add('active');
          showToast('🏠 Welcome back to NestFinder!');
        }
        else if(label === 'Buy') {
          // Filter properties to For Sale, scroll to grid
          document.querySelectorAll('.s-tab').forEach(t=>t.classList.remove('active'));
          document.querySelectorAll('.s-tab')[0].classList.add('active');
          renderProps(properties.filter(p=>p.badge!=='rent'));
          document.getElementById('propsGrid').scrollIntoView({behavior:'smooth'});
          showToast('🏠 Showing properties for sale');
        }
        else if(label === 'Rent') {
          // Filter to rentals
          document.querySelectorAll('.s-tab').forEach(t=>t.classList.remove('active'));
          document.querySelectorAll('.s-tab')[1].classList.add('active');
          renderProps(properties.filter(p=>p.badge==='rent'));
          document.getElementById('propsGrid').scrollIntoView({behavior:'smooth'});
          showToast('🏡 Showing properties for rent');
        }
        else if(label === 'Sell') {
          openPostProperty();
        }
        else if(label === 'New Projects') {
          // Filter to new badge
          document.querySelectorAll('.s-tab').forEach(t=>t.classList.remove('active'));
          document.querySelectorAll('.s-tab')[2].classList.add('active');
          renderProps(properties.filter(p=>p.badge==='new'));
          document.getElementById('propsGrid').scrollIntoView({behavior:'smooth'});
          showToast('🏗️ Showing new projects');
        }
        else if(label === 'Agents') {
          document.querySelector('section:has(#agentsGrid)') 
            ? document.getElementById('agentsGrid').scrollIntoView({behavior:'smooth'})
            : document.getElementById('agentsGrid').closest('section').scrollIntoView({behavior:'smooth'});
          showToast('👨‍💼 Showing top agents');
        }
      });
    });
    renderProps();
    initFirebase().then(() => loadPropertiesFromFirestore());
    setTimeout(initOverviewMap, 500);
  });

  function showToast(msg) {
    const t = document.getElementById('toast');
    t.textContent = msg;
    t.style.display='block';
    t.style.opacity='1';
    clearTimeout(window._toastTimer);
    window._toastTimer = setTimeout(()=>{ t.style.opacity='0'; setTimeout(()=>t.style.display='none',300); }, 2800);
  }

  // ── AGENT DATA ─────────────────────────────────
  let agents = [
    { id:1, name:"Suresh Kumar",  title:"Luxury Homes Specialist", city:"Bangalore",     gender:"👨‍💼", deals:142, rating:4.9, phone:"+91 98765 43210" },
    { id:2, name:"Kavitha Gowda", title:"Residential Expert",       city:"Mysuru",        gender:"👩‍💼", deals:98,  rating:4.8, phone:"+91 99887 76655" },
    { id:3, name:"Rajesh Shetty", title:"Commercial Leasing",       city:"Mangaluru",     gender:"👨‍💼", deals:215, rating:5.0, phone:"+91 91234 56789" },
    { id:4, name:"Preethi Naidu", title:"Plot & Land",              city:"Hubli-Dharwad", gender:"👩‍💼", deals:76,  rating:4.7, phone:"+91 90011 22334" },
  ];
  let isOwnerLoggedIn = false;
  const OWNER_CREDS = { user:'admin', pass:'owner123' };

  function renderAgents() {
    const grid = document.getElementById('agentsGrid');
    if(!grid) return;
    grid.innerHTML = agents.map(a => `
      <div class="agent-card" style="position:relative;">
        ${isOwnerLoggedIn ? `
          <div style="position:absolute;top:10px;right:10px;display:flex;gap:6px;">
            <button onclick="openEditAgent(${a.id})" style="width:28px;height:28px;border-radius:50%;background:#e8f0ff;border:1px solid #c8d4f0;cursor:pointer;font-size:13px;" title="Edit">✏️</button>
            <button onclick="deleteAgent(${a.id})" style="width:28px;height:28px;border-radius:50%;background:#fff0ee;border:1px solid #f0c8c0;cursor:pointer;font-size:13px;" title="Delete">🗑️</button>
          </div>` : ''}
        <div class="agent-avatar">${a.gender}</div>
        <div class="agent-name">${a.name}</div>
        <div class="agent-title">${a.title} · ${a.city}</div>
        <div class="agent-stats">
          <div class="ag-stat"><strong>${a.deals}</strong><span>Deals</span></div>
          <div class="ag-stat"><strong>${a.rating}⭐</strong><span>Rating</span></div>
        </div>
        <button class="agent-btn" onclick="showToast('📞 Connecting to ${a.name} at ${a.phone}')">Contact Agent</button>
      </div>
    `).join('');
  }

  function renderOwnerAgentList() {
    const list = document.getElementById('ownerAgentList');
    if(!list) return;
    if(agents.length === 0) { list.innerHTML = '<div style="text-align:center;padding:32px;color:#aaa;">No agents yet. Add one above!</div>'; return; }
    list.innerHTML = agents.map(a => `
      <div style="background:#fff;border:1px solid #e8e0d0;border-radius:12px;padding:16px 18px;margin-bottom:10px;display:flex;align-items:center;gap:14px;">
        <div style="width:44px;height:44px;border-radius:50%;background:linear-gradient(135deg,#c9963a,#e8b85a);display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0;">${a.gender}</div>
        <div style="flex:1;">
          <div style="font-weight:600;font-size:15px;color:#1a1a2e;">${a.name}</div>
          <div style="font-size:12px;color:#8a8a9a;">${a.title} · ${a.city}</div>
          <div style="font-size:12px;color:#c9963a;margin-top:2px;">${a.deals} deals · ⭐${a.rating} · ${a.phone}</div>
        </div>
        <div style="display:flex;gap:8px;">
          <button onclick="openEditAgent(${a.id})" style="padding:8px 14px;background:#f0f4ff;border:1px solid #c8d4f0;border-radius:8px;font-size:12px;font-weight:600;color:#3a5abd;cursor:pointer;font-family:'DM Sans',sans-serif;">✏️ Edit</button>
          <button onclick="deleteAgent(${a.id})" style="padding:8px 14px;background:#fff0ee;border:1px solid #f0c8c0;border-radius:8px;font-size:12px;font-weight:600;color:#c0533a;cursor:pointer;font-family:'DM Sans',sans-serif;">🗑️ Delete</button>
        </div>
      </div>
    `).join('');
  }

  function openOwnerPanel() {
    document.getElementById('ownerPanel').style.display = 'block';
    document.body.style.overflow = 'hidden';
    renderOwnerAgentList();
  }

  function closeOwnerLogin() {
    document.getElementById('ownerLoginModal').style.display = 'none';
    document.body.style.overflow = '';
    document.getElementById('ownerLoginErr').style.display = 'none';
  }

  function verifyOwner() {
    const u = document.getElementById('owner-user').value.trim();
    const p = document.getElementById('owner-pass').value.trim();
    const err = document.getElementById('ownerLoginErr');
    if(u === OWNER_CREDS.user && p === OWNER_CREDS.pass) {
      isOwnerLoggedIn = true;
      closeOwnerLogin();
      document.getElementById('ownerEditBtn').style.display = 'flex';
      document.getElementById('ownerPanel').style.display = 'block';
      document.body.style.overflow = 'hidden';
      renderAgents();
      renderOwnerAgentList();
      showToast('✅ Owner mode activated! You can now edit agents.');
    } else {
      err.textContent = '⚠️ Incorrect username or password.';
      err.style.display = 'block';
    }
  }

  function closeOwnerPanel() {
    document.getElementById('ownerPanel').style.display = 'none';
    document.body.style.overflow = '';
  }

  function addAgent() {
    const name   = document.getElementById('new-agent-name').value.trim();
    const title  = document.getElementById('new-agent-title').value.trim();
    const city   = document.getElementById('new-agent-city').value;
    const gender = document.getElementById('new-agent-gender').value;
    const deals  = parseInt(document.getElementById('new-agent-deals').value) || 0;
    const rating = parseFloat(document.getElementById('new-agent-rating').value) || 4.5;
    const phone  = document.getElementById('new-agent-phone').value.trim() || 'N/A';
    if(!name || !title || !city) { showToast('⚠️ Please fill Name, Specialization and City'); return; }
    agents.push({ id: Date.now(), name, title, city, gender, deals, rating: Math.min(5, rating), phone });
    ['new-agent-name','new-agent-title','new-agent-deals','new-agent-rating','new-agent-phone'].forEach(id => document.getElementById(id).value='');
    document.getElementById('new-agent-city').value = '';
    renderAgents();
    renderOwnerAgentList();
    showToast(`✅ ${name} added to Top Agents!`);
  }

  function openEditAgent(id) {
    const a = agents.find(x => x.id === id);
    if(!a) return;
    document.getElementById('edit-agent-id').value     = id;
    document.getElementById('edit-agent-name').value   = a.name;
    document.getElementById('edit-agent-title').value  = a.title + ' · ' + a.city;
    document.getElementById('edit-agent-deals').value  = a.deals;
    document.getElementById('edit-agent-rating').value = a.rating;
    document.getElementById('edit-agent-phone').value  = a.phone;
    document.getElementById('edit-agent-gender').value = a.gender;
    document.getElementById('agentEditModal').style.display = 'flex';
  }

  function closeEditModal() {
    document.getElementById('agentEditModal').style.display = 'none';
  }

  function saveAgentEdit() {
    const id  = parseInt(document.getElementById('edit-agent-id').value);
    const idx = agents.findIndex(x => x.id === id);
    if(idx === -1) return;
    const fullTitle = document.getElementById('edit-agent-title').value.trim();
    const parts = fullTitle.split('·');
    agents[idx].name   = document.getElementById('edit-agent-name').value.trim();
    agents[idx].title  = parts[0]?.trim() || fullTitle;
    agents[idx].city   = parts[1]?.trim() || agents[idx].city;
    agents[idx].deals  = parseInt(document.getElementById('edit-agent-deals').value) || 0;
    agents[idx].rating = parseFloat(document.getElementById('edit-agent-rating').value) || 4.5;
    agents[idx].phone  = document.getElementById('edit-agent-phone').value.trim();
    agents[idx].gender = document.getElementById('edit-agent-gender').value;
    closeEditModal();
    renderAgents();
    renderOwnerAgentList();
    showToast(`✅ ${agents[idx].name}'s details updated!`);
  }

  function deleteAgent(id) {
    const a = agents.find(x => x.id === id);
    if(!a) return;

    // Custom confirm toast instead of browser confirm()
    const t = document.getElementById('toast');
    t.innerHTML = `🗑️ Remove <strong>${a.name}</strong>? 
      <button onclick="confirmDeleteAgent(${id})" style="margin-left:10px;background:#c0533a;color:#fff;border:none;padding:4px 12px;border-radius:6px;cursor:pointer;font-family:'DM Sans',sans-serif;font-size:13px;font-weight:600;">Yes, Delete</button>
      <button onclick="document.getElementById('toast').style.opacity='0'" style="margin-left:6px;background:rgba(255,255,255,0.2);color:#fff;border:none;padding:4px 12px;border-radius:6px;cursor:pointer;font-family:'DM Sans',sans-serif;font-size:13px;">Cancel</button>`;
    t.style.display = 'block';
    t.style.opacity = '1';
    clearTimeout(window._toastTimer);
    window._toastTimer = setTimeout(()=>{ t.style.opacity='0'; setTimeout(()=>{ t.style.display='none'; t.innerHTML=''; }, 300); }, 6000);
  }

  function confirmDeleteAgent(id) {
    const a = agents.find(x => x.id === id);
    if(!a) return;
    agents = agents.filter(x => x.id !== id);
    renderAgents();
    renderOwnerAgentList();
    const t = document.getElementById('toast');
    t.innerHTML = `✅ ${a.name} removed successfully.`;
    t.style.display = 'block';
    t.style.opacity = '1';
    clearTimeout(window._toastTimer);
    window._toastTimer = setTimeout(()=>{ t.style.opacity='0'; setTimeout(()=>{ t.style.display='none'; t.innerHTML=''; }, 300); }, 2500);
  }

  renderAgents();

  // ── HERO HEADLINE CYCLER (Typewriter) ────────────
  const headlines = [
    'Find Your Dream Home in Your Dream City',
    'Find Your Perfect Apartment in Karnataka',
    'Discover a Comfortable Villa Just for You',
    'Explore Premium Plots Across Karnataka',
    'Rent Your Ideal Home in Bangalore',
    'Find a Cosy PG or Studio Today',
    'Your Dream Office Space Awaits You',
    'Move Into Your New Home This Season',
    'Search Verified Properties in Mysuru',
    'Buy or Rent in Mangaluru at the Best Price',
  ];
  const hlEl = document.getElementById('heroHeadline');
  let hlIndex = 0;
  let charIndex = 0;
  let typing = true;
  let pauseTimer = null;

  function getStyledChar(fullText, idx) {
    // Wrap em-worthy words in gold
    return fullText.slice(0, idx);
  }

  function applyStyle(text) {
    // Bold-gold the first "key" word group (between position 10–30ish)
    return text.replace(/(Dream Home|Perfect|Comfortable|Premium|Ideal|Cosy|Dream Office|New|Verified|Mangaluru)/g,
      '<em>$1</em>');
  }

  function typeWriter() {
    const fullText = headlines[hlIndex];
    if(typing) {
      charIndex++;
      hlEl.innerHTML = applyStyle(fullText.slice(0, charIndex));
      if(charIndex < fullText.length) {
        setTimeout(typeWriter, 45);
      } else {
        // Pause 3s then erase
        pauseTimer = setTimeout(() => { typing = false; eraseWriter(); }, 3000);
      }
    }
  }

  function eraseWriter() {
    const fullText = headlines[hlIndex];
    if(charIndex > 0) {
      charIndex--;
      hlEl.innerHTML = applyStyle(fullText.slice(0, charIndex));
      setTimeout(eraseWriter, 22);
    } else {
      hlIndex = (hlIndex + 1) % headlines.length;
      typing = true;
      setTimeout(typeWriter, 300);
    }
  }

  // Blinking cursor style
  const cursorStyle = document.createElement('style');
  cursorStyle.textContent = `
    #heroHeadline::after {
      content: '|';
      color: var(--gold-light);
      animation: blink 0.7s step-end infinite;
      margin-left: 2px;
      font-weight: 300;
    }
    @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }
  `;
  document.head.appendChild(cursorStyle);

  typeWriter();


  // ════════════════════════════════════════════════
  // 🗺️ MAPS (Leaflet - free, no API key needed)
  // ════════════════════════════════════════════════
  let mapModalInstance = null, overviewMapInstance = null, currentMapProp = null;

  function openMapModal(prop) {
    currentMapProp = prop;
    document.getElementById('mapModalTitle').textContent = prop.name;
    document.getElementById('mapModalLoc').textContent = '📍 ' + prop.loc;
    document.getElementById('mapModal').style.display = 'flex';
    document.body.style.overflow = 'hidden';
    setTimeout(() => {
      if(mapModalInstance) { mapModalInstance.remove(); }
      mapModalInstance = L.map('propertyMap').setView([prop.lat, prop.lng], 15);
      L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '© OpenStreetMap contributors'
      }).addTo(mapModalInstance);
      const icon = L.divIcon({ className:'', html: '<div style="background:#c9963a;color:#fff;padding:8px 12px;border-radius:10px;font-weight:700;font-size:13px;white-space:nowrap;box-shadow:0 4px 12px rgba(0,0,0,0.3);">🏠 ' + prop.price + '</div>', iconAnchor: [40, 20] });
      L.marker([prop.lat, prop.lng], {icon}).addTo(mapModalInstance).bindPopup('<b>' + prop.name + '</b><br/>' + prop.loc).openPopup();
    }, 200);
  }

  function closeMapModal(e) {
    if(!e || e.target === document.getElementById('mapModal')) {
      document.getElementById('mapModal').style.display = 'none';
      document.body.style.overflow = '';
    }
  }

  function openGoogleMaps() {
    if(currentMapProp) window.open('https://maps.google.com/?q=' + currentMapProp.lat + ',' + currentMapProp.lng, '_blank');
  }

  function initOverviewMap() {
    if(overviewMapInstance) return;
    overviewMapInstance = L.map('overviewMap').setView([13.1, 76.0], 7);
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: '© OpenStreetMap contributors'
    }).addTo(overviewMapInstance);
    properties.forEach(p => {
      if(!p.lat) return;
      const color = p.badge==='rent' ? '#5a7a5e' : p.badge==='new' ? '#c0533a' : '#c9963a';
      const icon = L.divIcon({ className:'', html: '<div style="background:' + color + ';color:#fff;padding:6px 10px;border-radius:8px;font-weight:700;font-size:11px;white-space:nowrap;box-shadow:0 3px 10px rgba(0,0,0,0.25);cursor:pointer;">' + p.price + '</div>', iconAnchor:[30,15] });
      L.marker([p.lat, p.lng], {icon}).addTo(overviewMapInstance)
        .bindPopup('<b>' + p.name + '</b><br/>📍 ' + p.loc + '<br/>' + p.beds + ' Beds · ' + p.area)
        .on('click', () => { overviewMapInstance.setView([p.lat, p.lng], 14); });
    });
  }

  // ════════════════════════════════════════════════
  // 💳 RAZORPAY PAYMENT
  // ════════════════════════════════════════════════
  let selectedPlanAmount = 0, selectedPlanName = '', selectedPropertyId = null;

  function openPremiumModal(propId) {
    selectedPropertyId = propId;
    document.getElementById('premiumModal').style.display = 'flex';
    document.body.style.overflow = 'hidden';
  }

  function closePremiumModal(e) {
    if(!e || e.target === document.getElementById('premiumModal')) {
      document.getElementById('premiumModal').style.display = 'none';
      document.body.style.overflow = '';
    }
  }

  function selectPlan(el, amount, name, price) {
    document.querySelectorAll('.plan-card').forEach(c => {
      c.style.borderColor = '#e0ddd6'; c.classList.remove('selected-plan');
    });
    el.style.borderColor = '#c9963a'; el.classList.add('selected-plan');
    selectedPlanAmount = amount; selectedPlanName = name;
    const info = document.getElementById('selectedPlanInfo');
    info.style.display = 'block';
    info.textContent = '✅ Selected: ' + name + ' — ' + price;
    const btn = document.getElementById('payNowBtn');
    btn.textContent = 'Pay ' + price + ' via Razorpay →';
    btn.style.opacity = '1'; btn.style.pointerEvents = 'auto';
  }

  function initiateRazorpay() {
    if(!selectedPlanAmount) return;
    // 🔧 Replace with your Razorpay Key ID from dashboard.razorpay.com
    const RAZORPAY_KEY = 'rzp_test_SP39PQG9LSSFnh';
    const options = {
      key: RAZORPAY_KEY,
      amount: selectedPlanAmount * 100, // paise
      currency: 'INR',
      name: 'NestFinder',
      description: selectedPlanName,
      image: 'https://i.imgur.com/your-logo.png',
      prefill: {
        name: currentUser?.name || '',
        email: currentUser?.email || '',
        contact: ''
      },
      theme: { color: '#c9963a' },
      handler: function(response) {
        closePremiumModal();
        // Mark property as boosted
        const prop = properties.find(p => p.id === selectedPropertyId);
        if(prop) prop.boosted = true;
        renderProps();
        showToast('🎉 Payment successful! Your listing is now boosted. ID: ' + response.razorpay_payment_id);
      },
      modal: { ondismiss: () => showToast('Payment cancelled. Your listing was not boosted.') }
    };
    if(RAZORPAY_KEY === 'rzp_test_SP39PQG9LSSFnh') {
      // Demo mode - simulate payment
      closePremiumModal();
      showToast('🎉 [Demo] Payment of ₹' + selectedPlanAmount + ' simulated! Add Razorpay key for real payments.');
      return;
    }
    const rzp = new Razorpay(options);
    rzp.open();
  }

  // ════════════════════════════════════════════════
  // 📱 MOBILE NAV
  // ════════════════════════════════════════════════
  function toggleMobileNav() {
    const d = document.getElementById('mobileNavDrawer');
    d.classList.toggle('open');
  }
  function closeMobileNav() {
    document.getElementById('mobileNavDrawer').classList.remove('open');
  }
  function filterNav(type) {
    if(type==='buy') { renderProps(properties.filter(p=>p.badge!=='rent')); document.getElementById('propsGrid').scrollIntoView({behavior:'smooth'}); }
    else if(type==='rent') { renderProps(properties.filter(p=>p.badge==='rent')); document.getElementById('propsGrid').scrollIntoView({behavior:'smooth'}); }
    else if(type==='new') { renderProps(properties.filter(p=>p.badge==='new')); document.getElementById('propsGrid').scrollIntoView({behavior:'smooth'}); }
  }

  // ════════════════════════════════════════════════
  // 🔥 FIREBASE FIRESTORE - Persist properties & agents
  // ════════════════════════════════════════════════
  async function savePropertyToFirestore(prop) {
    if(isDemoMode || !firebaseDb) return;
    try {
      const { collection, addDoc, serverTimestamp } = window.__firebaseModules;
      await addDoc(collection(firebaseDb, 'properties'), { ...prop, createdAt: serverTimestamp(), userId: currentUser?.uid || 'anonymous' });
    } catch(e) { console.warn('Firestore save failed:', e.message); }
  }

  async function loadPropertiesFromFirestore() {
    if(isDemoMode || !firebaseDb) return;
    try {
      const { collection, getDocs } = window.__firebaseModules;
      const snap = await getDocs(collection(firebaseDb, 'properties'));
      snap.forEach(doc => {
        const data = doc.data();
        if(!properties.find(p => p.id === doc.id)) {
          properties.unshift({ ...data, id: doc.id, isNew: true });
        }
      });
      renderProps();
    } catch(e) { console.warn('Firestore load failed:', e.message); }
  }

  async function saveAgentToFirestore(agent) {
    if(isDemoMode || !firebaseDb) return;
    try {
      const { collection, addDoc, serverTimestamp } = window.__firebaseModules;
      await addDoc(collection(firebaseDb, 'agents'), { ...agent, createdAt: serverTimestamp() });
    } catch(e) { console.warn('Agent save failed:', e.message); }
  }

  // ── AUTH LOGIC ───────────────────────────────────
  let currentMode = 'login';
  let selectedRole = 'buyer';
  let currentUser = null;

  // Fake user store (in-memory)
  const userStore = {};

  function switchAuth(mode) {
    currentMode = mode;
    const isLogin = mode === 'login';
    const isWebowner = selectedRole === 'webowner';
    document.getElementById('backBtnRow').style.display = isLogin ? 'none' : 'block';
    document.getElementById('tabLogin').style.borderBottom = isLogin ? '3px solid #c9963a' : '3px solid transparent';
    document.getElementById('tabLogin').style.color = isLogin ? '#1a1a2e' : '#8a8a9a';
    document.getElementById('tabSignup').style.borderBottom = !isLogin ? '3px solid #c9963a' : '3px solid transparent';
    document.getElementById('tabSignup').style.color = !isLogin ? '#1a1a2e' : '#8a8a9a';
    document.getElementById('authSubtitle').textContent = isLogin ? 'Welcome back! Login to continue' : 'Create your free account today';
    document.getElementById('authSubmitBtn').textContent = isLogin ? 'Login →' : 'Create Account →';
    document.getElementById('authToggleText').textContent = isLogin ? "Don't have an account?" : 'Already have an account?';
    document.getElementById('authToggleBtn').textContent = isLogin ? 'Sign Up' : 'Login';
    document.getElementById('nameField').style.display = (!isLogin && !isWebowner) ? 'block' : 'none';
    document.getElementById('cityField').style.display = (!isLogin && !isWebowner) ? 'block' : 'none';
    document.getElementById('agentLicField').style.display = (!isLogin && selectedRole==='agent') ? 'block' : 'none';
    document.getElementById('authError').style.display = 'none';
  }

  function selectRole(role) {
    selectedRole = role;
    ['buyer','seller','webowner','agent'].forEach(r => {
      const id = 'role' + r.charAt(0).toUpperCase() + r.slice(1);
      const btn = document.getElementById(id);
      if(!btn) return;
      const isActive = r === role;
      btn.style.border     = isActive ? '2px solid #c9963a' : '2px solid #e0ddd6';
      btn.style.background = isActive ? '#fff8f0' : '#fff';
      btn.style.color      = isActive ? '#c9963a' : '#8a8a9a';
    });
    // Show/hide webowner hint
    document.getElementById('webownerHint').style.display = role === 'webowner' ? 'block' : 'none';
    // Show/hide agent RERA field
    document.getElementById('agentLicField').style.display = (currentMode==='signup' && role==='agent') ? 'block' : 'none';
    // Hide signup fields for webowner (they use fixed credentials)
    const isWebowner = role === 'webowner';
    document.getElementById('nameField').style.display = (!isWebowner && currentMode==='signup') ? 'block' : 'none';
    document.getElementById('cityField').style.display = (!isWebowner && currentMode==='signup') ? 'block' : 'none';
  }

  
  // ════════════════════════════════════════════════
  // 🔐 FIREBASE AUTHENTICATION
  // ════════════════════════════════════════════════
  const firebaseConfig = {
    apiKey: "AIzaSyDyAI7kENBsXEU_ZPN9EprLn51afBb4Kb4",
    authDomain: "nestfinder-9d9ed.firebaseapp.com",
    projectId: "nestfinder-9d9ed",
    storageBucket: "nestfinder-9d9ed.firebasestorage.app",
    messagingSenderId: "108695422806",
    appId: "1:108695422806:web:e0f37e003b7c0703a2b8f7",
    measurementId: "G-MT65LM3X31"
  };

  // Demo mode fallback (works without Firebase setup)
  let firebaseApp = null, firebaseAuth = null, firebaseDb = null;
  let isDemoMode = false; // Set to false when Firebase config is added

  async function initFirebase() {
    try {
      if(FIREBASE_CONFIG.apiKey === 'YOUR_API_KEY') {
        console.log('ℹ️ Running in Demo Mode. Add Firebase config to enable real auth + database.');
        isDemoMode = true; return;
      }
      const { initializeApp, getAuth, getFirestore } = window.__firebaseModules;
      firebaseApp = initializeApp(FIREBASE_CONFIG);
      firebaseAuth = getAuth(firebaseApp);
      firebaseDb = getFirestore(firebaseApp);
      isDemoMode = false;
      console.log('✅ Firebase connected!');
      // Listen for auth state
      const { onAuthStateChanged } = window.__firebaseModules;
      onAuthStateChanged(firebaseAuth, (user) => {
        if(user && !currentUser) {
          // Auto restore session on page reload
          const savedRole = localStorage.getItem('nf_role') || 'buyer';
          const savedCity = localStorage.getItem('nf_city') || 'Karnataka';
          loginUser({ name: user.displayName || user.email.split('@')[0], email: user.email, role: savedRole, city: savedCity, uid: user.uid });
        }
      });
    } catch(e) {
      console.warn('Firebase init failed, running demo mode:', e.message);
      isDemoMode = true;
    }
  }

  async function handleAuth() {
    const email = document.getElementById('auth-email').value.trim();
    const pass  = document.getElementById('auth-pass').value.trim();
    document.getElementById('authError').style.display = 'none';

    if(!email || !pass) { showErr('Please enter your email and password.'); return; }
    if(pass.length < 6) { showErr('Password must be at least 6 characters.'); return; }

    // Website Owner - always works same way
    if(selectedRole === 'webowner') {
      if(email === 'admin@nestfinder.com' && pass === 'owner123') {
        loginUser({ name:'Website Owner', email, role:'webowner', city:'Karnataka' });
      } else { showErr('Invalid Website Owner credentials.'); }
      return;
    }

    if(!email.includes('@')) { showErr('Please enter a valid email address.'); return; }

    const btn = document.getElementById('authSubmitBtn');
    btn.textContent = '⏳ Please wait...'; btn.disabled = true;

    try {
      if(isDemoMode) {
        // ── DEMO MODE (no Firebase) ──
        if(currentMode === 'signup') {
          const name = document.getElementById('auth-name').value.trim();
          const city = document.getElementById('auth-city').value;
          if(!name) { showErr('Please enter your full name.'); return; }
          if(!city) { showErr('Please select your city.'); return; }
          userStore[email] = { name, email, pass, role: selectedRole, city };
          loginUser(userStore[email]);
        } else {
          if(!userStore[email]) { showErr('No account found. Please sign up first.'); return; }
          if(userStore[email].pass !== pass) { showErr('Incorrect password.'); return; }
          loginUser(userStore[email]);
        }
      } else {
        // ── FIREBASE MODE ──
        const { createUserWithEmailAndPassword, signInWithEmailAndPassword } = window.__firebaseModules;
        if(currentMode === 'signup') {
          const name = document.getElementById('auth-name').value.trim();
          const city = document.getElementById('auth-city').value;
          if(!name) { showErr('Please enter your full name.'); return; }
          if(!city) { showErr('Please select your city.'); return; }
          const cred = await createUserWithEmailAndPassword(firebaseAuth, email, pass);
          // Save extra info to Firestore
          const { doc, setDoc } = window.__firebaseModules;
          await setDoc(doc(firebaseDb, 'users', cred.user.uid), { name, email, role: selectedRole, city, createdAt: new Date().toISOString() });
          localStorage.setItem('nf_role', selectedRole);
          localStorage.setItem('nf_city', city);
          loginUser({ name, email, role: selectedRole, city, uid: cred.user.uid });
        } else {
          const cred = await signInWithEmailAndPassword(firebaseAuth, email, pass);
          const { doc, getDoc } = window.__firebaseModules;
          const snap = await getDoc(doc(firebaseDb, 'users', cred.user.uid));
          const data = snap.exists() ? snap.data() : { name: email.split('@')[0], role: selectedRole, city: 'Karnataka' };
          localStorage.setItem('nf_role', data.role);
          localStorage.setItem('nf_city', data.city);
          loginUser({ ...data, email, uid: cred.user.uid });
        }
      }
    } catch(e) {
      const msg = e.code === 'auth/user-not-found' ? 'No account found. Please sign up.'
        : e.code === 'auth/wrong-password' ? 'Incorrect password. Please try again.'
        : e.code === 'auth/email-already-in-use' ? 'Email already registered. Please login.'
        : e.code === 'auth/weak-password' ? 'Password must be at least 6 characters.'
        : e.message || 'Something went wrong. Please try again.';
      showErr(msg);
    } finally {
      btn.textContent = currentMode === 'login' ? 'Login →' : 'Create Account →';
      btn.disabled = false;
    }
  }

  async // logout() handled by Firebase auth block above

  function showErr(msg) {
    const e = document.getElementById('authError');
    e.textContent = '⚠️ ' + msg;
    e.style.display = 'block';
  }

  function loginUser(user) {
    currentUser = user;
    document.getElementById('authGate').style.display = 'none';
    document.body.style.overflow = '';
    document.getElementById('navPostBtn').style.display = 'none';
    const navUser = document.getElementById('navUser');
    navUser.style.display = 'flex';

    const roleEmoji = user.role==='webowner' ? '👑' : user.role==='agent' ? '👨‍💼' : user.role==='seller' ? '🏷️' : '🏠';
    document.getElementById('navUserAvatar').textContent = roleEmoji;
    document.getElementById('userMenuName').innerHTML = `
      <div>${user.name}</div>
      <div style="font-size:11px;color:#8a8a9a;font-weight:400;margin-top:2px;">
        ${user.role==='webowner' ? '👑 Website Owner' : user.role.charAt(0).toUpperCase()+user.role.slice(1)} · ${user.city||'Karnataka'}
      </div>`;

    // Only show Edit Agents button for Website Owner
    const editBtn = document.getElementById('ownerEditBtn');
    if(user.role === 'webowner') {
      isOwnerLoggedIn = true;
      editBtn.style.display = 'flex';
      editBtn.style.marginRight = '8px';
      renderAgents(); // re-render with edit/delete buttons visible
      showToast(`👑 Welcome, Website Owner! Edit Agents button is now active.`);
    } else {
      editBtn.style.display = 'none';
      showToast(`👋 Welcome, ${user.name.split(' ')[0]}! Logged in as ${user.role}.`);
    }
  }

  function socialLogin(provider) {
    const fakeUser = { name: provider==='Google' ? 'Google User' : 'Phone User', email: 'user@example.com', role: selectedRole, city: 'Bangalore' };
    userStore[fakeUser.email] = fakeUser;
    loginUser(fakeUser);
  }

  function toggleUserMenu() {
    const menu = document.getElementById('userMenu');
    menu.style.display = menu.style.display === 'none' ? 'block' : 'none';
  }

  function logout() {
    currentUser = null;
    document.getElementById('navUser').style.display = 'none';
    document.getElementById('navPostBtn').style.display = 'block';
    document.getElementById('userMenu').style.display = 'none';
    document.getElementById('ownerEditBtn').style.display = 'none';
    isOwnerLoggedIn = false;
    document.getElementById('authGate').style.display = 'flex';
    document.body.style.overflow = 'hidden';
    // Reset form
    ['auth-name','auth-email','auth-pass','auth-lic'].forEach(id => { const el=document.getElementById(id); if(el) el.value=''; });
    document.getElementById('authError').style.display='none';
    switchAuth('login');
  }

  function togglePassVis() {
    const p = document.getElementById('auth-pass');
    p.type = p.type === 'password' ? 'text' : 'password';
    document.getElementById('eyeBtn').textContent = p.type === 'password' ? '👁️' : '🙈';
  }

  // Block body scroll on auth gate
  document.body.style.overflow = 'hidden';
</script>
<!-- OWNER LOGIN MODAL -->
<div id="ownerLoginModal" style="display:none;position:fixed;inset:0;z-index:3000;background:rgba(0,0,0,0.7);backdrop-filter:blur(6px);align-items:center;justify-content:center;padding:20px;">
  <div style="background:#fff;border-radius:20px;width:100%;max-width:380px;padding:36px;box-shadow:0 32px 80px rgba(0,0,0,0.4);position:relative;">
    <button onclick="closeOwnerLogin()" style="position:absolute;top:14px;right:14px;background:none;border:none;font-size:20px;cursor:pointer;color:#aaa;">✕</button>
    <div style="text-align:center;margin-bottom:24px;">
      <div style="font-size:36px;margin-bottom:8px;">🔐</div>
      <div style="font-family:'Playfair Display',serif;font-size:22px;font-weight:700;color:#1a1a2e;">Owner Access</div>
      <div style="font-size:13px;color:#8a8a9a;margin-top:4px;">Enter owner credentials to edit agents</div>
    </div>
    <div style="display:flex;flex-direction:column;gap:12px;">
      <input id="owner-user" type="text" placeholder="Username" style="padding:13px 16px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
      <input id="owner-pass" type="password" placeholder="Password" style="padding:13px 16px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
      <div id="ownerLoginErr" style="display:none;color:#c0533a;font-size:13px;padding:8px 12px;background:#fff0ee;border-radius:8px;"></div>
      <button onclick="verifyOwner()" style="background:#1a1a2e;color:#fff;border:none;padding:14px;border-radius:10px;font-size:15px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;" onmouseover="this.style.background='#c9963a'" onmouseout="this.style.background='#1a1a2e'">Login as Owner →</button>
      <div style="text-align:center;font-size:12px;color:#bbb;">Default: username <strong>admin</strong> / password <strong>owner123</strong></div>
    </div>
  </div>
</div>

<!-- OWNER AGENT PANEL -->
<div id="ownerPanel" style="display:none;position:fixed;inset:0;z-index:3000;background:rgba(0,0,0,0.7);backdrop-filter:blur(6px);overflow-y:auto;">
  <div style="background:#fff;min-height:100vh;max-width:700px;margin:0 auto;padding:0 0 60px;" onclick="event.stopPropagation()">

    <!-- Panel Header -->
    <div style="background:#1a1a2e;padding:20px 28px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:10;">
      <div style="display:flex;align-items:center;gap:12px;">
        <span style="font-size:20px;">⚙️</span>
        <div>
          <div style="font-family:'Playfair Display',serif;font-size:18px;font-weight:700;color:#fff;">Manage Top Agents</div>
          <div style="font-size:12px;color:rgba(255,255,255,0.45);margin-top:2px;">Owner Control Panel</div>
        </div>
      </div>
      <button onclick="closeOwnerPanel()" style="background:rgba(255,255,255,0.1);border:none;color:#fff;width:36px;height:36px;border-radius:50%;font-size:18px;cursor:pointer;">✕</button>
    </div>

    <div style="padding:28px;">

      <!-- Add New Agent -->
      <div style="background:#f9f7f3;border-radius:16px;padding:22px;margin-bottom:28px;border:1px solid #e8e0d0;">
        <div style="font-size:13px;font-weight:700;color:#1a1a2e;letter-spacing:0.1em;text-transform:uppercase;margin-bottom:16px;">➕ Add New Agent</div>
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;">
          <input id="new-agent-name" type="text" placeholder="Full Name*" style="padding:11px 14px;border:1.5px solid #e0ddd6;border-radius:9px;font-size:13px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
          <input id="new-agent-title" type="text" placeholder="Specialization (e.g. Luxury Homes)*" style="padding:11px 14px;border:1.5px solid #e0ddd6;border-radius:9px;font-size:13px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
          <select id="new-agent-city" style="padding:11px 14px;border:1.5px solid #e0ddd6;border-radius:9px;font-size:13px;font-family:'DM Sans',sans-serif;outline:none;background:#fff;">
            <option value="">Select City*</option>
            <option>Bangalore</option><option>Mysuru</option><option>Mangaluru</option><option>Hubli-Dharwad</option><option>Belagavi</option><option>Davanagere</option><option>Shivamogga</option><option>Tumakuru</option>
          </select>
          <select id="new-agent-gender" style="padding:11px 14px;border:1.5px solid #e0ddd6;border-radius:9px;font-size:13px;font-family:'DM Sans',sans-serif;outline:none;background:#fff;">
            <option value="👨‍💼">👨‍💼 Male</option>
            <option value="👩‍💼">👩‍💼 Female</option>
          </select>
          <input id="new-agent-deals" type="number" placeholder="No. of Deals" min="0" style="padding:11px 14px;border:1.5px solid #e0ddd6;border-radius:9px;font-size:13px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
          <input id="new-agent-rating" type="number" placeholder="Rating (e.g. 4.8)" min="1" max="5" step="0.1" style="padding:11px 14px;border:1.5px solid #e0ddd6;border-radius:9px;font-size:13px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
          <input id="new-agent-phone" type="text" placeholder="Phone Number" style="padding:11px 14px;border:1.5px solid #e0ddd6;border-radius:9px;font-size:13px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
        </div>
        <button onclick="addAgent()" style="margin-top:14px;width:100%;background:#c9963a;color:#fff;border:none;padding:13px;border-radius:10px;font-size:14px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;" onmouseover="this.style.background='#1a1a2e'" onmouseout="this.style.background='#c9963a'">Add Agent to Listing</button>
      </div>

      <!-- Agent List -->
      <div style="font-size:13px;font-weight:700;color:#1a1a2e;letter-spacing:0.1em;text-transform:uppercase;margin-bottom:14px;">📋 Current Agents</div>
      <div id="ownerAgentList"></div>
    </div>
  </div>
</div>

<!-- AGENT EDIT MODAL -->
<div id="agentEditModal" style="display:none;position:fixed;inset:0;z-index:4000;background:rgba(0,0,0,0.6);backdrop-filter:blur(4px);display:none;align-items:center;justify-content:center;padding:20px;">
  <div style="background:#fff;border-radius:20px;width:100%;max-width:420px;padding:32px;position:relative;box-shadow:0 24px 60px rgba(0,0,0,0.3);">
    <button onclick="closeEditModal()" style="position:absolute;top:14px;right:14px;background:none;border:none;font-size:20px;cursor:pointer;color:#aaa;">✕</button>
    <div style="font-family:'Playfair Display',serif;font-size:20px;font-weight:700;color:#1a1a2e;margin-bottom:20px;">✏️ Edit Agent</div>
    <input type="hidden" id="edit-agent-id"/>
    <div style="display:flex;flex-direction:column;gap:11px;">
      <input id="edit-agent-name" type="text" placeholder="Full Name" style="padding:12px 14px;border:1.5px solid #e0ddd6;border-radius:9px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
      <input id="edit-agent-title" type="text" placeholder="Specialization · City" style="padding:12px 14px;border:1.5px solid #e0ddd6;border-radius:9px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
      <div style="display:flex;gap:10px;">
        <input id="edit-agent-deals" type="number" placeholder="Deals" style="flex:1;padding:12px 14px;border:1.5px solid #e0ddd6;border-radius:9px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
        <input id="edit-agent-rating" type="number" placeholder="Rating" step="0.1" min="1" max="5" style="flex:1;padding:12px 14px;border:1.5px solid #e0ddd6;border-radius:9px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
      </div>
      <input id="edit-agent-phone" type="text" placeholder="Phone Number" style="padding:12px 14px;border:1.5px solid #e0ddd6;border-radius:9px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
      <select id="edit-agent-gender" style="padding:12px 14px;border:1.5px solid #e0ddd6;border-radius:9px;font-size:14px;font-family:'DM Sans',sans-serif;outline:none;background:#fff;">
        <option value="👨‍💼">👨‍💼 Male</option>
        <option value="👩‍💼">👩‍💼 Female</option>
      </select>
    </div>
    <button onclick="saveAgentEdit()" style="margin-top:18px;width:100%;background:#1a1a2e;color:#fff;border:none;padding:14px;border-radius:10px;font-size:15px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;" onmouseover="this.style.background='#c9963a'" onmouseout="this.style.background='#1a1a2e'">Save Changes</button>
  </div>
</div>


<!-- MAP MODAL -->
<div id="mapModal" style="display:none;position:fixed;inset:0;z-index:3000;background:rgba(0,0,0,0.7);backdrop-filter:blur(6px);display:none;align-items:center;justify-content:center;padding:20px;" onclick="closeMapModal(event)">
  <div style="background:#fff;border-radius:20px;width:100%;max-width:760px;overflow:hidden;box-shadow:0 32px 80px rgba(0,0,0,0.4);" onclick="event.stopPropagation()">
    <div style="background:#1a1a2e;padding:18px 24px;display:flex;align-items:center;justify-content:space-between;">
      <div>
        <div id="mapModalTitle" style="font-family:'Playfair Display',serif;font-size:18px;font-weight:700;color:#fff;"></div>
        <div id="mapModalLoc" style="font-size:12px;color:rgba(255,255,255,0.5);margin-top:2px;"></div>
      </div>
      <button onclick="closeMapModal()" style="background:rgba(255,255,255,0.1);border:none;color:#fff;width:34px;height:34px;border-radius:50%;font-size:16px;cursor:pointer;">✕</button>
    </div>
    <div class="map-wrapper" id="propertyMap" style="height:380px;width:100%;"></div>
    <div style="padding:16px 24px;display:flex;gap:12px;border-top:1px solid #f0ece4;">
      <button onclick="openGoogleMaps()" style="flex:1;background:#1a1a2e;color:#fff;border:none;padding:12px;border-radius:10px;font-size:14px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;">🗺️ Open in Google Maps</button>
      <button onclick="closeMapModal()" style="flex:1;background:#f9f7f3;color:#1a1a2e;border:1px solid #e0ddd6;padding:12px;border-radius:10px;font-size:14px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;">Close</button>
    </div>
  </div>
</div>

<!-- PROPERTIES MAP OVERVIEW SECTION -->
<section style="padding:60px 5%;background:#fff;">
  <div class="section-header">
    <div>
      <div class="section-title">Explore on <span>Map</span></div>
      <div class="section-sub">View all Karnataka properties on an interactive map</div>
    </div>
  </div>
  <div id="overviewMap" style="height:420px;border-radius:16px;overflow:hidden;box-shadow:0 8px 32px rgba(0,0,0,0.12);"></div>
  <p style="text-align:center;color:#8a8a9a;font-size:13px;margin-top:14px;">📍 Click any pin to view property details</p>
</section>

<!-- FOOTER PAGE MODAL -->
<div id="pageModal" style="display:none;position:fixed;inset:0;z-index:3500;background:rgba(0,0,0,0.65);backdrop-filter:blur(6px);overflow-y:auto;padding:30px 16px;" onclick="closePageModal(event)">
  <div style="background:#faf7f2;border-radius:20px;max-width:680px;margin:0 auto;overflow:hidden;box-shadow:0 32px 80px rgba(0,0,0,0.35);" onclick="event.stopPropagation()">
    <div style="background:#1a1a2e;padding:20px 28px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:10;">
      <div id="pageModalTitle" style="font-family:'Playfair Display',serif;font-size:20px;font-weight:700;color:#fff;"></div>
      <button onclick="closePageModal()" style="background:rgba(255,255,255,0.12);border:none;color:#fff;width:36px;height:36px;border-radius:50%;font-size:18px;cursor:pointer;">✕</button>
    </div>
    <div id="pageModalBody" style="padding:32px;"></div>
  </div>
</div>

<script>
// ── FOOTER PAGE CONTENT ──────────────────────────
const pages = {

  // ── EXPLORE ──────────────────────────────────────
  'explore-sale': {
    title: '🏠 Residential for Sale',
    html: `
      <p style="color:#666;line-height:1.8;margin-bottom:22px;">Browse thousands of verified homes for sale across Karnataka — apartments, villas, independent houses and more.</p>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:22px;">
        ${[['Bangalore','42,500+ listings'],['Mysuru','8,200+ listings'],['Mangaluru','6,100+ listings'],['Hubli-Dharwad','4,800+ listings'],['Belagavi','3,300+ listings'],['Shivamogga','2,100+ listings']].map(([c,n])=>`
        <div onclick="closePageModal();showToast('🔍 Showing properties for sale in ${c}')" style="background:#fff;border:1px solid #e8e0d0;border-radius:12px;padding:15px 18px;cursor:pointer;display:flex;justify-content:space-between;align-items:center;" onmouseover="this.style.borderColor='#c9963a'" onmouseout="this.style.borderColor='#e8e0d0'">
          <div style="font-weight:600;color:#1a1a2e;">📍 ${c}</div>
          <div style="font-size:12px;color:#c9963a;font-weight:500;">${n}</div>
        </div>`).join('')}
      </div>
      <div style="background:#fff8f0;border:1px solid #f0dcc0;border-radius:12px;padding:16px;margin-bottom:20px;">
        <div style="font-weight:600;color:#1a1a2e;margin-bottom:8px;">💡 Buyer Tips</div>
        <ul style="color:#666;font-size:13px;line-height:2;padding-left:18px;">
          <li>Always verify RERA registration before booking</li>
          <li>Check for clear title deeds and encumbrance certificate</li>
          <li>Compare at least 3 properties before deciding</li>
          <li>Get a home loan pre-approval to speed up the process</li>
        </ul>
      </div>
      <button onclick="closePageModal();document.getElementById('propsGrid').scrollIntoView({behavior:'smooth'})" style="width:100%;background:#1a1a2e;color:#fff;border:none;padding:14px;border-radius:12px;font-size:15px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;">View All Properties for Sale →</button>`
  },

  'explore-rent': {
    title: '🏡 Residential for Rent',
    html: `
      <p style="color:#666;line-height:1.8;margin-bottom:22px;">Find verified rental homes in Karnataka — zero brokerage options, furnished & unfurnished, directly from owners.</p>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:22px;">
        ${[['Bangalore','28,000+ rentals'],['Mysuru','5,400+ rentals'],['Mangaluru','4,100+ rentals'],['Hubli-Dharwad','2,900+ rentals'],['Tumakuru','1,600+ rentals'],['Davanagere','1,200+ rentals']].map(([c,n])=>`
        <div onclick="closePageModal();showToast('🔍 Showing rentals in ${c}')" style="background:#fff;border:1px solid #e8e0d0;border-radius:12px;padding:15px 18px;cursor:pointer;display:flex;justify-content:space-between;align-items:center;" onmouseover="this.style.borderColor='#5a7a5e'" onmouseout="this.style.borderColor='#e8e0d0'">
          <div style="font-weight:600;color:#1a1a2e;">📍 ${c}</div>
          <div style="font-size:12px;color:#5a7a5e;font-weight:500;">${n}</div>
        </div>`).join('')}
      </div>
      <div style="background:#f0f7f0;border:1px solid #c0d8c0;border-radius:12px;padding:16px;margin-bottom:20px;">
        <div style="font-weight:600;color:#1a1a2e;margin-bottom:8px;">💡 Renter Tips</div>
        <ul style="color:#666;font-size:13px;line-height:2;padding-left:18px;">
          <li>Always sign a registered rental agreement</li>
          <li>Verify owner's identity and property documents</li>
          <li>Inspect for water supply, electricity & internet</li>
          <li>Clarify maintenance charges upfront</li>
        </ul>
      </div>
      <button onclick="closePageModal();showToast('🔍 Loading all rental listings...')" style="width:100%;background:#5a7a5e;color:#fff;border:none;padding:14px;border-radius:12px;font-size:15px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;">View All Rental Listings →</button>`
  },

  'explore-commercial': {
    title: '🏬 Commercial Spaces',
    html: `
      <p style="color:#666;line-height:1.8;margin-bottom:22px;">Find offices, shops, warehouses and more across Karnataka. Best locations for your business growth.</p>
      <div style="display:flex;flex-direction:column;gap:12px;margin-bottom:22px;">
        ${[['🏢','Office Space','IT parks, co-working spaces, corporate offices','12,400+ listings'],['🛒','Retail / Shop','High street stores, mall kiosks, showrooms','8,900+ listings'],['🏭','Warehouse & Industrial','Storage hubs, logistics centres, factories','3,200+ listings'],['🍽️','Restaurant & Food Court','Cloud kitchens, cafes, QSR spaces','2,100+ listings'],['🏨','Hotel & Hospitality','Guest houses, boutique hotels, resorts','1,400+ listings']].map(([e,t,d,n])=>`
        <div onclick="closePageModal();showToast('🔍 Browsing ${t} listings')" style="background:#fff;border:1px solid #e8e0d0;border-radius:12px;padding:16px 18px;display:flex;gap:14px;align-items:center;cursor:pointer;" onmouseover="this.style.borderColor='#c9963a'" onmouseout="this.style.borderColor='#e8e0d0'">
          <span style="font-size:30px;flex-shrink:0;">${e}</span>
          <div style="flex:1"><div style="font-weight:600;color:#1a1a2e;">${t}</div><div style="font-size:12px;color:#8a8a9a;margin-top:2px;">${d}</div></div>
          <div style="font-size:12px;color:#c9963a;font-weight:600;white-space:nowrap;">${n}</div>
        </div>`).join('')}
      </div>`
  },

  'explore-newprojects': {
    title: '🏗️ New Projects',
    html: `
      <p style="color:#666;line-height:1.8;margin-bottom:22px;">Explore freshly launched and under-construction projects from Karnataka's top developers. RERA approved with best launch prices.</p>
      <div style="display:flex;flex-direction:column;gap:12px;margin-bottom:22px;">
        ${[['Prestige Group','12 active projects · Bangalore, Mysuru','Since 1986 · AAA rated'],['Brigade Group','8 active projects · Bangalore, Mangaluru','Since 1986 · ISO certified'],['Sobha Developers','6 active projects · Bangalore','Since 1995 · Award winning'],['Puravankara','5 active projects · Bangalore','Since 1975 · Listed on NSE/BSE'],['Godrej Properties','4 active projects · Bangalore','Since 1990 · Pan India developer']].map(([d,l,t])=>`
        <div onclick="closePageModal();showToast('🏗️ Opening ${d} projects')" style="background:#fff;border:1px solid #e8e0d0;border-radius:12px;padding:16px 18px;cursor:pointer;" onmouseover="this.style.borderColor='#c9963a'" onmouseout="this.style.borderColor='#e8e0d0'">
          <div style="display:flex;justify-content:space-between;align-items:flex-start;">
            <div><div style="font-weight:700;color:#1a1a2e;font-size:15px;">${d}</div><div style="font-size:12px;color:#8a8a9a;margin-top:3px;">📍 ${l}</div></div>
            <span style="background:#f5f0e8;color:#c9963a;font-size:11px;padding:4px 10px;border-radius:20px;font-weight:600;white-space:nowrap;">Verified</span>
          </div>
          <div style="font-size:11px;color:#aaa;margin-top:6px;">🏆 ${t}</div>
        </div>`).join('')}
      </div>
      <div style="background:#fff8f0;border:1px solid #f0dcc0;border-radius:12px;padding:14px;">
        <div style="font-size:13px;color:#c9963a;font-weight:600;">⚠️ Always check RERA registration number before booking any new project.</div>
      </div>`
  },

  'explore-plots': {
    title: '🌳 Plots & Land',
    html: `
      <p style="color:#666;line-height:1.8;margin-bottom:22px;">Buy verified residential, agricultural or commercial plots across Karnataka. Clear titles, legal checks included.</p>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:22px;">
        ${[['🏘️','Residential Plot','Build your own home'],['🌾','Agricultural Land','Farming & investment'],['📋','NA / Non-Agri Plot','Approved for construction'],['🏭','Industrial Plot','Factory or warehouse use'],['🏖️','Farm House Plot','Weekend retreat land'],['🏕️','Gated Layout Plot','Community living']].map(([e,t,d])=>`
        <div onclick="closePageModal();showToast('🌳 Browsing ${t} listings')" style="background:#fff;border:1px solid #e8e0d0;border-radius:12px;padding:16px;cursor:pointer;text-align:center;" onmouseover="this.style.borderColor='#c9963a'" onmouseout="this.style.borderColor='#e8e0d0'">
          <div style="font-size:26px;margin-bottom:6px;">${e}</div>
          <div style="font-weight:600;color:#1a1a2e;font-size:13px;">${t}</div>
          <div style="font-size:11px;color:#8a8a9a;margin-top:3px;">${d}</div>
        </div>`).join('')}
      </div>
      <div style="background:#f0f7f0;border:1px solid #c0d8c0;border-radius:12px;padding:14px;">
        <div style="font-weight:600;color:#1a1a2e;margin-bottom:6px;">💡 Plot Buying Checklist</div>
        <ul style="color:#666;font-size:12px;line-height:2;padding-left:16px;margin:0;">
          <li>Verify khata, mutation & encumbrance certificate</li>
          <li>Check DC conversion for non-agricultural use</li>
          <li>Confirm BDA / BMRDA / RERA approval</li>
        </ul>
      </div>`
  },

  // ── COMPANY ──────────────────────────────────────
  'company-about': {
    title: '🏢 About NestFinder',
    html: `
      <div style="text-align:center;padding:10px 0 28px;">
        <div style="font-family:'Playfair Display',serif;font-size:36px;font-weight:900;color:#1a1a2e;">Nest<span style="color:#c9963a;">Finder</span></div>
        <div style="color:#8a8a9a;font-size:13px;margin-top:6px;letter-spacing:0.05em;text-transform:uppercase;">Karnataka's Most Trusted Real Estate Platform</div>
      </div>
      <p style="color:#555;font-size:15px;line-height:1.9;margin-bottom:16px;">NestFinder was founded in <strong>2020</strong> in Bangalore with one mission — to make finding a home in Karnataka simple, transparent, and stress-free. We connect buyers, sellers, renters, and agents on one powerful platform built for the people of Karnataka.</p>
      <p style="color:#555;font-size:15px;line-height:1.9;margin-bottom:24px;">From IT corridor apartments in Whitefield to heritage homes in Mysuru's Gokulam, coastal villas in Mangaluru to farmland in the Western Ghats — NestFinder covers every corner of Karnataka with verified listings, expert agents, and zero hidden fees.</p>
      <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-bottom:24px;">
        ${[['1.2L+','Verified Listings'],['8,000+','Expert Agents'],['5L+','Happy Users'],['30+','Cities Covered'],['₹0','Listing Fee'],['98%','Verified Profiles']].map(([v,l])=>`
        <div style="background:#fff;border:1px solid #e8e0d0;border-radius:12px;padding:16px;text-align:center;">
          <div style="font-family:'Playfair Display',serif;font-size:22px;font-weight:700;color:#c9963a;">${v}</div>
          <div style="font-size:11px;color:#8a8a9a;margin-top:4px;">${l}</div>
        </div>`).join('')}
      </div>
      <div style="background:#1a1a2e;border-radius:14px;padding:20px 24px;color:#fff;">
        <div style="font-weight:600;font-size:15px;margin-bottom:8px;">🎯 Our Vision</div>
        <p style="color:rgba(255,255,255,0.65);font-size:13px;line-height:1.8;margin:0;">To be the most trusted, transparent and technology-driven real estate platform in South India — empowering every Kannadiga to own their dream property with confidence.</p>
      </div>`
  },

  'company-careers': {
    title: '💼 Careers at NestFinder',
    html: `
      <p style="color:#666;line-height:1.8;margin-bottom:6px;">Join our fast-growing team and help build Karnataka's #1 property platform. We offer competitive salaries, flexible work, and a great culture.</p>
      <div style="background:#fff8f0;border:1px solid #f0dcc0;border-radius:10px;padding:12px 16px;margin-bottom:20px;font-size:13px;color:#c9963a;font-weight:500;">🚀 We're hiring! 8 open positions across Engineering, Sales & Marketing.</div>
      <div style="display:flex;flex-direction:column;gap:11px;margin-bottom:22px;">
        ${[['Senior Frontend Developer','Bangalore · Full-time · ₹18–28 LPA','Engineering','🟢 Open'],['Product Manager','Bangalore · Full-time · ₹20–32 LPA','Product','🟢 Open'],['Sales Executive – Bangalore','Bangalore · Full-time · ₹6–10 LPA + incentives','Sales','🟢 Open'],['Sales Executive – Mysuru','Mysuru · Full-time · ₹5–8 LPA + incentives','Sales','🟢 Open'],['Digital Marketing Manager','Remote · Full-time · ₹12–18 LPA','Marketing','🟢 Open'],['Content Writer – Real Estate','Remote · Part-time · ₹3–5 LPA','Content','🟢 Open']].map(([r,l,d,s])=>`
        <div style="background:#fff;border:1px solid #e8e0d0;border-radius:12px;padding:15px 18px;cursor:pointer;" onmouseover="this.style.borderColor='#c9963a'" onmouseout="this.style.borderColor='#e8e0d0'" onclick="showToast('📧 Application link sent for: ${r}')">
          <div style="display:flex;justify-content:space-between;align-items:flex-start;gap:8px;">
            <div><div style="font-weight:600;color:#1a1a2e;font-size:14px;">${r}</div><div style="font-size:12px;color:#8a8a9a;margin-top:3px;">${l}</div></div>
            <div style="text-align:right;flex-shrink:0;"><span style="background:#f5f0e8;color:#c9963a;font-size:11px;padding:3px 9px;border-radius:20px;">${d}</span><div style="font-size:11px;color:#4a9a5a;margin-top:4px;">${s}</div></div>
          </div>
        </div>`).join('')}
      </div>
      <div style="display:flex;gap:10px;">
        <button onclick="showToast('📧 Send resume to careers@nestfinder.com')" style="flex:1;background:#1a1a2e;color:#fff;border:none;padding:13px;border-radius:12px;font-size:14px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;">Send Resume →</button>
        <button onclick="showToast('📞 HR: +91 80 4567 8900')" style="flex:1;background:#fff;color:#1a1a2e;border:2px solid #1a1a2e;padding:13px;border-radius:12px;font-size:14px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;">Call HR</button>
      </div>`
  },

  'company-press': {
    title: '📰 Press & Media',
    html: `
      <p style="color:#666;line-height:1.8;margin-bottom:6px;">NestFinder in the news. For media inquiries, interviews or press kits contact <strong style="color:#1a1a2e;">press@nestfinder.com</strong></p>
      <div style="background:#f9f7f3;border-radius:10px;padding:12px 16px;margin-bottom:20px;display:flex;gap:20px;font-size:13px;">
        <div><strong style="color:#1a1a2e;">Press Contact:</strong><br/><span style="color:#8a8a9a;">Anjali Rao, PR Head</span></div>
        <div><strong style="color:#1a1a2e;">Email:</strong><br/><span style="color:#c9963a;">press@nestfinder.com</span></div>
        <div><strong style="color:#1a1a2e;">Phone:</strong><br/><span style="color:#8a8a9a;">+91 80 4567 8910</span></div>
      </div>
      <div style="display:flex;flex-direction:column;gap:12px;margin-bottom:22px;">
        ${[['NestFinder crosses 5 lakh users across Karnataka','The Hindu · March 2026','🏆 Milestone'],['NestFinder named Best PropTech Startup 2025','Economic Times · November 2025','🏅 Award'],['How NestFinder is changing real estate in Tier-2 KA cities','Deccan Herald · August 2025','📖 Feature'],['NestFinder raises ₹50 Cr in Series A funding','Business Standard · April 2025','💰 Funding'],['Karnataka CM inaugurates NestFinder HQ in Bangalore','Times of India · January 2025','🎉 Event']].map(([h,s,b])=>`
        <div style="background:#fff;border:1px solid #e8e0d0;border-radius:12px;padding:16px 18px;cursor:pointer;" onmouseover="this.style.borderColor='#c9963a'" onmouseout="this.style.borderColor='#e8e0d0'">
          <div style="display:flex;justify-content:space-between;align-items:flex-start;gap:8px;">
            <div style="font-weight:600;color:#1a1a2e;font-size:14px;line-height:1.5;">${h}</div>
            <span style="background:#f5f0e8;color:#c9963a;font-size:11px;padding:3px 10px;border-radius:20px;white-space:nowrap;">${b}</span>
          </div>
          <div style="font-size:12px;color:#8a8a9a;margin-top:5px;">🗞️ ${s}</div>
        </div>`).join('')}
      </div>`
  },

  'company-advertise': {
    title: '📣 Advertise with NestFinder',
    html: `
      <p style="color:#666;line-height:1.8;margin-bottom:22px;">Reach <strong>5 lakh+</strong> active property seekers every month across Karnataka. Promote your project, brand, or services with us.</p>
      <div style="display:flex;flex-direction:column;gap:14px;margin-bottom:24px;">
        ${[['🥉','Basic Plan','₹5,000 / month',['Banner ads on listing pages','10,000+ monthly impressions','Basic analytics dashboard'],'#8a8a9a'],['🥈','Standard Plan','₹15,000 / month',['Featured property listings','50,000+ monthly impressions','City-level targeting','Lead tracking'],'#c9963a'],['🥇','Premium Plan','₹35,000 / month',['Homepage hero banner','1,50,000+ monthly impressions','All-city targeting','Priority customer support','Dedicated account manager'],'#f5c518']].map(([b,t,p,f,c])=>`
        <div style="background:#fff;border:2px solid #e8e0d0;border-radius:14px;padding:20px 22px;" onmouseover="this.style.borderColor='${c}'" onmouseout="this.style.borderColor='#e8e0d0'">
          <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:14px;">
            <div style="font-size:20px;">${b} <span style="font-family:'Playfair Display',serif;font-size:17px;font-weight:700;color:#1a1a2e;margin-left:6px;">${t}</span></div>
            <div style="font-size:20px;font-weight:700;color:${c};font-family:'Playfair Display',serif;">${p}</div>
          </div>
          <ul style="color:#666;font-size:13px;line-height:2;padding-left:18px;margin:0 0 14px;">
            ${f.map(i=>`<li>${i}</li>`).join('')}
          </ul>
          <button onclick="showToast('📧 Sales team will contact you within 24 hrs!')" style="width:100%;background:#1a1a2e;color:#fff;border:none;padding:11px;border-radius:10px;font-size:13px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;">Get Started →</button>
        </div>`).join('')}
      </div>
      <div style="text-align:center;font-size:13px;color:#8a8a9a;">For custom packages: <strong style="color:#c9963a;">ads@nestfinder.com</strong> · +91 80 4567 8920</div>`
  },

  'company-blog': {
    title: '📝 NestFinder Blog',
    html: `
      <p style="color:#666;line-height:1.8;margin-bottom:20px;">Tips, guides & insights on real estate in Karnataka — for buyers, sellers, renters and investors.</p>
      <div style="display:flex;flex-direction:column;gap:14px;margin-bottom:20px;">
        ${[['Top 10 Upcoming Localities to Invest in Bangalore in 2026','Investment · 8 min read','🔥 Trending'],['Complete Guide to Buying Your First Home in Karnataka','Buying Guide · 12 min read','📖 Popular'],['Rental Agreement in Karnataka: What You Must Know','Legal · 6 min read','⚖️ Legal'],['RERA Karnataka: How to Check if Your Project is Registered','RERA · 5 min read','✅ Must Read'],['Home Loan vs Renting in Bangalore — What Makes More Sense?','Finance · 7 min read','💰 Finance'],['Best Localities for IT Professionals in Bangalore 2026','Lifestyle · 9 min read','🏙️ Lifestyle']].map(([t,m,b])=>`
        <div onclick="showToast('📖 Opening article: ${t.substring(0,30)}...')" style="background:#fff;border:1px solid #e8e0d0;border-radius:12px;padding:16px 18px;cursor:pointer;display:flex;justify-content:space-between;align-items:flex-start;gap:10px;" onmouseover="this.style.borderColor='#c9963a'" onmouseout="this.style.borderColor='#e8e0d0'">
          <div><div style="font-weight:600;color:#1a1a2e;font-size:14px;line-height:1.5;margin-bottom:4px;">${t}</div><div style="font-size:11px;color:#8a8a9a;">${m}</div></div>
          <span style="background:#f5f0e8;color:#c9963a;font-size:10px;padding:3px 9px;border-radius:20px;white-space:nowrap;flex-shrink:0;">${b}</span>
        </div>`).join('')}
      </div>
      <button onclick="showToast('📝 Loading all blog articles...')" style="width:100%;background:#c9963a;color:#fff;border:none;padding:13px;border-radius:12px;font-size:14px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;">View All Articles →</button>`
  },

  // ── SUPPORT ──────────────────────────────────────
  'support-helpcenter': {
    title: '❓ Help Center',
    html: `
      <p style="color:#666;line-height:1.8;margin-bottom:20px;">Find answers to the most common questions about using NestFinder.</p>
      <div style="display:flex;flex-direction:column;gap:10px;margin-bottom:22px;">
        ${[['How do I post a property for free?','Click "Post Property Free" in the top navigation. Fill in property details, add photos and submit. It goes live within 2 hours after verification.'],['How do I contact a property owner?','Click on any property card, then click "Contact Agent" or "Schedule Visit" to get connected directly.'],['Is NestFinder free for buyers?','Yes! Browsing, searching, shortlisting and contacting sellers is completely free for buyers and renters.'],['How do I verify if a property is genuine?','Look for the ✅ Verified badge on listings. You can also request document verification from the agent.'],['How do I report a fake listing?','Scroll to the footer and click "Report Fraud", or email fraud@nestfinder.com with listing details.'],['Can I list my property if I am an agent?','Yes. Agents can sign up with their RERA license number and post multiple listings.']].map(([q,a])=>`
        <details style="background:#fff;border:1px solid #e8e0d0;border-radius:12px;overflow:hidden;">
          <summary style="padding:15px 18px;font-weight:600;color:#1a1a2e;font-size:14px;cursor:pointer;list-style:none;display:flex;justify-content:space-between;align-items:center;">${q} <span style="color:#c9963a;font-size:18px;">+</span></summary>
          <div style="padding:0 18px 16px;color:#666;font-size:13px;line-height:1.8;border-top:1px solid #f0ece4;padding-top:12px;">${a}</div>
        </details>`).join('')}
      </div>
      <div style="background:#f9f7f3;border-radius:12px;padding:18px;text-align:center;">
        <div style="font-weight:600;color:#1a1a2e;margin-bottom:6px;">Still need help?</div>
        <div style="font-size:13px;color:#8a8a9a;margin-bottom:12px;">Our support team is available Mon–Sat, 9 AM – 7 PM</div>
        <div style="display:flex;gap:10px;justify-content:center;">
          <button onclick="showToast('📞 Calling support: +91 80 4567 8900')" style="background:#1a1a2e;color:#fff;border:none;padding:10px 20px;border-radius:10px;font-size:13px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;">📞 Call Support</button>
          <button onclick="showToast('💬 Opening live chat...')" style="background:#c9963a;color:#fff;border:none;padding:10px 20px;border-radius:10px;font-size:13px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;">💬 Live Chat</button>
        </div>
      </div>`
  },

  'support-privacy': {
    title: '🔒 Privacy Policy',
    html: `
      <div style="font-size:12px;color:#8a8a9a;margin-bottom:16px;">Last updated: March 1, 2026</div>
      ${[['Information We Collect','We collect information you provide when registering (name, email, phone, city, role). We also collect usage data such as pages visited, searches made, and properties viewed to improve our services.'],['How We Use Your Information','Your information is used to: match you with relevant properties, connect you with agents, send you property alerts, and improve our platform experience. We do not sell your personal data to third parties.'],['Data Security','All data is encrypted using industry-standard SSL/TLS protocols. Passwords are hashed and never stored in plain text. We conduct regular security audits to protect your information.'],['Cookies','We use cookies to remember your preferences and browsing history on NestFinder. You can disable cookies in your browser settings, but some features may not function properly.'],['Your Rights','You have the right to access, update or delete your personal information at any time. Contact privacy@nestfinder.com to exercise these rights.'],['Third-Party Links','Our platform may contain links to third-party websites. We are not responsible for their privacy practices. Please review their privacy policies separately.'],['Contact Us','For privacy-related queries: privacy@nestfinder.com · NestFinder Pvt. Ltd., Koramangala, Bangalore 560034']].map(([t,b])=>`
      <div style="margin-bottom:18px;">
        <div style="font-weight:700;color:#1a1a2e;font-size:14px;margin-bottom:6px;">📌 ${t}</div>
        <p style="color:#666;font-size:13px;line-height:1.8;margin:0;">${b}</p>
      </div>`).join('')}`
  },

  'support-terms': {
    title: '📋 Terms of Use',
    html: `
      <div style="font-size:12px;color:#8a8a9a;margin-bottom:16px;">Effective Date: January 1, 2026 · Governing Law: Karnataka, India</div>
      ${[['Acceptance of Terms','By accessing NestFinder, you agree to be bound by these Terms of Use. If you do not agree, please discontinue use of the platform immediately.'],['User Eligibility','You must be 18 years or older to register and use NestFinder. By registering, you confirm that the information provided is accurate and up to date.'],['Property Listings','Sellers and agents are responsible for the accuracy of their listings. NestFinder reserves the right to remove any listing that is found to be fraudulent, misleading or in violation of applicable laws.'],['Prohibited Activities','Users must not post fake listings, impersonate others, scrape data, send spam, or engage in any activity that violates applicable laws or infringes on others\' rights.'],['Limitation of Liability','NestFinder acts as an intermediary platform and is not responsible for transactions between buyers and sellers. Always verify property documents independently before making any payment.'],['Intellectual Property','All content, logos, trademarks, and technology on NestFinder are owned by NestFinder Pvt. Ltd. Reproduction or distribution without written permission is prohibited.'],['Changes to Terms','NestFinder may update these terms at any time. Continued use of the platform after updates constitutes acceptance of the new terms.'],['Contact','For legal queries: legal@nestfinder.com · NestFinder Pvt. Ltd., Koramangala, Bangalore 560034']].map(([t,b])=>`
      <div style="margin-bottom:16px;">
        <div style="font-weight:700;color:#1a1a2e;font-size:14px;margin-bottom:5px;">📌 ${t}</div>
        <p style="color:#666;font-size:13px;line-height:1.8;margin:0;">${b}</p>
      </div>`).join('')}`
  },

  'support-contact': {
    title: '📞 Contact Us',
    html: `
      <p style="color:#666;line-height:1.8;margin-bottom:22px;">We'd love to hear from you. Reach us through any of the channels below — our team responds within 24 hours.</p>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:24px;">
        ${[['📞','General Support','+91 80 4567 8900','Mon–Sat, 9 AM–7 PM'],['📧','Email Us','support@nestfinder.com','Response in 24 hrs'],['💬','Live Chat','Available on website','Mon–Sat, 9 AM–7 PM'],['🏢','Head Office','Koramangala, Bangalore 560034','Visit by appointment']].map(([e,t,v,h])=>`
        <div style="background:#fff;border:1px solid #e8e0d0;border-radius:12px;padding:18px;text-align:center;" onmouseover="this.style.borderColor='#c9963a'" onmouseout="this.style.borderColor='#e8e0d0'">
          <div style="font-size:28px;margin-bottom:8px;">${e}</div>
          <div style="font-weight:600;color:#1a1a2e;font-size:13px;">${t}</div>
          <div style="color:#c9963a;font-size:13px;font-weight:500;margin-top:4px;">${v}</div>
          <div style="color:#8a8a9a;font-size:11px;margin-top:3px;">${h}</div>
        </div>`).join('')}
      </div>
      <div style="background:#f9f7f3;border-radius:14px;padding:22px;">
        <div style="font-weight:600;color:#1a1a2e;margin-bottom:14px;font-size:15px;">✉️ Send us a message</div>
        <div style="display:flex;flex-direction:column;gap:10px;">
          <input type="text" placeholder="Your Name" style="padding:12px 14px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:13px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
          <input type="email" placeholder="Email Address" style="padding:12px 14px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:13px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"/>
          <textarea placeholder="Your message..." rows="3" style="padding:12px 14px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:13px;font-family:'DM Sans',sans-serif;outline:none;resize:none;" onfocus="this.style.borderColor='#c9963a'" onblur="this.style.borderColor='#e0ddd6'"></textarea>
          <button onclick="showToast('✅ Message sent! We will reply within 24 hours.')" style="background:#c9963a;color:#fff;border:none;padding:13px;border-radius:10px;font-size:14px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;">Send Message →</button>
        </div>
      </div>`
  },

  'support-fraud': {
    title: '🚨 Report Fraud',
    html: `
      <div style="background:#fff0ee;border:1px solid #f0c8c0;border-radius:12px;padding:16px 18px;margin-bottom:22px;">
        <div style="font-weight:700;color:#c0533a;font-size:14px;margin-bottom:6px;">⚠️ Protect Yourself from Property Fraud</div>
        <p style="color:#666;font-size:13px;line-height:1.8;margin:0;">Never pay any advance amount without physically visiting the property and verifying all original documents. NestFinder never asks for payment to show properties.</p>
      </div>
      <div style="margin-bottom:20px;">
        <div style="font-weight:700;color:#1a1a2e;margin-bottom:12px;font-size:14px;">🔴 Common Fraud Warning Signs</div>
        <div style="display:flex;flex-direction:column;gap:8px;">
          ${['Price is unusually low compared to market rate','Owner claims to be abroad and asks for advance via transfer','Refuses physical site visit or document verification','No original title deed or RERA registration','Asks for full payment before agreement is signed','Property listed by multiple different "owners"'].map(w=>`
          <div style="background:#fff;border:1px solid #f0c8c0;border-radius:10px;padding:12px 16px;font-size:13px;color:#666;display:flex;gap:10px;align-items:flex-start;">
            <span style="color:#c0533a;flex-shrink:0;">⛔</span>${w}
          </div>`).join('')}
        </div>
      </div>
      <div style="background:#f9f7f3;border-radius:14px;padding:22px;">
        <div style="font-weight:600;color:#1a1a2e;margin-bottom:14px;font-size:15px;">📝 Report a Fraudulent Listing</div>
        <div style="display:flex;flex-direction:column;gap:10px;">
          <input type="text" placeholder="Property Listing URL or ID" style="padding:12px 14px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:13px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c0533a'" onblur="this.style.borderColor='#e0ddd6'"/>
          <input type="text" placeholder="Your Name & Phone Number" style="padding:12px 14px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:13px;font-family:'DM Sans',sans-serif;outline:none;" onfocus="this.style.borderColor='#c0533a'" onblur="this.style.borderColor='#e0ddd6'"/>
          <select style="padding:12px 14px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:13px;font-family:'DM Sans',sans-serif;outline:none;background:#fff;">
            <option>Select Fraud Type</option>
            <option>Fake/Non-existent Property</option>
            <option>Wrong Price or Details</option>
            <option>Duplicate Listing</option>
            <option>Advance Payment Scam</option>
            <option>Identity Fraud</option>
            <option>Other</option>
          </select>
          <textarea placeholder="Describe the fraud in detail..." rows="3" style="padding:12px 14px;border:1.5px solid #e0ddd6;border-radius:10px;font-size:13px;font-family:'DM Sans',sans-serif;outline:none;resize:none;" onfocus="this.style.borderColor='#c0533a'" onblur="this.style.borderColor='#e0ddd6'"></textarea>
          <button onclick="showToast('🚨 Fraud report submitted! We will investigate within 48 hours.')" style="background:#c0533a;color:#fff;border:none;padding:13px;border-radius:10px;font-size:14px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;">Submit Fraud Report 🚨</button>
        </div>
        <div style="text-align:center;font-size:12px;color:#8a8a9a;margin-top:12px;">Emergency: fraud@nestfinder.com · +91 80 4567 8999</div>
      </div>`
  }
};

function openPage(section, key) {
  const page = pages[section + '-' + key];
  if(!page) return;
  document.getElementById('pageModalTitle').textContent = page.title;
  document.getElementById('pageModalBody').innerHTML = page.html;
  document.getElementById('pageModal').style.display = 'block';
  document.body.style.overflow = 'hidden';
  // Scroll modal to top
  document.getElementById('pageModal').scrollTop = 0;
}

function closePageModal(e) {
  if(!e || e.target === document.getElementById('pageModal')) {
    document.getElementById('pageModal').style.display = 'none';
    document.body.style.overflow = '';
  }
}
</script>


<!-- PREMIUM LISTING MODAL (Razorpay) -->
<div id="premiumModal" style="display:none;position:fixed;inset:0;z-index:4500;background:rgba(0,0,0,0.7);backdrop-filter:blur(6px);align-items:center;justify-content:center;padding:20px;" onclick="closePremiumModal(event)">
  <div style="background:#fff;border-radius:20px;width:100%;max-width:460px;overflow:hidden;box-shadow:0 32px 80px rgba(0,0,0,0.4);" onclick="event.stopPropagation()">
    <div style="background:linear-gradient(135deg,#c9963a,#1a1a2e);padding:28px 28px 22px;text-align:center;">
      <div style="font-size:36px;margin-bottom:8px;">⭐</div>
      <div style="font-family:'Playfair Display',serif;font-size:22px;font-weight:700;color:#fff;">Boost Your Listing</div>
      <div style="color:rgba(255,255,255,0.65);font-size:13px;margin-top:6px;">Get 10x more views with Premium</div>
    </div>
    <div style="padding:24px 28px;">
      <div style="display:flex;flex-direction:column;gap:12px;margin-bottom:24px;">
        
        <div onclick="selectPlan(this,499,'⭐ Basic Boost','₹499')" class="plan-card" style="border:2px solid #e0ddd6;border-radius:12px;padding:14px 18px;cursor:pointer;display:flex;justify-content:space-between;align-items:center;transition:all 0.2s;" onmouseover="this.style.borderColor='#c9963a'" onmouseout="if(!this.classList.contains('selected-plan'))this.style.borderColor='#e0ddd6'">
          <div><div style="font-weight:600;color:#1a1a2e;">⭐ Basic Boost</div><div style="font-size:12px;color:#8a8a9a;margin-top:2px;">7 days · 3x more views</div></div>
          <div style="font-size:18px;font-weight:700;color:#c9963a;">₹499</div>
        </div>
        <div onclick="selectPlan(this,999,'🌟 Standard Boost','₹999')" class="plan-card" style="border:2px solid #e0ddd6;border-radius:12px;padding:14px 18px;cursor:pointer;display:flex;justify-content:space-between;align-items:center;transition:all 0.2s;" onmouseover="this.style.borderColor='#c9963a'" onmouseout="if(!this.classList.contains('selected-plan'))this.style.borderColor='#e0ddd6'">
          <div><div style="font-weight:600;color:#1a1a2e;">🌟 Standard Boost</div><div style="font-size:12px;color:#8a8a9a;margin-top:2px;">15 days · 7x more views</div></div>
          <div style="font-size:18px;font-weight:700;color:#c9963a;">₹999</div>
        </div>
        <div onclick="selectPlan(this,1999,'💎 Premium Boost','₹1,999')" class="plan-card" style="border:2px solid #e0ddd6;border-radius:12px;padding:14px 18px;cursor:pointer;display:flex;justify-content:space-between;align-items:center;transition:all 0.2s;" onmouseover="this.style.borderColor='#c9963a'" onmouseout="if(!this.classList.contains('selected-plan'))this.style.borderColor='#e0ddd6'">
          <div><div style="font-weight:600;color:#1a1a2e;">💎 Premium Boost</div><div style="font-size:12px;color:#8a8a9a;margin-top:2px;">30 days · 10x more views + Homepage Feature</div></div>
          <div style="font-size:18px;font-weight:700;color:#c9963a;">₹1,999</div>
        </div>
      </div>
      <div id="selectedPlanInfo" style="background:#fff8f0;border:1px solid #f0dcc0;border-radius:10px;padding:12px 16px;margin-bottom:18px;font-size:13px;color:#c9963a;font-weight:500;display:none;"></div>
      <button id="payNowBtn" onclick="initiateRazorpay()" style="width:100%;background:#c9963a;color:#fff;border:none;padding:15px;border-radius:12px;font-size:16px;font-weight:700;cursor:pointer;font-family:'DM Sans',sans-serif;opacity:0.5;pointer-events:none;">Select a Plan to Continue →</button>
      <div style="text-align:center;margin-top:12px;font-size:11px;color:#aaa;">🔒 Secured by Razorpay · UPI, Cards, NetBanking accepted</div>
      <button onclick="closePremiumModal()" style="width:100%;margin-top:10px;background:none;border:none;color:#8a8a9a;font-size:13px;cursor:pointer;font-family:'DM Sans',sans-serif;">Maybe later</button>
    </div>
  </div>
</div>
</body>
</html>
