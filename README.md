<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>학교 시설 안내</title>
<link href="https://fonts.googleapis.com/css2?family=Nanum+Myeongjo:wght@400;700;800&family=Noto+Sans+KR:wght@300;400;500;700&display=swap" rel="stylesheet">
<style>
:root{
  --white:#fff;--bg:#f4f6f9;--bg2:#eef1f6;
  --navy:#0d2a5e;--navy-mid:#1a3f7a;--navy-light:#2a5298;
  --accent:#1565c0;--accent-light:#e8f0fe;
  --gold:#b8922a;--text:#1a1a2e;--text-mid:#4a5568;--text-light:#8a9ab5;
  --border:#d4dce8;--border-light:#eaf0f8;
  --green-room:#c8d46a;--yellow-room:#f5c842;--cream-room:#f5f0d8;
  --shadow-sm:0 1px 4px rgba(13,42,94,.08);
  --shadow-md:0 4px 20px rgba(13,42,94,.12);
  --r:10px;--rs:6px;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
html,body{height:100%;overflow:hidden;}
body{background:var(--bg);color:var(--text);font-family:'Noto Sans KR',sans-serif;display:flex;flex-direction:column;}

/* HEADER */
header{background:var(--white);border-bottom:1px solid var(--border);padding:0 28px;height:56px;display:flex;align-items:center;justify-content:space-between;flex-shrink:0;box-shadow:var(--shadow-sm);position:relative;z-index:200;}
header::after{content:'';position:absolute;bottom:0;left:0;right:0;height:3px;background:linear-gradient(90deg,var(--navy),var(--accent),var(--gold));}
.logo{display:flex;align-items:center;gap:10px;}
.logo-em{width:34px;height:34px;background:var(--navy);border-radius:7px;display:grid;place-items:center;color:#fff;font-size:17px;}
.logo-name{font-family:'Nanum Myeongjo',serif;font-size:15px;font-weight:800;color:var(--navy);letter-spacing:1px;}
.logo-sub{font-size:9px;color:var(--text-light);letter-spacing:2px;}
.hdr-right{display:flex;align-items:center;gap:7px;}
.btn{padding:6px 13px;border-radius:var(--rs);font-size:11px;font-weight:500;cursor:pointer;border:none;transition:all .2s;font-family:'Noto Sans KR',sans-serif;}
.btn-ghost{background:transparent;color:var(--text-mid);}
.btn-ghost:hover{background:var(--bg2);color:var(--navy);}
.btn-solid{background:var(--navy);color:#fff;}
.btn-solid:hover{background:var(--navy-mid);}
.hdr-time{font-size:11px;color:var(--text-light);font-variant-numeric:tabular-nums;letter-spacing:1px;padding:5px 9px;background:var(--bg2);border-radius:var(--rs);border:1px solid var(--border);}

.app{flex:1;display:flex;flex-direction:column;overflow:hidden;min-height:0;}

/* DEFAULT VIEW */
#vd{display:flex;flex-direction:column;flex:1;min-height:0;overflow:hidden;}
#vd.hidden{display:none;}
.map-bar{padding:8px 22px;background:#fff;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;flex-shrink:0;}
.map-bar-t{font-family:'Nanum Myeongjo',serif;font-size:14px;color:var(--navy);font-weight:700;}
.map-bar-s{font-size:10px;color:var(--text-light);margin-top:1px;}
.map-bar-ctrl{display:flex;gap:3px;}
.zb{width:26px;height:26px;background:#fff;border:1px solid var(--border);border-radius:5px;font-size:13px;cursor:pointer;display:grid;place-items:center;color:var(--navy);transition:all .15s;line-height:1;}
.zb:hover{background:var(--navy);color:#fff;border-color:var(--navy);}
.map-outer{flex:1;overflow:hidden;position:relative;background:#eef1f7;min-height:0;}
.map-zoom{transform-origin:0 0;cursor:grab;width:100%;height:100%;}
.map-zoom:active{cursor:grabbing;}
.map-svg{width:100%;height:100%;display:block;}
.dz{cursor:pointer;}
.dz rect,.dz ellipse{fill:rgba(13,42,94,.05);stroke:rgba(13,42,94,.25);stroke-width:1.5;transition:all .2s;}
.dz:hover rect,.dz:hover ellipse{fill:rgba(21,101,192,.14);stroke:var(--accent);stroke-width:2;filter:drop-shadow(0 0 5px rgba(21,101,192,.3));}
.dz-lbl{fill:var(--navy);font-family:'Noto Sans KR',sans-serif;font-size:11px;font-weight:700;text-anchor:middle;pointer-events:none;paint-order:stroke;stroke:#fff;stroke-width:4px;}
.chip-bar{flex-shrink:0;padding:7px 18px;background:#fff;border-top:1px solid var(--border);display:flex;gap:7px;overflow-x:auto;scrollbar-width:none;}
.chip-bar::-webkit-scrollbar{display:none;}
.chip{display:flex;align-items:center;gap:5px;padding:5px 13px;background:#fff;border:1px solid var(--border);border-radius:20px;font-size:11px;color:var(--text-mid);cursor:pointer;transition:all .2s;white-space:nowrap;}
.chip:hover{border-color:var(--accent);color:var(--accent);background:var(--accent-light);}
.chip-dot{width:7px;height:7px;border-radius:50%;}

/* DETAIL VIEW */
#vdet{display:none;flex:1;min-height:0;overflow:hidden;}
#vdet.visible{display:flex;flex-direction:row;}

/* Left sidebar */
.side-l{width:178px;min-width:160px;background:var(--navy);display:flex;flex-direction:column;overflow:hidden;flex-shrink:0;}
.side-l-hdr{padding:12px 14px 8px;border-bottom:1px solid rgba(255,255,255,.1);flex-shrink:0;}
.back-btn{display:flex;align-items:center;gap:6px;cursor:pointer;color:rgba(255,255,255,.55);font-size:10px;background:none;border:none;font-family:'Noto Sans KR',sans-serif;margin-bottom:10px;transition:color .2s;padding:0;}
.back-btn:hover{color:#fff;}
.back-btn svg{width:12px;height:12px;stroke:currentColor;fill:none;stroke-width:2;}
.side-l-title{font-size:8px;color:rgba(255,255,255,.3);letter-spacing:2px;font-weight:500;}
.blist{flex:1;overflow-y:auto;padding:6px;display:flex;flex-direction:column;gap:1px;}
.blist::-webkit-scrollbar{width:2px;}
.blist::-webkit-scrollbar-thumb{background:rgba(255,255,255,.15);}
.bi{display:flex;align-items:center;gap:8px;padding:8px 10px;border-radius:6px;cursor:pointer;transition:all .15s;font-size:11px;color:rgba(255,255,255,.65);border:1px solid transparent;}
.bi:hover{background:rgba(255,255,255,.08);color:#fff;}
.bi.active{background:rgba(255,255,255,.14);color:#fff;border-color:rgba(255,255,255,.18);}
.bi-dot{width:7px;height:7px;border-radius:50%;flex-shrink:0;}
.bi-name{flex:1;font-weight:500;}
.fl-list{display:none;flex-direction:column;gap:1px;padding:3px 0 3px 22px;}
.fl-list.open{display:flex;}
.fl-btn{padding:5px 9px;border-radius:4px;cursor:pointer;background:none;border:none;font-family:'Noto Sans KR',sans-serif;font-size:10px;color:rgba(255,255,255,.48);text-align:left;width:100%;transition:all .15s;}
.fl-btn:hover{background:rgba(255,255,255,.06);color:rgba(255,255,255,.85);}
.fl-btn.active{background:rgba(255,216,64,.2);color:#ffd840;font-weight:700;}

/* Center scrollable */
.center-main{flex:1;overflow-y:auto;display:flex;flex-direction:column;min-width:0;background:var(--bg);}
.center-main::-webkit-scrollbar{width:5px;}
.center-main::-webkit-scrollbar-thumb{background:var(--border);border-radius:3px;}

/* Hero */
.d-hero{background:var(--navy);padding:24px 32px 20px;position:relative;overflow:hidden;flex-shrink:0;}
.d-hero::before{content:'';position:absolute;inset:0;background:linear-gradient(135deg,var(--navy),var(--navy-light));}
.d-hero::after{content:'';position:absolute;right:-40px;top:-40px;width:180px;height:180px;border-radius:50%;background:rgba(255,255,255,.03);border:1px solid rgba(255,255,255,.05);}
.hero-badge{position:relative;z-index:1;display:inline-flex;align-items:center;gap:6px;background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.15);padding:3px 10px;border-radius:20px;font-size:9px;color:rgba(255,255,255,.65);letter-spacing:2px;margin-bottom:8px;}
.hero-bdot{width:5px;height:5px;border-radius:50%;background:#7fff6b;}
.hero-title{position:relative;z-index:1;font-family:'Nanum Myeongjo',serif;font-size:26px;font-weight:800;color:#fff;letter-spacing:2px;margin-bottom:3px;}
.hero-sub{position:relative;z-index:1;font-size:9px;color:rgba(255,255,255,.35);letter-spacing:3px;margin-bottom:10px;}
.hero-desc{position:relative;z-index:1;font-size:12px;color:rgba(255,255,255,.72);line-height:1.9;max-width:500px;}

/* Info strip */
.istrip{background:#fff;border-bottom:1px solid var(--border-light);display:flex;flex-shrink:0;}
.is-it{flex:1;padding:12px 16px;border-right:1px solid var(--border-light);display:flex;flex-direction:column;gap:2px;}
.is-it:last-child{border-right:none;}
.is-lbl{font-size:9px;color:var(--text-light);letter-spacing:1.5px;}
.is-val{font-size:12px;font-weight:700;color:var(--navy);}

/* Content grid - image 2 layout */
.content-grid{display:grid;grid-template-columns:1fr 260px;flex:1;}
.col-left{padding:20px 20px 20px 26px;display:flex;flex-direction:column;gap:20px;border-right:1px solid var(--border-light);overflow-y:auto;}
.col-left::-webkit-scrollbar{width:4px;}
.col-left::-webkit-scrollbar-thumb{background:var(--border);border-radius:2px;}
.col-right{padding:20px 18px;display:flex;flex-direction:column;gap:12px;background:#fff;overflow-y:auto;}
.col-right::-webkit-scrollbar{width:4px;}
.col-right::-webkit-scrollbar-thumb{background:var(--border);border-radius:2px;}

.sec-hd{display:flex;align-items:center;gap:8px;margin-bottom:10px;padding-bottom:8px;border-bottom:2px solid var(--border-light);}
.sec-bar{width:3px;height:16px;background:var(--navy);border-radius:2px;flex-shrink:0;}
.sec-hd h3{font-family:'Nanum Myeongjo',serif;font-size:14px;color:var(--navy);font-weight:700;}

/* Floor plan */
.plan-wrap{background:#fff;border:1px solid var(--border);border-radius:var(--r);overflow:hidden;box-shadow:var(--shadow-sm);cursor:pointer;transition:border-color .2s;}
.plan-wrap:hover{border-color:var(--accent);}
.plan-topbar{display:flex;justify-content:space-between;align-items:center;padding:8px 14px;border-bottom:1px solid var(--border-light);background:var(--bg2);}
.plan-hint{font-size:9px;color:var(--accent);}
.plan-svg-area{padding:0;overflow:hidden;}
.plan-svg-area svg{display:block;width:100%;height:auto;}

/* Floor tabs */
.ftabs{display:flex;gap:5px;flex-wrap:wrap;margin-bottom:10px;}
.ftab{padding:5px 14px;border-radius:20px;font-size:10px;font-weight:500;cursor:pointer;border:1px solid var(--border);background:#fff;color:var(--text-mid);transition:all .15s;font-family:'Noto Sans KR',sans-serif;}
.ftab.on,.ftab:hover{background:var(--navy);color:#fff;border-color:var(--navy);}

/* Photos */
.photo-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;}
.ph-card{border-radius:var(--rs);overflow:hidden;border:1px solid var(--border);background:#fff;cursor:pointer;transition:all .2s;box-shadow:var(--shadow-sm);}
.ph-card:hover{transform:translateY(-2px);box-shadow:var(--shadow-md);border-color:var(--accent);}
.ph-img{aspect-ratio:4/3;background:var(--bg2);display:flex;align-items:center;justify-content:center;}
.ph-img svg{width:100%;height:100%;}
.ph-lbl{padding:5px 7px;font-size:9px;color:var(--text-mid);font-weight:500;text-align:center;}

/* Right col */
.floor-desc-title{font-size:13px;font-weight:700;color:var(--navy);margin-bottom:6px;font-family:'Nanum Myeongjo',serif;}
.floor-desc-text{font-size:11px;color:var(--text-mid);line-height:1.85;}
.info-list{display:flex;flex-direction:column;gap:5px;margin-top:4px;}
.info-row{padding:8px 11px;background:var(--bg2);border-radius:var(--rs);border:1px solid var(--border-light);}
.info-row-k{font-size:9px;color:var(--text-light);letter-spacing:1px;}
.info-row-v{font-size:11px;font-weight:600;color:var(--navy);margin-top:2px;}

/* LIGHTBOX */
#lb{position:fixed;inset:0;background:rgba(0,0,0,.9);z-index:1000;display:none;align-items:center;justify-content:center;padding:24px;backdrop-filter:blur(8px);}
#lb.open{display:flex;}
.lb-box{position:relative;max-width:92vw;max-height:92vh;background:#fff;border-radius:var(--r);overflow:hidden;box-shadow:0 24px 80px rgba(0,0,0,.5);display:flex;flex-direction:column;}
.lb-close{position:absolute;top:10px;right:10px;width:32px;height:32px;background:rgba(0,0,0,.6);color:#fff;border:none;border-radius:50%;font-size:16px;cursor:pointer;display:grid;place-items:center;z-index:10;line-height:1;}
.lb-close:hover{background:rgba(0,0,0,.85);}
.lb-content{flex:1;overflow:auto;background:var(--bg2);display:flex;align-items:flex-start;justify-content:center;padding:16px;}
.lb-content svg{width:min(900px,88vw);height:auto;}
.lb-cap{padding:10px 16px;font-size:12px;color:var(--text-mid);font-weight:500;background:#fff;border-top:1px solid var(--border);flex-shrink:0;}

/* SVG floor plan common styles */
.fp-wall{fill:#fff;stroke:#222;stroke-width:3;}
.fp-room-cream{fill:#f5f0d8;stroke:#888;stroke-width:1.5;}
.fp-room-green{fill:#c8d46a;stroke:#888;stroke-width:1.5;}
.fp-room-yellow{fill:#f5c842;stroke:#888;stroke-width:1.5;}
.fp-room-blue{fill:#c8e8f5;stroke:#888;stroke-width:1.5;}
.fp-txt{font-family:'Noto Sans KR',sans-serif;font-size:13px;font-weight:700;fill:#222;text-anchor:middle;dominant-baseline:middle;}
.fp-txt-sm{font-family:'Noto Sans KR',sans-serif;font-size:10px;font-weight:500;fill:#333;text-anchor:middle;dominant-baseline:middle;}
.fp-txt-xs{font-family:'Noto Sans KR',sans-serif;font-size:8.5px;fill:#444;text-anchor:middle;dominant-baseline:middle;}
.fp-stair{fill:#f5c842;stroke:#888;stroke-width:1;}
.fp-pink{fill:#f472b6;}
.fp-blue-icon{fill:#38bdf8;}
.fp-fire{fill:#ef4444;}
</style>
</head>
<body>

<header>
  <div class="logo">
    <div class="logo-em">🏫</div>
    <div>
      <div class="logo-name">학교 시설 안내</div>
      <div class="logo-sub">CAMPUS GUIDE SYSTEM</div>
    </div>
  </div>
  <div class="hdr-right">
    <button class="btn btn-ghost" id="hdr-back" style="display:none" onclick="goHome()">← 전체 지도</button>
    <button class="btn btn-ghost">학사 일정</button>
    <button class="btn btn-ghost">오시는 길</button>
    <button class="btn btn-solid">📞 대표 전화</button>
    <div class="hdr-time" id="clock">00:00:00</div>
  </div>
</header>

<div class="app">

<!-- DEFAULT VIEW -->
<div id="vd">
  <div class="map-bar">
    <div>
      <div class="map-bar-t">캠퍼스 시설 안내도</div>
      <div class="map-bar-s">건물 클릭 → 상세 정보 · 휠 확대/축소 · 드래그 이동</div>
    </div>
    <div class="map-bar-ctrl">
      <button class="zb" onclick="dvZ(1.2)">+</button>
      <button class="zb" onclick="dvZ(.83)">−</button>
      <button class="zb" onclick="dvR()" style="font-size:10px">↺</button>
    </div>
  </div>
  <div class="map-outer" id="dv-outer">
    <div class="map-zoom" id="dv-zoom">
      <svg class="map-svg" viewBox="0 0 1000 620" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <pattern id="g" patternUnits="userSpaceOnUse" width="8" height="8"><rect width="8" height="8" fill="#d4edda"/><line x1="0" y1="4" x2="8" y2="4" stroke="#c8e6cc" stroke-width=".4"/></pattern>
          <pattern id="pv" patternUnits="userSpaceOnUse" width="14" height="14"><rect width="14" height="14" fill="#e8ecf2"/><rect width="14" height="14" fill="none" stroke="#d8dfe8" stroke-width=".5"/></pattern>
          <filter id="sh"><feDropShadow dx="1" dy="2" stdDeviation="2" flood-color="rgba(0,0,0,.13)"/></filter>
        </defs>
        <rect width="1000" height="620" fill="#eef1f7"/>
        <rect x="530" y="40" width="445" height="555" fill="url(#pv)" rx="3" opacity=".9"/>
        <!-- Basketball -->
        <rect x="30" y="50" width="155" height="260" rx="3" fill="#dde8f5" stroke="#b8cce8" stroke-width="1.5"/>
        <text x="112" y="105" fill="#3a5a8a" font-size="11" text-anchor="middle" font-family="Noto Sans KR,sans-serif" font-weight="700">미니맵</text>
        <rect x="50" y="130" width="115" height="160" rx="3" fill="#c8d8f0" stroke="#a0b8d8" stroke-width="1"/>
        <circle cx="107" cy="210" r="28" fill="none" stroke="rgba(255,255,255,.7)" stroke-width="1.5"/>
        <text x="107" y="214" fill="#3a5a8a" font-size="10" text-anchor="middle" font-family="Noto Sans KR,sans-serif" font-weight="600">농구코트</text>
        <!-- Soccer -->
        <rect x="190" y="50" width="326" height="260" rx="3" fill="url(#g)" stroke="#a8d5a2" stroke-width="2"/>
        <rect x="205" y="65" width="296" height="230" fill="none" stroke="rgba(255,255,255,.9)" stroke-width="1.5"/>
        <line x1="353" y1="65" x2="353" y2="295" stroke="rgba(255,255,255,.9)" stroke-width="1.5"/>
        <circle cx="353" cy="180" r="32" fill="none" stroke="rgba(255,255,255,.8)" stroke-width="1.5"/>
        <circle cx="353" cy="180" r="3" fill="rgba(255,255,255,.8)"/>
        <rect x="205" y="138" width="22" height="84" fill="none" stroke="rgba(255,255,255,.7)" stroke-width="1"/>
        <rect x="479" y="138" width="22" height="84" fill="none" stroke="rgba(255,255,255,.7)" stroke-width="1"/>
        <text x="353" y="180" fill="rgba(255,255,255,.6)" font-size="13" text-anchor="middle" font-family="Noto Sans KR,sans-serif">축구장</text>
        <!-- 강당/급식실 -->
        <rect x="30" y="330" width="280" height="240" rx="3" fill="#e8edf5" filter="url(#sh)" stroke="#c0cce0" stroke-width="1.5"/>
        <line x1="30" y1="450" x2="310" y2="450" stroke="#c8d4e8" stroke-width="2"/>
        <text x="170" y="400" fill="#1a3f7a" font-size="12" font-weight="700" text-anchor="middle" font-family="Noto Sans KR,sans-serif">강당 (2층)</text>
        <text x="170" y="490" fill="#1a3f7a" font-size="12" font-weight="700" text-anchor="middle" font-family="Noto Sans KR,sans-serif">급식실 (1층)</text>
        <!-- 5동 -->
        <rect x="330" y="390" width="180" height="120" rx="2" fill="#f5dcd8" filter="url(#sh)" stroke="#e0b4ac" stroke-width="1.5"/>
        <rect x="330" y="390" width="180" height="22" rx="2" fill="#d4705a" stroke="#c05040" stroke-width="1"/>
        <text x="420" y="458" fill="#7a1a10" font-size="13" font-weight="700" text-anchor="middle" font-family="Noto Sans KR,sans-serif">5동</text>
        <!-- 3동 -->
        <rect x="546" y="90" width="130" height="360" rx="2" fill="#dde4f0" filter="url(#sh)" stroke="#b8c4d8" stroke-width="1.5"/>
        <rect x="546" y="90" width="130" height="18" rx="1" fill="#7090c0"/>
        <text x="611" y="278" fill="#1a3f7a" font-size="13" font-weight="700" text-anchor="middle" font-family="Noto Sans KR,sans-serif">3동</text>
        <!-- 4동+도서관 -->
        <rect x="692" y="90" width="130" height="190" rx="2" fill="#dceef0" filter="url(#sh)" stroke="#b0ccd0" stroke-width="1.5"/>
        <rect x="692" y="90" width="130" height="22" rx="1" fill="#60c080"/>
        <text x="757" y="175" fill="#0a3a20" font-size="12" font-weight="700" text-anchor="middle" font-family="Noto Sans KR,sans-serif">4동 / 도서관</text>
        <!-- connector -->
        <rect x="735" y="279" width="30" height="30" rx="1" fill="#c8d4e0" stroke="#b0bcc8" stroke-width="1"/>
        <!-- 2동 -->
        <rect x="692" y="308" width="130" height="210" rx="2" fill="#dde4f0" filter="url(#sh)" stroke="#b8c4d8" stroke-width="1.5"/>
        <rect x="692" y="308" width="130" height="16" rx="1" fill="#7090c0"/>
        <text x="757" y="418" fill="#1a3f7a" font-size="13" font-weight="700" text-anchor="middle" font-family="Noto Sans KR,sans-serif">2동</text>
        <!-- 1동 -->
        <rect x="840" y="90" width="120" height="450" rx="2" fill="#e8edf5" filter="url(#sh)" stroke="#c0cce0" stroke-width="1.5"/>
        <rect x="852" y="110" width="13" height="9" rx="1" fill="#c0d0e8" stroke="#b0c0d8" stroke-width=".5"/>
        <rect x="871" y="110" width="13" height="9" rx="1" fill="#c0d0e8" stroke="#b0c0d8" stroke-width=".5"/>
        <rect x="890" y="110" width="13" height="9" rx="1" fill="#d8e4f0" stroke="#b0c0d8" stroke-width=".5"/>
        <rect x="909" y="110" width="13" height="9" rx="1" fill="#c0d0e8" stroke="#b0c0d8" stroke-width=".5"/>
        <rect x="928" y="110" width="12" height="9" rx="1" fill="#c0d0e8" stroke="#b0c0d8" stroke-width=".5"/>
        <rect x="880" y="498" width="28" height="34" rx="1" fill="#c0cce0" stroke="#b0bcd0" stroke-width="1"/>
        <text x="900" y="330" fill="#1a3f7a" font-size="13" font-weight="700" text-anchor="middle" font-family="Noto Sans KR,sans-serif">1동</text>
        <circle cx="960" cy="565" r="24" fill="white" stroke="#c0cce0" stroke-width="1.5" opacity=".92"/>
        <polygon points="960,547 963,562 960,560 957,562" fill="#c0392b"/>
        <polygon points="960,583 963,568 960,570 957,568" fill="#8a9ab5"/>
        <text x="960" y="550" fill="#c0392b" font-size="6" text-anchor="middle" font-family="monospace">N</text>
        <!-- zones -->
        <g class="dz" onclick="sel('field')"><rect x="25" y="45" width="496" height="272" rx="3"/><text class="dz-lbl" x="275" y="60">운동장</text></g>
        <g class="dz" onclick="sel('hall')"><rect x="25" y="325" width="285" height="250" rx="3"/><text class="dz-lbl" x="167" y="578">강당 / 급식실</text></g>
        <g class="dz" onclick="sel('b5')"><rect x="325" y="385" width="190" height="130" rx="2"/><text class="dz-lbl" x="420" y="530">5동</text></g>
        <g class="dz" onclick="sel('b3')"><rect x="541" y="85" width="140" height="370" rx="2"/><text class="dz-lbl" x="611" y="465">3동</text></g>
        <g class="dz" onclick="sel('b4')"><rect x="687" y="85" width="140" height="200" rx="2"/><text class="dz-lbl" x="757" y="295">4동/도서관</text></g>
        <g class="dz" onclick="sel('b2')"><rect x="687" y="303" width="140" height="220" rx="2"/><text class="dz-lbl" x="757" y="530">2동</text></g>
        <g class="dz" onclick="sel('b1')"><rect x="835" y="85" width="130" height="465" rx="2"/><text class="dz-lbl" x="900" y="558">1동</text></g>
      </svg>
    </div>
  </div>
  <div class="chip-bar" id="chip-bar"></div>
</div>

<!-- DETAIL VIEW -->
<div id="vdet">
  <div class="side-l">
    <div class="side-l-hdr">
      <button class="back-btn" onclick="goHome()"><svg viewBox="0 0 16 16"><path d="M10 12L6 8l4-4"/></svg>전체 지도</button>
      <div class="side-l-title">시설 목록</div>
    </div>
    <div class="blist" id="blist"></div>
  </div>
  <div class="center-main" id="center-main">
    <div class="d-hero">
      <div class="hero-badge"><span class="hero-bdot"></span><span id="hbadge">시설 안내</span></div>
      <div class="hero-title" id="htitle">—</div>
      <div class="hero-sub" id="hsub">—</div>
      <div class="hero-desc" id="hdesc">—</div>
    </div>
    <div class="istrip" id="istrip"></div>
    <div class="content-grid" id="content-grid">
      <div class="col-left" id="col-left">
        <div>
          <div class="sec-hd"><div class="sec-bar"></div><h3 id="plan-title">구조도</h3></div>
          <div class="ftabs" id="ftabs"></div>
          <div class="plan-wrap" onclick="openLBPlan()" id="plan-wrap">
            <div class="plan-topbar">
              <span id="plan-lbl" style="font-size:10px;color:var(--text-light);letter-spacing:1px;"></span>
              <span class="plan-hint">🔍 클릭하여 확대</span>
            </div>
            <div class="plan-svg-area" id="plan-svg-area"></div>
          </div>
        </div>
        <div>
          <div class="sec-hd"><div class="sec-bar"></div><h3>시설 사진</h3></div>
          <div class="photo-grid" id="pgrid"></div>
        </div>
      </div>
      <div class="col-right" id="col-right">
        <div>
          <div class="sec-hd"><div class="sec-bar"></div><h3>층 · 장소 설명</h3></div>
          <div class="floor-desc-title" id="rdesc-t"></div>
          <div class="floor-desc-text" id="rdesc-b"></div>
        </div>
        <div>
          <div class="sec-hd" style="margin-top:14px;"><div class="sec-bar"></div><h3>기본 정보</h3></div>
          <div class="info-list" id="ilist"></div>
        </div>
      </div>
    </div>
  </div>
</div>

</div><!-- .app -->

<!-- LIGHTBOX -->
<div id="lb" onclick="lbClick(event)">
  <div class="lb-box">
    <button class="lb-close" onclick="closeLB()">✕</button>
    <div class="lb-content" id="lb-content"></div>
    <div class="lb-cap" id="lb-cap"></div>
  </div>
</div>

<script>
// ════════════════════════════════════════════
//  FLOOR PLAN SVGs  (실제 구조도)
// ════════════════════════════════════════════

// Common helpers
const W = (text, x, y, cls='fp-txt', extra='') =>
  `<text class="${cls}" x="${x}" y="${y}" ${extra}>${text}</text>`;
const R = (x,y,w,h,cls='fp-room-cream',r=4) =>
  `<rect class="${cls}" x="${x}" y="${y}" width="${w}" height="${h}" rx="${r}"/>`;
const STAIR = (x,y,w=44,h=44) =>
  `<rect class="fp-stair" x="${x}" y="${y}" width="${w}" height="${h}" rx="3"/>
   <text x="${x+w/2}" y="${y+h/2}" class="fp-txt-xs">계단</text>`;
const FIRE = (x,y) =>
  `<rect class="fp-fire" x="${x}" y="${y}" width="12" height="14" rx="2"/>`;
const WOMEN = (x,y) =>
  `<rect x="${x}" y="${y}" width="36" height="44" rx="4" fill="#f472b6"/>
   <text x="${x+18}" y="${y+26}" class="fp-txt-xs" style="fill:white;font-size:7px;">WOMEN</text>`;
const MEN = (x,y) =>
  `<rect x="${x}" y="${y}" width="36" height="44" rx="4" fill="#38bdf8"/>
   <text x="${x+18}" y="${y+26}" class="fp-txt-xs" style="fill:white;font-size:7px;">MEN</text>`;

// ─── 1동 4층 ───
const b1_4f = `<svg viewBox="0 0 820 280" xmlns="http://www.w3.org/2000/svg">
  <rect class="fp-wall" x="4" y="4" width="812" height="272" rx="6"/>
  <!-- top protrusions for stairs/WC -->
  <rect class="fp-wall" x="160" y="4" width="160" height="80" rx="4"/>
  <rect class="fp-wall" x="420" y="4" width="160" height="80" rx="4"/>
  <!-- Women / Men / stairs -->
  ${WOMEN(172,12)} ${STAIR(242,12,60,60)}
  ${STAIR(432,12,60,60)} ${MEN(504,12)}
  <!-- corridor -->
  <line x1="4" y1="100" x2="816" y2="100" stroke="#ccc" stroke-width="1" stroke-dasharray="6,3"/>
  <!-- rooms row -->
  ${R(20,118,96,130)} ${W('2-1',68,183)}
  ${R(128,118,96,130)} ${W('2-2',176,183)}
  ${R(236,118,96,130)} ${W('2-3',284,183)}
  ${R(344,118,180,130,'fp-room-cream')} ${W('큰들마',434,176)} ${W('콜로키움',434,196,'fp-txt-sm')}
  ${R(536,118,96,130)} ${W('2-4',584,183)}
  ${R(644,118,96,130)} ${W('2-5',692,183)}
  ${R(752,118,50,130)} ${W('2-6',777,183)}
  <!-- stair right -->
  ${STAIR(768,118,44,50)}
  <!-- fire -->
  ${FIRE(14,106)} ${FIRE(122,106)} ${FIRE(230,106)} ${FIRE(340,106)} ${FIRE(510,106)} ${FIRE(532,106)} ${FIRE(638,106)} ${FIRE(746,106)}
</svg>`;

// ─── 1동 3층 ───
const b1_3f = `<svg viewBox="0 0 820 280" xmlns="http://www.w3.org/2000/svg">
  <rect class="fp-wall" x="4" y="4" width="812" height="272" rx="6"/>
  <rect class="fp-wall" x="160" y="4" width="160" height="80" rx="4"/>
  <rect class="fp-wall" x="420" y="4" width="160" height="80" rx="4"/>
  ${WOMEN(172,12)} ${STAIR(242,12,60,60)}
  ${STAIR(432,12,60,60)} ${MEN(504,12)}
  <!-- top right: 꿈키움라운지 + 학습실 -->
  <rect class="fp-wall" x="640" y="4" width="176" height="96" rx="4"/>
  ${R(642,6,108,42,'fp-room-green')} ${W('꿈키움라운지',696,27,'fp-txt-sm')}
  ${R(756,6,58,42,'fp-room-green')} ${W('학습실',785,27,'fp-txt-sm')}
  ${R(642,52,108,42,'fp-room-green')} ${W('꿈키움라운지',696,73,'fp-txt-sm')}
  ${R(756,52,58,42,'fp-room-green')} ${W('학습실',785,73,'fp-txt-sm')}
  <line x1="4" y1="100" x2="816" y2="100" stroke="#ccc" stroke-width="1" stroke-dasharray="6,3"/>
  ${R(20,118,96,130)} ${W('1-8',68,183)}
  ${R(128,118,96,130)} ${W('1-7',176,183)}
  ${R(236,118,96,130)} ${W('1-6',284,183)}
  ${R(344,118,64,130,'fp-room-yellow')} ${W('2학년',376,173,'fp-txt-sm')} ${W('교무실',376,191,'fp-txt-sm')}
  ${R(420,118,96,130)} ${W('1-5',468,183)}
  ${R(528,118,96,130)} ${W('2-8',576,183)}
  ${R(636,118,96,130)} ${W('2-7',684,183)}
  ${R(744,118,64,130,'fp-room-green')} ${W('꿈키움',776,170,'fp-txt-sm')} ${W('라운지',776,186,'fp-txt-sm')}
  <!-- 학습실 right side -->
  ${R(744,118,34,62,'fp-room-green')}
  ${R(744,184,34,64,'fp-room-green')}
  ${STAIR(760,230,44,18)}
  ${FIRE(14,106)} ${FIRE(122,106)} ${FIRE(230,106)} ${FIRE(416,106)} ${FIRE(524,106)} ${FIRE(632,106)} ${FIRE(740,106)}
</svg>`;

// ─── 1동 2층 ───
const b1_2f = `<svg viewBox="0 0 820 280" xmlns="http://www.w3.org/2000/svg">
  <rect class="fp-wall" x="4" y="4" width="812" height="272" rx="6"/>
  <rect class="fp-wall" x="160" y="4" width="160" height="80" rx="4"/>
  <rect class="fp-wall" x="420" y="4" width="160" height="80" rx="4"/>
  ${WOMEN(172,12)} ${STAIR(242,12,60,60)}
  ${STAIR(432,12,60,60)} ${MEN(504,12)}
  <rect class="fp-wall" x="640" y="4" width="176" height="96" rx="4"/>
  ${R(642,6,176,88,'fp-room-green')} ${W('꿈키움 라운지',730,50,'fp-txt-sm')}
  <line x1="4" y1="100" x2="816" y2="100" stroke="#ccc" stroke-width="1" stroke-dasharray="6,3"/>
  <!-- 하니꿈틀 공작소 left big -->
  ${R(20,104,150,168,'fp-room-green')} ${W('하니꿈틀',95,175)} ${W('공작소',95,195,'fp-txt-sm')}
  ${R(182,118,96,130)} ${W('1-4',230,183)}
  ${R(290,118,64,130,'fp-room-yellow')} ${W('1학년',322,173,'fp-txt-sm')} ${W('교무실',322,191,'fp-txt-sm')}
  ${R(366,118,96,130)} ${W('1-3',414,183)}
  ${R(474,118,96,130)} ${W('1-2',522,183)}
  ${R(582,118,96,130)} ${W('1-1',630,183)}
  ${R(690,118,60,130,'fp-room-green')} ${W('꿈키움',720,170,'fp-txt-sm')} ${W('라운지',720,186,'fp-txt-sm')}
  ${R(756,118,34,62,'fp-room-green')} ${W('학습실',773,149,'fp-txt-xs')}
  ${R(756,184,34,64,'fp-room-green')} ${W('학습실',773,216,'fp-txt-xs')}
  ${STAIR(760,230,44,18)}
  ${FIRE(14,106)} ${FIRE(178,106)} ${FIRE(362,106)} ${FIRE(470,106)} ${FIRE(578,106)} ${FIRE(686,106)}
</svg>`;

// ─── 1동 1층 ───
const b1_1f = `<svg viewBox="0 0 820 280" xmlns="http://www.w3.org/2000/svg">
  <rect class="fp-wall" x="4" y="4" width="812" height="272" rx="6"/>
  <rect class="fp-wall" x="160" y="4" width="160" height="80" rx="4"/>
  <rect class="fp-wall" x="420" y="4" width="160" height="80" rx="4"/>
  ${WOMEN(172,12)} ${STAIR(242,12,60,60)}
  <!-- 출입문 -->
  <rect x="326" y="94" width="56" height="10" rx="2" fill="#aaa"/>
  <text x="354" y="101" class="fp-txt-xs" style="fill:#555;">출입문</text>
  ${STAIR(432,12,60,60)} ${MEN(504,12)}
  <!-- Wee클래스 top right -->
  <rect class="fp-wall" x="610" y="4" width="206" height="96" rx="4"/>
  ${R(612,6,204,88,'fp-room-green')} ${W('wee클래스',714,50,'fp-txt')}
  <!-- 출입문 right -->
  <rect x="790" y="94" width="56" height="10" rx="2" fill="#aaa"/>
  <text x="818" y="101" class="fp-txt-xs" style="fill:#555;">출입문</text>
  <line x1="4" y1="100" x2="816" y2="100" stroke="#ccc" stroke-width="1" stroke-dasharray="6,3"/>
  <!-- 정독실 left big -->
  ${R(20,104,148,168,'fp-room-green')} ${W('정독실',94,188,'fp-txt')}
  ${R(180,118,108,130)} ${W('제1과학실',234,183,'fp-txt-sm')}
  ${R(296,118,60,130,'fp-room-cream')} ${W('과학과',326,174,'fp-txt-xs')} ${W('연구실',326,190,'fp-txt-xs')}
  ${R(368,118,108,130)} ${W('제2과학실',422,183,'fp-txt-sm')}
  ${R(484,118,60,130,'fp-room-cream')} ${W('과학',514,172,'fp-txt-xs')} ${W('자료실',514,186,'fp-txt-xs')}
  ${R(552,118,60,130,'fp-room-cream')} ${W('음악과',582,172,'fp-txt-xs')} ${W('연구실',582,186,'fp-txt-xs')}
  ${R(620,118,152,130,'fp-room-green')} ${W('음악실',696,183,'fp-txt')}
  ${STAIR(764,118,44,50)}
  ${FIRE(176,110)} ${FIRE(364,110)} ${FIRE(480,110)} ${FIRE(548,110)} ${FIRE(616,110)}
</svg>`;

// ─── 5동 2층 ───
const b5_2f = `<svg viewBox="0 0 700 160" xmlns="http://www.w3.org/2000/svg">
  <rect class="fp-wall" x="4" y="4" width="692" height="152" rx="6"/>
  ${R(14,14,120,60,'fp-room-cream')} ${W('교육공무직휴게실',74,44,'fp-txt-xs')}
  ${R(14,78,120,60,'fp-room-cream')} ${W('여자탈의실',74,108,'fp-txt-sm')}
  <text x="74" y="14" class="fp-txt-xs"><!-- label --></text>
  ${R(14,140,120,12,'fp-room-cream')} ${W('남자탈의실',74,146,'fp-txt-xs')}
  <!-- fix layout -->
  <rect class="fp-room-cream" x="14" y="78" width="120" height="28" rx="3" stroke="#888" stroke-width="1.5"/>
  <text class="fp-txt-xs" x="74" y="92">여자탈의실</text>
  <rect class="fp-room-cream" x="14" y="108" width="120" height="28" rx="3" stroke="#888" stroke-width="1.5"/>
  <text class="fp-txt-xs" x="74" y="122">남자탈의실</text>
  <rect class="fp-room-cream" x="14" y="138" width="120" height="14" rx="2" stroke="#888" stroke-width="1.5"/>
  <text class="fp-txt-xs" x="74" y="145">남교사휴게실</text>
  ${R(148,14,340,136,'fp-room-cream')} ${W('체력단련실',318,82,'fp-txt')}
  ${R(502,14,100,136,'fp-room-cream')} ${W('체육과',552,74,'fp-txt-sm')} ${W('연구실',552,90,'fp-txt-sm')}
  ${STAIR(614,60,70,60)}
</svg>`;

// ─── 5동 1층 ───
const b5_1f = `<svg viewBox="0 0 500 120" xmlns="http://www.w3.org/2000/svg">
  <rect class="fp-wall" x="4" y="4" width="492" height="112" rx="6"/>
  ${R(14,14,140,92,'fp-room-cream')} ${W('여탈의실',84,60,'fp-txt-sm')}
  ${R(166,14,140,92,'fp-room-cream')} ${W('남탈의실',236,60,'fp-txt-sm')}
  ${R(318,14,140,92,'fp-room-cream')} ${W('체육비품실',388,60,'fp-txt-sm')}
  ${STAIR(434,60,54,46)}
</svg>`;

// ─── 4동 지하 ───
const b4_b1 = `<svg viewBox="0 0 760 200" xmlns="http://www.w3.org/2000/svg">
  <rect class="fp-wall" x="4" y="4" width="752" height="192" rx="6"/>
  ${R(14,14,220,172,'fp-room-cream')} ${W('시청각실',124,100,'fp-txt')}
  ${R(248,14,140,80,'fp-room-cream')}
  ${R(400,14,200,80,'fp-room-cream')}
  ${STAIR(560,68,60,60)}
  ${R(636,14,110,80,'fp-room-cream')}
  ${R(636,100,110,86,'fp-room-cream')}
</svg>`;

// ─── 4동 1층 ───
const b4_1f = `<svg viewBox="0 0 820 300" xmlns="http://www.w3.org/2000/svg">
  <!-- Left block -->
  <rect class="fp-wall" x="4" y="4" width="380" height="292" rx="6"/>
  ${R(14,14,110,80,'fp-room-cream')} ${W('인쇄실',69,54,'fp-txt-sm')}
  ${R(134,14,110,80,'fp-room-cream')} ${W('행정실',189,54,'fp-txt-sm')}
  ${R(254,14,110,80,'fp-room-cream')} ${W('당직실',309,54,'fp-txt-sm')}
  <!-- 출입문 top -->
  <rect x="170" y="4" width="60" height="8" rx="2" fill="#aaa"/>
  <text x="200" y="10" class="fp-txt-xs" style="fill:#555;">출입문</text>
  ${STAIR(340,10,40,60)}
  <!-- 홍보관 middle -->
  <text class="fp-txt-sm" x="200" y="140">홍보관</text>
  ${R(14,160,110,100,'fp-room-cream')} ${W('교장실',69,210,'fp-txt-sm')}
  ${R(134,160,100,100,'fp-room-cream')} ${W('학부모',184,200,'fp-txt-xs')} ${W('회의실',184,215,'fp-txt-xs')}
  <!-- WC -->
  ${WOMEN(248,170)} ${MEN(288,170)}
  <!-- 출입문 bottom -->
  <rect x="170" y="288" width="60" height="8" rx="2" fill="#aaa"/>
  <text x="200" y="298" class="fp-txt-xs" style="fill:#555;">출입문</text>
  ${FIRE(10,108)}
  <!-- Right block: 도서관 -->
  <rect class="fp-wall" x="434" y="4" width="382" height="292" rx="6"/>
  ${STAIR(440,10,50,56)} ${WOMEN(500,14)}
  ${R(544,14,268,272,'fp-room-green')} ${W('도서관',678,150,'fp-txt')}
  ${STAIR(440,220,50,56)} ${MEN(500,226)}
  <!-- 출입문 middle -->
  <rect x="430" y="138" width="8" height="24" rx="2" fill="#aaa"/>
  <text x="418" y="150" class="fp-txt-xs" style="fill:#555;writing-mode:vertical-lr;">출입문</text>
</svg>`;

// ─── 4동 2층 ───
const b4_2f = `<svg viewBox="0 0 820 260" xmlns="http://www.w3.org/2000/svg">
  <!-- Left block: 교무실 -->
  <rect class="fp-wall" x="4" y="4" width="400" height="252" rx="6"/>
  ${R(14,14,120,252,'fp-room-yellow')} ${W('교무실',74,140,'fp-txt')}
  ${R(146,14,80,80,'fp-room-cream')} ${W('자료제작',186,54,'fp-txt-xs')}
  ${MEN(236,14)}
  ${STAIR(294,14,50,56)}
  ${R(146,160,80,90,'fp-room-cream')} ${W('교감실',186,205,'fp-txt-sm')}
  ${WOMEN(236,160)}
  <!-- 창고 -->
  ${R(310,160,80,90,'fp-room-cream')} ${W('창고',350,205,'fp-txt-sm')}
  <!-- 출입문 middle -->
  <rect x="396" y="118" width="8" height="24" rx="2" fill="#aaa"/>
  ${FIRE(282,90)}
  <!-- Right block -->
  <rect class="fp-wall" x="434" y="4" width="382" height="252" rx="6"/>
  ${STAIR(436,10,50,56)} ${WOMEN(494,14)}
  ${R(544,14,120,116,'fp-room-green')} ${W('소셜라운지',604,60,'fp-txt-xs')} ${W('(탈의실)',604,76,'fp-txt-xs')}
  ${R(672,14,140,116,'fp-room-green')} ${W('423호',742,54,'fp-txt-sm')} ${W('강의실',742,72,'fp-txt-sm')}
  ${STAIR(436,130,50,56)}
  ${R(544,134,120,114,'fp-room-green')} ${W('자료실',604,191,'fp-txt-sm')}
  ${R(672,134,70,114,'fp-room-green')} ${W('글로벌',707,185,'fp-txt-xs')} ${W('라운지',707,200,'fp-txt-xs')}
  ${R(748,134,38,114,'fp-room-green')} ${W('421호',767,180,'fp-txt-xs')} ${W('상담실',767,196,'fp-txt-xs')}
  ${R(790,134,22,114,'fp-room-green')} ${W('422호',801,185,'fp-txt-xs')}
</svg>`;

// ─── 4동 3층 ───
const b4_3f = `<svg viewBox="0 0 820 240" xmlns="http://www.w3.org/2000/svg">
  <!-- Left block -->
  <rect class="fp-wall" x="4" y="4" width="400" height="232" rx="6"/>
  ${R(14,14,140,104,'fp-room-cream')} ${W('학습도움실',84,54,'fp-txt-xs')} ${W('3-9',84,72,'fp-txt-sm')}
  ${WOMEN(162,14)} ${MEN(202,14)}
  ${STAIR(290,14,50,56)}
  ${R(14,124,140,104,'fp-room-cream')} ${W('학습도움실',84,164,'fp-txt-xs')} ${W('2-9',84,182,'fp-txt-sm')}
  ${R(162,124,140,104,'fp-room-cream')} ${W('학습도움실',232,164,'fp-txt-xs')} ${W('1-9',232,182,'fp-txt-sm')}
  <!-- 창고 -->
  ${R(310,160,80,68,'fp-room-cream')} ${W('창고',350,194,'fp-txt-sm')}
  ${FIRE(286,100)}
  <!-- Right block -->
  <rect class="fp-wall" x="434" y="4" width="382" height="232" rx="6"/>
  ${STAIR(436,10,50,56)} ${MEN(494,14)}
  ${R(544,14,130,104,'fp-room-green')} ${W('435호 강의실',609,54,'fp-txt-xs')} ${W('(비주얼아트실)',609,70,'fp-txt-xs')}
  ${R(680,14,130,104,'fp-room-green')} ${W('434호 토의실',745,60,'fp-txt-sm')}
  ${STAIR(436,130,50,56)}
  ${R(544,124,190,104,'fp-room-green')} ${W('431호 중강당',639,164,'fp-txt-xs')} ${W('(연극실)',639,180,'fp-txt-xs')}
  ${R(740,124,76,104,'fp-room-green')} ${W('432호',778,160,'fp-txt-xs')} ${W('학습실',778,176,'fp-txt-xs')}
  ${R(820,124,0,104,'fp-room-green')}
  <!-- 433호 -->
  <rect class="fp-room-green" x="740" y="124" width="72" height="104" rx="3" stroke="#888" stroke-width="1.5"/>
  <text class="fp-txt-xs" x="776" y="185">433호</text>
</svg>`;

// ─── 4동 4층 (수학과) ───
const b4_4f = `<svg viewBox="0 0 820 240" xmlns="http://www.w3.org/2000/svg">
  <!-- Left block: 수학과 -->
  <rect class="fp-wall" x="4" y="4" width="400" height="232" rx="6"/>
  ${R(14,14,160,104,'fp-room-green')} ${W('수학교과1실',94,60,'fp-txt-sm')}
  ${WOMEN(184,14)} ${MEN(224,14)}
  ${R(280,14,100,104,'fp-room-cream')} ${W('수학과',330,50,'fp-txt-xs')} ${W('연구실',330,68,'fp-txt-xs')}
  ${STAIR(320,14,70,60)}
  ${R(14,124,160,104,'fp-room-green')} ${W('수학교과2실',94,176,'fp-txt-sm')}
  ${R(184,124,160,104,'fp-room-green')} ${W('수학교과3실',264,176,'fp-txt-sm')}
  ${FIRE(12,110)} ${FIRE(356,110)}
  <!-- 창고 -->
  ${R(356,160,38,68,'fp-room-cream')} ${W('창고',375,194,'fp-txt-xs')}
  <!-- Right: 옥상 -->
  <rect class="fp-wall" x="434" y="4" width="382" height="232" rx="6"/>
  <text style="font-family:'Nanum Myeongjo',serif;font-size:52px;font-weight:800;fill:#1a1a2e;" x="625" y="148" text-anchor="middle">옥상</text>
</svg>`;

// ─── 3동 1층 ───
const b3_1f = `<svg viewBox="0 0 820 260" xmlns="http://www.w3.org/2000/svg">
  <rect class="fp-wall" x="4" y="4" width="812" height="252" rx="6"/>
  <!-- top protrusions -->
  <rect class="fp-wall" x="150" y="4" width="160" height="78" rx="4"/>
  <rect class="fp-wall" x="430" y="4" width="160" height="78" rx="4"/>
  ${STAIR(152,10,50,56)} ${WOMEN(208,10)} ${MEN(208,44)}
  <!-- 출입문 -->
  <rect x="234" y="80" width="60" height="8" rx="2" fill="#aaa"/>
  <text x="264" y="88" class="fp-txt-xs" style="fill:#555;">출입문</text>
  ${STAIR(432,10,50,56)} ${MEN(490,44)}
  <rect x="590" y="80" width="60" height="8" rx="2" fill="#aaa"/>
  <text x="620" y="88" class="fp-txt-xs" style="fill:#555;">출입문</text>
  <!-- right protrusion top: 311호 미술실 -->
  <rect class="fp-wall" x="620" y="4" width="196" height="78" rx="4"/>
  ${R(622,6,40,68,'fp-room-cream')} ${W('방송실',642,40,'fp-txt-xs')}
  ${R(668,6,144,68,'fp-room-green')} ${W('311호 미술실',740,34,'fp-txt-xs')} ${W('(비주얼아트실)',740,52,'fp-txt-xs')}
  ${STAIR(754,80,60,20)}
  <line x1="4" y1="98" x2="816" y2="98" stroke="#ccc" stroke-width="1" stroke-dasharray="6,3"/>
  <!-- 보건실 left -->
  ${R(14,100,130,150,'fp-room-green')} ${W('보건실',79,175,'fp-txt')}
  <!-- 출입문 bottom-left -->
  <rect x="14" y="246" width="60" height="8" rx="2" fill="#aaa"/>
  ${R(156,114,130,130)} ${W('컴퓨터1실',221,179,'fp-txt-sm')}
  ${R(294,114,60,130,'fp-room-cream')} ${W('정보',324,172,'fp-txt-xs')} ${W('연구실',324,188,'fp-txt-xs')}
  ${R(362,114,130,130,'fp-room-cream')} ${W('진로교육',427,170,'fp-txt-xs')} ${W('전용교실',427,186,'fp-txt-xs')}
  ${R(500,114,58,130,'fp-room-cream')} ${W('진로진학',529,170,'fp-txt-xs')} ${W('상담실',529,188,'fp-txt-xs')}
  ${R(566,114,132,130,'fp-room-cream')} ${W('312호 무용실',632,170,'fp-txt-xs')} ${W('(연극실)',632,188,'fp-txt-xs')}
  ${STAIR(730,114,80,56)}
  ${FIRE(152,104)} ${FIRE(358,104)} ${FIRE(496,104)} ${FIRE(562,104)} ${FIRE(700,80)}
</svg>`;

// ─── 3동 2층 ───
const b3_2f = `<svg viewBox="0 0 820 260" xmlns="http://www.w3.org/2000/svg">
  <rect class="fp-wall" x="4" y="4" width="812" height="252" rx="6"/>
  <rect class="fp-wall" x="150" y="4" width="160" height="78" rx="4"/>
  <rect class="fp-wall" x="430" y="4" width="160" height="78" rx="4"/>
  ${STAIR(152,10,50,56)} ${WOMEN(208,10)}
  ${STAIR(432,10,50,56)} ${MEN(490,10)}
  <!-- top center: 321호 대강의실 -->
  <rect class="fp-wall" x="270" y="4" width="156" height="78" rx="4"/>
  ${R(272,6,152,70,'fp-room-green')} ${W('321호',348,36,'fp-txt-sm')} ${W('대강의실',348,52,'fp-txt-sm')}
  <line x1="4" y1="98" x2="816" y2="98" stroke="#ccc" stroke-width="1" stroke-dasharray="6,3"/>
  ${R(14,100,120,150,'fp-room-green')} ${W('기술가정실',74,175,'fp-txt-sm')}
  ${R(146,114,70,130,'fp-room-cream')} ${W('여교직원',181,165,'fp-txt-xs')} ${W('휴게실',181,181,'fp-txt-xs')}
  ${R(224,114,120,130)} ${W('영어교과',284,175,'fp-txt-xs')} ${W('1실',284,191,'fp-txt-xs')}
  ${R(352,114,120,130)} ${W('영어교과',412,175,'fp-txt-xs')} ${W('2실',412,191,'fp-txt-xs')}
  ${R(480,114,120,130)} ${W('영어교과',540,175,'fp-txt-xs')} ${W('3실',540,191,'fp-txt-xs')}
  ${R(608,114,132,130,'fp-room-cream')} ${W('학생안전',674,168,'fp-txt-xs')} ${W('교육부실',674,184,'fp-txt-xs')}
  ${STAIR(740,114,70,56)}
  ${FIRE(220,104)} ${FIRE(476,104)}
</svg>`;

// ─── 3동 3층 ───
const b3_3f = `<svg viewBox="0 0 820 260" xmlns="http://www.w3.org/2000/svg">
  <rect class="fp-wall" x="4" y="4" width="812" height="252" rx="6"/>
  <rect class="fp-wall" x="150" y="4" width="520" height="90" rx="4"/>
  ${STAIR(152,10,50,70)}
  ${WOMEN(210,10)}
  <!-- top center rooms -->
  ${R(252,8,76,70,'fp-room-cream')} ${W('하닉콜로키움',290,43,'fp-txt-xs')}
  ${R(334,8,120,70,'fp-room-green')} ${W('꿈세움라운지',394,43,'fp-txt-xs')}
  <!-- 333·334호 -->
  ${R(460,8,76,34,'fp-room-cream')} ${W('333호 학습실',498,25,'fp-txt-xs')}
  ${R(460,46,76,32,'fp-room-cream')} ${W('334호 학습실',498,62,'fp-txt-xs')}
  ${MEN(542,10)}
  ${STAIR(592,10,70,70)}
  <line x1="4" y1="98" x2="816" y2="98" stroke="#ccc" stroke-width="1" stroke-dasharray="6,3"/>
  ${R(14,100,100,150,'fp-room-yellow')} ${W('3학년',64,168,'fp-txt-xs')} ${W('교무실',64,184,'fp-txt-xs')}
  ${R(122,114,120,130)} ${W('3자습실',182,179,'fp-txt-sm')}
  ${R(250,114,120,130)} ${W('3-1',310,179,'fp-txt')}
  ${R(378,114,120,130)} ${W('3-2',438,179,'fp-txt')}
  ${R(506,114,120,130)} ${W('3-3',566,179,'fp-txt')}
  ${R(634,114,120,130)} ${W('3-4',694,179,'fp-txt')}
  ${STAIR(750,114,60,60)}
  ${FIRE(246,104)} ${FIRE(374,104)} ${FIRE(502,104)} ${FIRE(630,104)}
</svg>`;

// ─── 3동 4층 ───
const b3_4f = `<svg viewBox="0 0 820 260" xmlns="http://www.w3.org/2000/svg">
  <rect class="fp-wall" x="4" y="4" width="812" height="252" rx="6"/>
  <rect class="fp-wall" x="150" y="4" width="520" height="90" rx="4"/>
  ${STAIR(152,10,50,70)}
  ${WOMEN(210,10)}
  <!-- 342·345호 -->
  ${R(252,8,76,34,'fp-room-cream')} ${W('342호 학습실',290,25,'fp-txt-xs')}
  ${R(252,46,76,32,'fp-room-cream')} ${W('345호 학습실',290,62,'fp-txt-xs')}
  ${R(334,8,120,70,'fp-room-green')} ${W('꿈세움라운지',394,43,'fp-txt-xs')}
  ${R(460,8,76,34,'fp-room-cream')} ${W('343호 학습실',498,25,'fp-txt-xs')}
  ${R(460,46,76,32,'fp-room-cream')} ${W('344호 학습실',498,62,'fp-txt-xs')}
  ${MEN(542,10)}
  ${STAIR(592,10,70,70)}
  <line x1="4" y1="98" x2="816" y2="98" stroke="#ccc" stroke-width="1" stroke-dasharray="6,3"/>
  ${R(14,100,100,150,'fp-room-green')} ${W('심자실',64,175,'fp-txt-sm')}
  ${R(122,114,120,130)} ${W('4자습실',182,179,'fp-txt-sm')}
  ${R(250,114,120,130)} ${W('3-5',310,179,'fp-txt')}
  ${R(378,114,120,130)} ${W('3-6',438,179,'fp-txt')}
  ${R(506,114,120,130)} ${W('3-7',566,179,'fp-txt')}
  ${R(634,114,120,130)} ${W('3-8',694,179,'fp-txt')}
  ${STAIR(750,114,60,60)}
  ${FIRE(246,104)} ${FIRE(374,104)} ${FIRE(502,104)} ${FIRE(630,104)}
</svg>`;

// ─── 기계실/전기실 ───
const b4_mech = `<svg viewBox="0 0 600 180" xmlns="http://www.w3.org/2000/svg">
  <rect class="fp-wall" x="4" y="4" width="592" height="172" rx="6"/>
  ${STAIR(14,60,60,60)}
  ${R(90,14,160,80,'fp-room-cream')} ${W('전기실',170,54,'fp-txt-sm')}
  <text style="font-family:'Nanum Myeongjo',serif;font-size:36px;font-weight:800;fill:#1a1a2e;" x="420" y="100" text-anchor="middle">기계실</text>
  ${STAIR(524,60,60,60)}
</svg>`;

// ════════════════════════════════════════════
//  ZONE DATA
// ════════════════════════════════════════════
const ZONES = {
  field:{name:'운동장',eng:'ATHLETIC FIELD',badge:'야외 시설',color:'#4caf50',
    desc:'축구장, 농구코트, 미니맵으로 구성된 복합 운동시설입니다.',
    strip:[['시설','축구장 · 농구코트'],['트랙','붉은 우레탄'],['조명','야간조명 완비'],['위치','캠퍼스 좌측']],
    floors:[{label:'전체',desc:'운동장 전체는 축구장, 농구코트, 미니맵 구역으로 나뉩니다.',svg:null,rooms:['⚽ 축구장','🏀 농구코트','🗺 미니맵']}],
    photos:['전경','축구장','농구코트','미니맵']},
  hall:{name:'강당 / 급식실',eng:'AUDITORIUM & CAFETERIA',badge:'복합 시설',color:'#1565c0',
    desc:'1층 급식실과 2층 강당으로 구성된 복합 건물입니다.',
    strip:[['위치','캠퍼스 좌하단'],['급식 운영','12:00~13:30'],['강당 수용','추가 예정'],['냉난방','완비']],
    floors:[
      {label:'1층 — 급식실',desc:'배식구역, 식사공간, 조리실로 구성됩니다.',svg:null,rooms:['🍱 배식구역','🪑 식사공간','🧑‍🍳 조리실','↩ 식기반납']},
      {label:'2층 — 강당',desc:'전교생 행사, 졸업식, 공연 등에 사용됩니다.',svg:null,rooms:['🎭 메인홀','🎤 무대','💺 관람석','🚪 로비']}],
    photos:['강당','무대','관람석','급식배식대']},
  b5:{name:'5동',eng:'BUILDING 5',badge:'교내 건물',color:'#c0392b',
    desc:'체력단련실, 탈의실, 체육과 연구실이 있는 2층 건물입니다.',
    strip:[['동 번호','5동'],['층수','2층'],['지붕','빨간색'],['위치','중앙 하단']],
    floors:[
      {label:'1층',desc:'여탈의실, 남탈의실, 체육비품실이 있습니다.',svg:b5_1f,rooms:['👔 여탈의실','👔 남탈의실','📦 체육비품실']},
      {label:'2층',desc:'교육공무직휴게실, 탈의실, 체력단련실, 체육과 연구실이 있습니다.',svg:b5_2f,rooms:['🏢 교육공무직휴게실','👔 여자탈의실','👔 남자탈의실','👔 남교사휴게실','💪 체력단련실','📚 체육과 연구실']}],
    photos:['정면','체력단련실','탈의실','복도']},
  b3:{name:'3동',eng:'BUILDING 3',badge:'교내 건물',color:'#5c7bb5',
    desc:'보건실, 교과교실, 강의실 등 다양한 시설이 있는 4층 건물입니다.',
    strip:[['동 번호','3동'],['층수','4층'],['지붕','파란색'],['위치','중앙 우측']],
    floors:[
      {label:'1층',desc:'보건실, 컴퓨터1실, 방송실, 진로교육 전용교실, 312호 무용실(연극실)이 있습니다.',svg:b3_1f,rooms:['🏥 보건실','💻 컴퓨터1실','📡 방송실','🎯 진로교육 전용교실','🎨 311호 미술실','💃 312호 무용실(연극실)']},
      {label:'2층',desc:'321호 대강의실, 기술가정실, 영어교과 1·2·3실, 학생안전 교육부실이 있습니다.',svg:b3_2f,rooms:['🏛 321호 대강의실','⚙️ 기술가정실','🔤 영어교과 1·2·3실','📋 학생안전 교육부실']},
      {label:'3층',desc:'3학년 교무실, 3자습실, 3-1~3-4 교실, 꿈세움라운지가 있습니다.',svg:b3_3f,rooms:['🏫 3학년 교무실','📖 3자습실','🏛 3-1','🏛 3-2','🏛 3-3','🏛 3-4','🌱 꿈세움라운지']},
      {label:'4층',desc:'심자실, 4자습실, 3-5~3-8 교실, 꿈세움라운지가 있습니다.',svg:b3_4f,rooms:['⛪ 심자실','📖 4자습실','🏛 3-5','🏛 3-6','🏛 3-7','🏛 3-8','🌱 꿈세움라운지']}],
    photos:['정면','교실','복도','계단']},
  b4:{name:'4동 / 도서관',eng:'BUILDING 4 & LIBRARY',badge:'교내 건물',color:'#2e7d32',
    desc:'도서관, 수학과, 교무실, 시청각실 등 다양한 시설이 있는 건물입니다.',
    strip:[['동 번호','4동'],['층수','4층 + 지하'],['특징','도서관 포함'],['위치','우측 상단']],
    floors:[
      {label:'지하',desc:'시청각실이 있습니다.',svg:b4_b1,rooms:['🎬 시청각실']},
      {label:'1층',desc:'인쇄실, 행정실, 당직실, 교장실, 학부모 회의실, 도서관이 있습니다.',svg:b4_1f,rooms:['🖨 인쇄실','🏛 행정실','🛏 당직실','👑 교장실','👨‍👩‍👧 학부모회의실','📚 도서관']},
      {label:'2층',desc:'교무실, 교감실, 소셜라운지(탈의실), 글로벌라운지, 421·422·423호가 있습니다.',svg:b4_2f,rooms:['🏫 교무실','👩‍💼 교감실','🛁 소셜라운지','🌍 글로벌라운지','📋 421호 상담실','💻 422호 온라인학습실','🎤 423호 강의실']},
      {label:'3층',desc:'학습도움실 1-9·2-9·3-9, 431~435호가 있습니다.',svg:b4_3f,rooms:['📖 학습도움실 3-9','📖 학습도움실 2-9','📖 학습도움실 1-9','🎨 435호(비주얼아트실)','💬 434호 토의실','🎭 431호 중강당(연극실)','📚 432·433호 학습실']},
      {label:'4층',desc:'수학교과 1·2·3실, 수학과 연구실, 옥상이 있습니다.',svg:b4_4f,rooms:['📐 수학교과1실','📐 수학교과2실','📐 수학교과3실','🔬 수학과 연구실','☀️ 옥상']},
      {label:'기계실',desc:'기계실과 전기실이 있습니다.',svg:b4_mech,rooms:['⚙️ 기계실','⚡ 전기실']}],
    photos:['정면','도서관','수학교과실','교무실']},
  b2:{name:'2동',eng:'BUILDING 2',badge:'교내 건물',color:'#5c7bb5',
    desc:'4층 건물입니다. 상세 구조도를 준비 중입니다.',
    strip:[['동 번호','2동'],['층수','4층'],['지붕','파란색'],['위치','우측 중하단']],
    floors:[
      {label:'1층',desc:'2동 1층 정보입니다.',svg:null,rooms:[]},
      {label:'2층',desc:'2동 2층 정보입니다.',svg:null,rooms:[]},
      {label:'3층',desc:'2동 3층 정보입니다.',svg:null,rooms:[]},
      {label:'4층',desc:'2동 4층 정보입니다.',svg:null,rooms:[]}],
    photos:['정면','내부','복도','계단']},
  b1:{name:'1동',eng:'BUILDING 1',badge:'교내 건물',color:'#0d2a5e',
    desc:'정독실, 과학실, 음악실, 교실 등 다양한 시설이 있는 4층 건물입니다.',
    strip:[['동 번호','1동'],['층수','4층'],['위치','캠퍼스 맨 우측'],['특징','가장 큰 건물']],
    floors:[
      {label:'1층',desc:'정독실, 제1·2과학실, 과학자료실, 음악과 연구실, 음악실, Wee클래스가 있습니다.',svg:b1_1f,rooms:['📖 정독실','🔬 제1·2과학실','📋 과학자료실','🎵 음악실','💙 Wee클래스']},
      {label:'2층',desc:'하니꿈틀 공작소, 1학년 교무실, 1-1~1-4 교실, 꿈키움 라운지가 있습니다.',svg:b1_2f,rooms:['🛠 하니꿈틀 공작소','🏫 1학년 교무실','🏛 1-1','🏛 1-2','🏛 1-3','🏛 1-4','🌱 꿈키움 라운지']},
      {label:'3층',desc:'2학년 교무실, 1-5~1-8, 2-7~2-8 교실, 꿈키움 라운지가 있습니다.',svg:b1_3f,rooms:['🏫 2학년 교무실','🏛 1-5','🏛 1-6','🏛 1-7','🏛 1-8','🏛 2-7','🏛 2-8','🌱 꿈키움 라운지']},
      {label:'4층',desc:'2-1~2-6 교실, 큰들마 콜로키움이 있습니다.',svg:b1_4f,rooms:['🏛 2-1','🏛 2-2','🏛 2-3','🏛 2-4','🏛 2-5','🏛 2-6','🎪 큰들마 콜로키움']}],
    photos:['정면','교실','정독실','음악실']}
};

// ════════════════════════════════════════════
//  APP LOGIC
// ════════════════════════════════════════════
function tick(){const n=new Date();document.getElementById('clock').textContent=[n.getHours(),n.getMinutes(),n.getSeconds()].map(v=>String(v).padStart(2,'0')).join(':');}
setInterval(tick,1000);tick();

// chips
const cb=document.getElementById('chip-bar');
Object.entries(ZONES).forEach(([id,z])=>{
  const c=document.createElement('div');c.className='chip';
  c.innerHTML=`<span class="chip-dot" style="background:${z.color}"></span>${z.name}`;
  c.onclick=()=>sel(id);cb.appendChild(c);
});

// blist
const bl=document.getElementById('blist');
Object.entries(ZONES).forEach(([id,z])=>{
  const item=document.createElement('div');item.className='bi';item.id=`bi-${id}`;
  item.innerHTML=`<span class="bi-dot" style="background:${z.color}"></span><span class="bi-name">${z.name}</span>`;
  item.onclick=()=>sel(id);bl.appendChild(item);
  const fw=document.createElement('div');fw.className='fl-list';fw.id=`fl-${id}`;
  z.floors.forEach((f,i)=>{
    const fb=document.createElement('button');fb.className='fl-btn';fb.id=`fb-${id}-${i}`;fb.textContent=f.label;
    fb.onclick=(e)=>{e.stopPropagation();selFloor(id,i);};fw.appendChild(fb);
  });
  bl.appendChild(fw);
});

let CZ=null,CF=0;

function sel(id){
  const z=ZONES[id];if(!z)return;
  document.getElementById('vd').classList.add('hidden');
  document.getElementById('vdet').classList.add('visible');
  document.getElementById('hdr-back').style.display='';
  document.querySelectorAll('.bi').forEach(e=>e.classList.remove('active'));
  document.getElementById(`bi-${id}`).classList.add('active');
  Object.keys(ZONES).forEach(zid=>{
    const fl=document.getElementById(`fl-${zid}`);
    if(fl)fl.className='fl-list'+(zid===id?' open':'');
  });
  if(CZ!==id)CF=0;
  CZ=id;
  document.getElementById('hbadge').textContent=z.badge;
  document.getElementById('htitle').textContent=z.name;
  document.getElementById('hsub').textContent=z.eng;
  document.getElementById('hdesc').textContent=z.desc;
  document.getElementById('istrip').innerHTML=z.strip.map(([k,v])=>
    `<div class="is-it"><div class="is-lbl">${k}</div><div class="is-val">${v}</div></div>`).join('');
  document.getElementById('ilist').innerHTML=z.strip.map(([k,v])=>
    `<div class="info-row"><div class="info-row-k">${k}</div><div class="info-row-v">${v}</div></div>`).join('');
  renderFloor(id,CF);
  renderPhotos(z);
  document.getElementById('center-main').scrollTop=0;
}

function selFloor(id,i){
  CF=i;renderFloor(id,i);
  document.getElementById('plan-wrap').scrollIntoView({behavior:'smooth',block:'nearest'});
}

function renderFloor(id,i){
  const z=ZONES[id];const f=z.floors[i];
  document.querySelectorAll('.fl-btn').forEach(b=>b.classList.remove('active'));
  const fb=document.getElementById(`fb-${id}-${i}`);if(fb)fb.classList.add('active');
  document.getElementById('plan-title').textContent=`구조도 — ${f.label}`;
  document.getElementById('plan-lbl').textContent=`${z.name} ${f.label}`;
  document.getElementById('ftabs').innerHTML=z.floors.map((fl,j)=>
    `<button class="ftab${j===i?' on':''}" onclick="selFloor('${id}',${j})">${fl.label}</button>`).join('');
  // plan SVG
  const area=document.getElementById('plan-svg-area');
  if(f.svg){
    area.innerHTML=f.svg;
  } else {
    // rooms as tags fallback
    const roomHtml=f.rooms.length
      ?f.rooms.map(r=>`<div style="background:var(--accent-light);border:1.5px solid var(--border);border-radius:5px;padding:8px 12px;font-size:10px;color:var(--navy);font-weight:500;display:inline-flex;align-items:center;gap:5px;">${r}</div>`).join('')
      :`<div style="color:var(--text-light);font-size:12px;padding:16px;">구조도 준비 중입니다.</div>`;
    area.innerHTML=`<div style="padding:16px;display:flex;flex-wrap:wrap;gap:7px;">${roomHtml}</div>`;
  }
  // right col
  document.getElementById('rdesc-t').textContent=`${z.name} ${f.label}`;
  document.getElementById('rdesc-b').textContent=f.desc;
}

function renderPhotos(z){
  document.getElementById('pgrid').innerHTML=z.photos.map(label=>
    `<div class="ph-card" onclick="openLBPhoto('${label}','${z.color}','${z.name}')">
      <div class="ph-img"><svg viewBox="0 0 160 120" xmlns="http://www.w3.org/2000/svg">
        <rect width="160" height="120" fill="#eef1f8"/>
        <rect x="8" y="8" width="144" height="104" rx="4" fill="#e2e8f4"/>
        <text x="80" y="50" font-size="24" text-anchor="middle" opacity=".2">📷</text>
        <text x="80" y="72" fill="#8a9ab5" font-size="9" text-anchor="middle" font-family="Noto Sans KR,sans-serif">사진 업로드 예정</text>
        <text x="80" y="86" fill="${z.color}" font-size="8" text-anchor="middle" font-family="Noto Sans KR,sans-serif" opacity=".6">${label}</text>
        <rect x="8" y="8" width="144" height="104" rx="4" fill="none" stroke="#d0d8e8" stroke-width="1"/>
      </svg></div>
      <div class="ph-lbl">${label}</div>
    </div>`).join('');
}

let _lbSVG='',_lbCap='';
function openLBPlan(){
  if(!CZ)return;
  const z=ZONES[CZ];const f=z.floors[CF];
  _lbCap=`${z.name} — ${f.label} 구조도`;
  if(f.svg){
    document.getElementById('lb-content').innerHTML=f.svg;
  } else {
    document.getElementById('lb-content').innerHTML=
      `<div style="padding:40px;color:var(--text-light);font-size:14px;">구조도 준비 중입니다.</div>`;
  }
  document.getElementById('lb-cap').textContent=_lbCap;
  document.getElementById('lb').classList.add('open');
}
function openLBPhoto(label,color,zoneName){
  document.getElementById('lb-content').innerHTML=
    `<svg viewBox="0 0 600 400" xmlns="http://www.w3.org/2000/svg" style="width:min(600px,85vw);">
      <rect width="600" height="400" fill="#eef1f8"/>
      <rect x="20" y="20" width="560" height="360" rx="8" fill="#e2e8f4"/>
      <text x="300" y="175" font-size="52" text-anchor="middle" opacity=".18">📷</text>
      <text x="300" y="218" fill="#8a9ab5" font-size="16" text-anchor="middle" font-family="Noto Sans KR,sans-serif">사진 업로드 예정</text>
      <text x="300" y="244" fill="${color}" font-size="13" text-anchor="middle" font-family="Noto Sans KR,sans-serif" opacity=".7">${label}</text>
    </svg>`;
  document.getElementById('lb-cap').textContent=`${zoneName} — ${label}`;
  document.getElementById('lb').classList.add('open');
}
function closeLB(){document.getElementById('lb').classList.remove('open');}
function lbClick(e){if(e.target===document.getElementById('lb'))closeLB();}

function goHome(){
  document.getElementById('vd').classList.remove('hidden');
  document.getElementById('vdet').classList.remove('visible');
  document.getElementById('hdr-back').style.display='none';
  document.querySelectorAll('.bi').forEach(e=>e.classList.remove('active'));
  Object.keys(ZONES).forEach(id=>{const fl=document.getElementById(`fl-${id}`);if(fl)fl.className='fl-list';});
  CZ=null;
}

// Default view zoom/pan
let dvS=1,dvX=0,dvY=0,dvDrag=false,dvL=null;
const dvOuter=document.getElementById('dv-outer');
const dvZm=document.getElementById('dv-zoom');
function dvApply(){dvZm.style.transform=`translate(${dvX}px,${dvY}px) scale(${dvS})`;}
function dvZ(f,cx,cy){
  const r=dvOuter.getBoundingClientRect();
  cx=cx??r.width/2;cy=cy??r.height/2;
  const ns=Math.max(.4,Math.min(6,dvS*f));
  dvX=cx-(cx-dvX)*(ns/dvS);dvY=cy-(cy-dvY)*(ns/dvS);dvS=ns;dvApply();
}
function dvR(){dvS=1;dvX=0;dvY=0;dvApply();}
dvOuter.addEventListener('wheel',e=>{
  e.preventDefault();const r=dvOuter.getBoundingClientRect();
  dvZ(e.deltaY<0?1.12:.89,e.clientX-r.left,e.clientY-r.top);
},{passive:false});
dvOuter.addEventListener('mousedown',e=>{
  if(e.target.closest('.dz,.zb'))return;
  dvDrag=true;dvL={x:e.clientX,y:e.clientY};e.preventDefault();
});
window.addEventListener('mousemove',e=>{
  if(!dvDrag)return;
  dvX+=e.clientX-dvL.x;dvY+=e.clientY-dvL.y;dvL={x:e.clientX,y:e.clientY};dvApply();
});
window.addEventListener('mouseup',()=>{dvDrag=false;});

function fitMap(){
  const bar=document.querySelector('.map-bar');
  const chip=document.querySelector('.chip-bar');
  if(!bar||!chip)return;
  const h=window.innerHeight-56-bar.offsetHeight-chip.offsetHeight;
  dvOuter.style.height=Math.max(200,h)+'px';
}
window.addEventListener('resize',fitMap);fitMap();
</script>
</body>
</html>
