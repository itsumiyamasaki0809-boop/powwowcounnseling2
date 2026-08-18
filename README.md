<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>POWWOW - パウワウ</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;1,300;1,400&family=Noto+Serif+JP:wght@300;400;500&family=Josefin+Sans:wght@200;300;400&display=swap" rel="stylesheet">
<style>
:root {
--brand-pink: #E91E63;
--brand-pink-dark: #C2185B;
--gold-light: #F48FB1;
--gold-pale: #FCE4EC;
--dark: #880E4F;
--cream: #FFF5F8;
--cream-dark: #F8E1E7;
--text-main: #4A041E;
--text-muted: #AD1457;
--base-font-size: 16px;
}

html { font-size: var(--base-font-size); }
html.font-small { --base-font-size: 14px; }
html.font-medium { --base-font-size: 16px; }
html.font-large { --base-font-size: 20px; }

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
background-color: var(--cream);
color: var(--text-main);
font-family: 'Noto Serif JP', serif;
min-height: 100vh;
overflow-x: hidden;
line-height: 1.6;
letter-spacing: 0.03em;
}

header {
background-color: var(--brand-pink-dark);
padding: 1rem 1.5rem;
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
position: sticky;
top: 0;
z-index: 100;
}

.logo {
font-family: 'Josefin Sans', sans-serif;
font-weight: 500;
font-size: 1.5rem;
letter-spacing: 0.25em;
color: #FFFFFF;
}

.logo-sub {
font-family: 'Josefin Sans', sans-serif;
font-weight: 300;
font-size: 0.625rem;
letter-spacing: 0.15em;
color: var(--gold-pale);
margin-top: 0.125rem;
}

.logo-img {
height: 2.25rem;
width: auto;
display: block;
}

.hero {
background-color: var(--brand-pink-dark);
padding: 3.75rem 1.5rem 3.125rem;
text-align: center;
position: relative;
overflow: hidden;
}

.hero::before {
content: '';
position: absolute;
inset: 0;
background: radial-gradient(ellipse 70% 60% at 50% 40%, rgba(255,255,255,0.15) 0%, transparent 70%);
pointer-events: none;
}

.hero-label {
font-family: 'Josefin Sans', sans-serif;
font-weight: 200;
font-size: 0.625rem;
letter-spacing: 0.45em;
color: var(--gold-light);
margin-bottom: 1.75rem;
display: flex;
align-items: center;
justify-content: center;
gap: 1rem;
}

.hero-label::before,
.hero-label::after {
content: '';
display: block;
width: 3.125rem;
height: 0.5px;
background: var(--gold-light);
opacity: 0.5;
}

.hero-title-jp {
font-family: 'Noto Serif JP', serif;
font-weight: 300;
font-size: clamp(1.5rem, 5vw, 2.25rem);
color: #FFFFFF;
line-height: 1.7;
margin-bottom: 1rem;
}

.hero-title-jp strong {
color: #FFEB3B;
font-weight: 500;
background: none;
}

.hero-subtitle {
font-family: 'Cormorant Garamond', serif;
font-style: italic;
font-weight: 300;
font-size: 0.875rem;
letter-spacing: 0.12em;
color: var(--gold-light);
opacity: 0.9;
margin-top: 1.5rem;
}

.section {
padding: 3.75rem 1.5rem;
max-width: 800px;
margin: 0 auto;
}

.section-title {
font-family: 'Noto Serif JP', serif;
font-size: clamp(1.25rem, 4vw, 1.5rem);
font-weight: 500;
color: var(--brand-pink-dark);
text-align: center;
margin-bottom: 2.5rem;
position: relative;
padding-bottom: 1rem;
}

.section-title::after {
content: '';
position: absolute;
bottom: 0;
left: 50%;
transform: translateX(-50%);
width: 2.5rem;
height: 1px;
background-color: var(--brand-pink);
}

.symptom-grid {
display: grid;
grid-template-columns: repeat(2, 1fr);
gap: 1rem;
margin-bottom: 1.5rem;
}

@media (min-width: 600px) {
.symptom-grid {
grid-template-columns: repeat(4, 1fr);
}
}

.symptom-card {
background: #fff;
border: 0.5px solid var(--gold-light);
border-radius: 8px;
padding: 2rem 0.75rem 1.5rem;
text-align: center;
position: relative;
box-shadow: 0 4px 10px rgba(233,30,99,0.05);
cursor: pointer;
user-select: none;
transition: transform 0.2s ease, box-shadow 0.2s ease, background 0.2s ease;
width: 100%;
font: inherit;
color: inherit;
}

.symptom-card:hover {
transform: translateY(-3px);
box-shadow: 0 8px 18px rgba(233,30,99,0.15);
}

.symptom-card.is-selected {
background: var(--gold-pale);
border-color: var(--brand-pink);
box-shadow: 0 6px 16px rgba(233,30,99,0.2);
}

.symptom-card.is-selected .symptom-check {
opacity: 1;
transform: scale(1);
}

.symptom-check {
position: absolute;
top: 0.5rem;
right: 0.5rem;
width: 1.25rem;
height: 1.25rem;
border-radius: 50%;
background: var(--brand-pink);
color: #fff;
font-size: 0.7rem;
display: flex;
align-items: center;
justify-content: center;
opacity: 0;
transform: scale(0.5);
transition: all 0.2s ease;
}

.symptom-hint {
text-align: center;
font-family: 'Noto Serif JP', serif;
font-weight: 300;
font-size: 0.75rem;
color: var(--text-muted);
margin-bottom: 1.25rem;
letter-spacing: 0.05em;
}

.ai-diagnosis-btn {
display: flex;
align-items: center;
justify-content: center;
gap: 0.5rem;
margin: 0 auto 2.5rem;
padding: 0.9rem 2.5rem;
background: linear-gradient(135deg, var(--brand-pink) 0%, var(--brand-pink-dark) 100%);
color: #FFFFFF;
border: none;
border-radius: 50px;
font-family: 'Noto Serif JP', serif;
font-weight: 500;
font-size: 1rem;
letter-spacing: 0.08em;
cursor: pointer;
box-shadow: 0 6px 16px rgba(233,30,99,0.3);
transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.ai-diagnosis-btn:hover {
transform: translateY(-2px);
box-shadow: 0 8px 20px rgba(233,30,99,0.4);
}

.ai-diagnosis-btn:active {
transform: translateY(0);
}

.ai-diagnosis-btn.is-shake {
animation: shakeBtn 0.4s;
}

@keyframes shakeBtn {
0%, 100% { transform: translateX(0); }
25% { transform: translateX(-6px); }
75% { transform: translateX(6px); }
}

.ai-diagnosis-icon {
font-size: 1.1rem;
}

.symptom-card::before {
content: '';
position: absolute;
top: 0; left: 50%;
transform: translateX(-50%);
width: 2.5rem;
height: 3px;
background: var(--brand-pink);
border-radius: 0 0 4px 4px;
}

.symptom-icon {
font-size: 2.25rem;
margin-bottom: 0.75rem;
display: block;
}

.symptom-text {
font-family: 'Noto Serif JP', serif;
font-weight: 400;
font-size: 0.8125rem;
color: var(--text-main);
}

.approach-block {
background-color: var(--brand-pink-dark);
border-radius: 12px;
padding: 2.5rem 2rem;
display: flex;
flex-direction: column;
gap: 2rem;
align-items: center;
position: relative;
overflow: hidden;
margin-top: 3.125rem;
max-height: 0;
padding-top: 0;
padding-bottom: 0;
margin-top: 0;
opacity: 0;
transition: max-height 0.6s ease, opacity 0.5s ease, padding 0.6s ease, margin 0.6s ease;
}

.approach-block.is-revealed {
max-height: 60rem;
padding: 2.5rem 2rem;
margin-top: 3.125rem;
opacity: 1;
}

.approach-block::before {
content: '';
position: absolute;
right: -2.5rem; top: -2.5rem;
width: 12.5rem; height: 12.5rem;
border-radius: 50%;
border: 1px solid rgba(255,255,255,0.1);
}

@media (min-width: 768px) {
.approach-block.is-revealed {
flex-direction: row;
justify-content: space-between;
padding: 3.125rem 3rem;
}
}

.approach-content {
flex: 1;
text-align: center;
position: relative;
z-index: 1;
}

@media (min-width: 768px) {
.approach-content {
text-align: left;
}
}

.approach-label {
font-family: 'Josefin Sans', sans-serif;
font-weight: 200;
font-size: 0.625rem;
letter-spacing: 0.4em;
color: var(--gold-light);
margin-bottom: 1.25rem;
}

.approach-title {
font-family: 'Noto Serif JP', serif;
font-weight: 300;
font-size: clamp(1.25rem, 4vw, 1.625rem);
color: #FFFFFF;
line-height: 1.8;
margin-bottom: 1.25rem;
}

.approach-title strong {
color: #FFEB3B;
font-weight: 500;
}

.approach-body {
font-family: 'Noto Serif JP', serif;
font-weight: 400;
font-size: 1.05rem;
color: rgba(255,255,255,0.9);
line-height: 1.9;
}

.approach-image-wrap {
flex-shrink: 0;
text-align: center;
position: relative;
z-index: 1;
background: rgba(0,0,0,0.1);
padding: 1rem;
border-radius: 100%;
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
}

.pelvis-illustration {
width: 11.5rem;
height: auto;
overflow: visible;
}

.pelvis-caption {
font-family: 'Noto Serif JP', serif;
font-weight: 300;
font-size: 0.625rem;
color: var(--gold-light);
margin-top: 0.5rem;
letter-spacing: 0.1em;
}

.reasons-section {
background-color: var(--cream-dark);
padding: 3.75rem 1.5rem;
}

.reasons-inner {
max-width: 800px;
margin: 0 auto;
}

.reason-item {
display: flex;
gap: 1.5rem;
align-items: flex-start;
padding: 2.25rem 0;
border-bottom: 0.5px solid rgba(233,30,99,0.2);
}

.reason-item:first-of-type {
border-top: 0.5px solid rgba(233,30,99,0.2);
}

@media (max-width: 600px) {
.reason-item {
flex-direction: column;
gap: 1rem;
padding: 1.5rem 0;
}
}

.reason-number {
font-family: 'Cormorant Garamond', serif;
font-weight: 400;
font-style: italic;
font-size: 3rem;
color: var(--brand-pink);
line-height: 1;
flex-shrink: 0;
}

.reason-title {
font-family: 'Noto Serif JP', serif;
font-size: 1.0625rem;
font-weight: 500;
color: var(--text-main);
margin-bottom: 0.75rem;
}

.reason-title em {
font-style: normal;
color: var(--brand-pink-dark);
background: linear-gradient(transparent 70%, var(--gold-light) 70%);
}

.reason-body {
font-family: 'Noto Serif JP', serif;
font-weight: 400;
font-size: 1rem;
line-height: 1.9;
color: var(--text-muted);
}

.reason-question {
font-family: 'Noto Serif JP', serif;
font-weight: 600;
font-size: 1.3rem;
color: #FFFFFF;
text-align: center;
margin: 2rem auto 0;
letter-spacing: 0.06em;
position: relative;
background: linear-gradient(135deg, var(--brand-pink) 0%, var(--brand-pink-dark) 100%);
padding: 0.9rem 1.5rem;
border-radius: 50px;
box-shadow: 0 6px 16px rgba(233,30,99,0.3);
max-width: 90%;
}

.gallery-container {
margin-top: 2rem;
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1rem;
}

.gallery-item {
background: #fff;
padding: 0.5rem;
border-radius: 8px;
box-shadow: 0 2px 8px rgba(0,0,0,0.05);
}

.gallery-item img {
width: 100%;
height: auto;
border-radius: 4px;
display: block;
}

.gallery-label {
font-size: 0.7rem;
text-align: center;
margin-top: 0.5rem;
color: var(--text-muted);
}

.ba-slider {
position: relative;
width: 100%;
aspect-ratio: 4 / 3;
overflow: hidden;
border-radius: 4px;
user-select: none;
touch-action: pan-y;
cursor: ew-resize;
background: #eee;
}

.ba-slider img {
position: absolute;
top: 0; left: 0;
width: 100%;
height: 100%;
object-fit: cover;
display: block;
pointer-events: none;
user-select: none;
-webkit-user-drag: none;
}

.ba-slider .ba-before-wrap {
position: absolute;
top: 0; left: 0;
height: 100%;
width: 50%;
overflow: hidden;
}

.ba-slider .ba-before-wrap img {
width: var(--ba-img-width, 100%);
max-width: none;
}

.ba-tag {
position: absolute;
top: 0.5rem;
font-family: 'Noto Serif JP', serif;
font-weight: 500;
font-size: 1rem;
letter-spacing: 0.05em;
color: #FFFFFF;
background: rgba(194,24,91,0.85);
padding: 0.3rem 0.85rem;
border-radius: 3px;
z-index: 3;
pointer-events: none;
}

.ba-tag.ba-tag-before { left: 0.5rem; }
.ba-tag.ba-tag-after { right: 0.5rem; }

.ba-handle {
position: absolute;
top: 0;
left: 50%;
height: 100%;
width: 2px;
background: #FFFFFF;
transform: translateX(-1px);
z-index: 4;
pointer-events: none;
box-shadow: 0 0 6px rgba(0,0,0,0.4);
}

.ba-caption {
font-family: 'Noto Serif JP', serif;
font-weight: 400;
font-size: 0.95rem;
text-align: center;
margin-top: 0.6rem;
color: var(--text-muted);
line-height: 1.7;
}

.ba-caption-label {
font-family: 'Noto Serif JP', serif;
font-weight: 400;
font-size: 0.8rem;
text-align: center;
margin-top: 0.6rem;
color: var(--text-muted);
}

.ba-caption-switch {
position: relative;
min-height: 3.2rem;
margin-top: 0.75rem;
}

.ba-caption-state {
position: absolute;
top: 0; left: 0;
width: 100%;
text-align: center;
font-family: 'Noto Serif JP', serif;
font-weight: 500;
font-size: 0.95rem;
line-height: 1.6;
opacity: 0;
transition: opacity 0.25s ease;
pointer-events: none;
}

.ba-caption-state.is-active {
opacity: 1;
}

.ba-caption-state.before-state {
color: #8A8A8A;
}

.ba-caption-state.after-state {
color: var(--brand-pink-dark);
}

.gallery-note {
font-family: 'Noto Serif JP', serif;
font-weight: 500;
font-size: 1.05rem;
line-height: 1.9;
color: var(--brand-pink-dark);
text-align: center;
margin-top: 2rem;
padding: 1.5rem 1.75rem;
background: var(--gold-pale);
border: 1px solid var(--brand-pink);
border-radius: 12px;
box-shadow: 0 4px 14px rgba(233,30,99,0.12);
}

@media (max-width: 600px) {
.gallery-container {
grid-template-columns: 1fr;
}
}

.care-chart-section {
padding: 3.75rem 1.5rem;
max-width: 900px;
margin: 0 auto;
}

.care-chart-lead {
font-family: 'Noto Serif JP', serif;
font-weight: 400;
font-size: 1rem;
line-height: 1.9;
color: var(--text-muted);
text-align: center;
margin-bottom: 2rem;
}

.care-chart-img-wrap {
background: #FFFFFF;
border-radius: 12px;
padding: 0.75rem;
box-shadow: 0 4px 15px rgba(233,30,99,0.08);
min-height: 200px;
display: flex;
align-items: center;
justify-content: center;
color: var(--text-muted);
font-size: 0.85rem;
}

.care-chart-img-wrap img {
width: 100%;
height: auto;
border-radius: 6px;
display: block;
}

.staff-banner {
margin: 0 auto;
max-width: 800px;
padding: 3.75rem 1.5rem;
}

.staff-banner-inner {
background: linear-gradient(160deg, var(--brand-pink-dark) 0%, var(--dark) 100%);
border-radius: 16px;
padding: 3rem 2rem;
text-align: center;
position: relative;
overflow: hidden;
box-shadow: 0 10px 30px rgba(136,14,79,0.25);
}

.staff-banner-inner::before {
content: '';
position: absolute;
right: -3rem; top: -3rem;
width: 14rem; height: 14rem;
border-radius: 50%;
border: 1px solid rgba(255,255,255,0.15);
}

.staff-banner-inner::after {
content: '';
position: absolute;
left: -2.5rem; bottom: -2.5rem;
width: 10rem; height: 10rem;
border-radius: 50%;
border: 1px solid rgba(255,255,255,0.1);
}

.staff-banner-eyebrow {
font-family: 'Josefin Sans', sans-serif;
font-weight: 300;
font-size: 0.7rem;
letter-spacing: 0.5em;
color: #FFEB3B;
margin-bottom: 1.25rem;
position: relative;
z-index: 1;
}

.staff-banner-text {
font-family: 'Noto Serif JP', serif;
font-weight: 500;
font-size: clamp(1.05rem, 3.2vw, 1.375rem);
color: #FFFFFF;
letter-spacing: 0.05em;
line-height: 1.9;
text-align: center;
position: relative;
z-index: 1;
}

.staff-banner-text .accent {
color: #FFEB3B;
}

.staff-banner-text .sub {
display: block;
font-size: 0.75em;
font-weight: 300;
opacity: 0.85;
margin: 0.5rem 0 1rem;
}

footer {
background-color: var(--dark);
padding: 3.75rem 1.5rem 3.125rem;
text-align: center;
color: #FFFFFF;
}

.footer-logo-img {
height: 1.75rem;
width: auto;
margin: 0 auto 0.75rem;
display: block;
}

.footer-tagline {
font-family: 'Noto Serif JP', serif;
font-weight: 300;
font-size: 0.625rem;
color: var(--gold-light);
letter-spacing: 0.1em;
}

.font-control {
position: fixed;
bottom: 1.5rem;
right: 1.5rem;
background: #FFFFFF;
border: 1px solid var(--brand-pink);
border-radius: 50px;
padding: 0.5rem;
display: flex;
gap: 0.25rem;
box-shadow: 0 4px 15px rgba(136, 14, 79, 0.2);
z-index: 1000;
}

.font-control-btn {
border: none;
background: transparent;
width: 2.5rem;
height: 2.5rem;
border-radius: 50%;
font-family: 'Noto Serif JP', serif;
color: var(--text-muted);
cursor: pointer;
font-size: 0.75rem;
display: flex;
align-items: center;
justify-content: center;
transition: all 0.2s ease;
}

.font-control-btn.active {
background: var(--brand-pink);
color: #FFFFFF;
}

@media (max-width: 600px) {
.font-control {
bottom: 1rem;
right: 1rem;
padding: 0.35rem;
}
.font-control-btn {
width: 2.2rem;
height: 2.2rem;
}
}
</style>
</head>
<body class="font-medium">

<div class="font-control">
<button class="font-control-btn" data-size="small">小</button>
<button class="font-control-btn active" data-size="medium">中</button>
<button class="font-control-btn" data-size="large">大</button>
</div>

<header>
<div class="logo">POWWOW</div>
<div class="logo-sub">パウワウ</div>
</header>

<section class="hero">
<p class="hero-title-jp">首や肩こりはもちろん女性特有の<br><strong>「なんとなくしんどい」</strong>には<br>実は<strong>原因</strong>があります。</p>
</section>

<div class="section">
<h2 class="section-title">こんなお悩み、ありませんか？</h2>
<div class="symptom-grid" id="symptom-grid">
<button type="button" class="symptom-card" data-symptom>
<span class="symptom-check">✓</span>
<span class="symptom-icon">😴</span>
<p class="symptom-text">寝ても疲れが取れない<br>寝つけない・眠りが浅い</p>
</button>
<button type="button" class="symptom-card" data-symptom>
<span class="symptom-check">✓</span>
<span class="symptom-icon">😮‍💨</span>
<p class="symptom-text">朝からだるい<br>やる気が出ない</p>
</button>
<button type="button" class="symptom-card" data-symptom>
<span class="symptom-check">✓</span>
<span class="symptom-icon">😤</span>
<p class="symptom-text">イライラしやすい<br>気分が沈みやすい</p>
</button>
<button type="button" class="symptom-card" data-symptom>
<span class="symptom-check">✓</span>
<span class="symptom-icon">🌡</span>
<p class="symptom-text">足のむくみ・<br>冷え・便秘がち</p>
</button>
</div>
<p class="symptom-hint" id="symptom-hint">気になるものをすべてタップしてから、下のボタンを押してください👆</p>
<button type="button" class="ai-diagnosis-btn" id="ai-diagnosis-btn">
<span class="ai-diagnosis-icon">🩺</span>診断する
</button>

<div class="approach-block" id="approach-block">
<div class="approach-content">
<h3 class="approach-title" id="approach-title">
<strong>仙骨の歪み度</strong><strong id="diagnosis-percent">0</strong>％
</h3>
<p class="approach-body" id="diagnosis-message">
骨盤の中心にある仙骨を整え、自律神経やホルモンバランスにアプローチ。<br>
身体の軸が整うと、心も軽くなります。
</p>
</div>
<div class="approach-image-wrap">
<svg class="pelvis-illustration" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
<path d="M55 85 C55 57, 80 49, 100 49 C120 49, 145 57, 145 85 C145 123, 120 145, 100 145 C80 145, 55 123, 55 85" stroke="#FFFFFF" stroke-width="1.2" fill="none" opacity="0.35"/>
<path d="M100 15 L100 95" stroke="#FFEB3B" stroke-width="3" stroke-linecap="round">
<animate attributeName="opacity" values="0.4;1;0.4" dur="3s" repeatCount="indefinite" />
</path>
<circle cx="100" cy="30" r="2" fill="#FFEB3B" />
<circle cx="100" cy="50" r="2" fill="#FFEB3B" />
<circle cx="100" cy="70" r="2" fill="#FFEB3B" />
<path d="M85 95 L115 95 L100 133 Z" fill="#FFEB3B" fill-opacity="0.35" stroke="#FFEB3B" stroke-width="2"/>
<line x1="100" y1="32" x2="35" y2="95" stroke="#FFFFFF" stroke-width="0.8" opacity="0.6"/>
<circle cx="100" cy="32" r="1.8" fill="#FFFFFF"/>
<text x="32" y="88" font-family="'Noto Serif JP',serif" font-size="10" fill="#FFFFFF" text-anchor="end">自律神経の</text>
<text x="32" y="102" font-family="'Noto Serif JP',serif" font-size="10" fill="#FFFFFF" text-anchor="end">通り道</text>
<line x1="100" y1="113" x2="165" y2="95" stroke="#FFEB3B" stroke-width="0.8" opacity="0.8"/>
<circle cx="100" cy="113" r="1.8" fill="#FFEB3B"/>
<text x="168" y="88" font-family="'Noto Serif JP',serif" font-weight="500" font-size="11" fill="#FFEB3B">仙骨</text>
<text x="168" y="103" font-family="'Noto Serif JP',serif" font-size="9" fill="#FFFFFF" opacity="0.85">骨格の土台</text>
</svg>
</div>
</div>
</div>

<div class="reasons-section">
<div class="reasons-inner">
<h2 class="section-title">パウワウ独自の「仙骨ケア」について</h2>
<p style="text-align:center; font-family:'Noto Serif JP',serif; font-weight:400; font-size:1rem; line-height:1.9; color:var(--text-muted); margin-bottom:2.5rem;">
パウワウの独自技術「サクラムバランステクニック®」で、骨盤の中心にある仙骨にアプローチ。ただほぐすだけではなく、身体全体のバランスを整えます。
</p>

<div class="reason-item">
<div class="reason-number">1</div>
<div>
<h3 class="reason-title"><em>女性特有のお悩み</em>を改善</h3>
<p class="reason-body">冷え・むくみ・生理など、女性特有のお悩みの改善。<br>※生理中も施術を受けていただけます。気になる場合はお気軽にお知らせください。</p>
</div>
</div>

<div class="reason-item">
<div class="reason-number">2</div>
<div>
<h3 class="reason-title"><em>肩こり・腰痛</em>などの不調を改善</h3>
<p class="reason-body">首こり・肩こり・腰痛など、日常的に感じる身体の不調を改善します。</p>
</div>
</div>

<div class="reason-item">
<div class="reason-number">3</div>
<div>
<h3 class="reason-title"><em>小顔や姿勢</em>の美しさまで改善</h3>
<p class="reason-body">姿勢が綺麗になる・表情が明るくなる・たるみ改善・小顔など見た目の美しさも改善します。</p>
<p class="reason-question">どちらの表情で生活したいですか？</p>
<div class="gallery-container">
<div class="gallery-item">
<div class="ba-slider" data-ba-slider>
<span class="ba-tag ba-tag-before">施術前</span>
<span class="ba-tag ba-tag-after">施術後</span>
<div style="width:100%;height:100%;display:flex;align-items:center;justify-content:center;background:#f3d6de;color:#8E5E65;font-size:0.8rem;">Before/After 画像</div>
<div class="ba-before-wrap">
<div style="width:100%;height:100%;display:flex;align-items:center;justify-content:center;background:#f8e1e7;color:#8E5E65;font-size:0.8rem;">Before</div>
</div>
<div class="ba-handle"></div>
</div>
<p class="ba-caption-label">40代（3ヶ月・8回ご利用）</p>
<div class="ba-caption-switch" data-caption-switch>
<p class="ba-caption-state before-state is-active" data-state="before">施術前：二重アゴ・もたつき・たるみ・だるさ・疲れ顔</p>
<p class="ba-caption-state after-state" data-state="after">施術後：表情が明るい・目がぱっちり・たるみがきゅっと！二重あごスッキリ</p>
</div>
</div>
<div class="gallery-item">
<div class="ba-slider" data-ba-slider>
<span class="ba-tag ba-tag-before">施術前</span>
<span class="ba-tag ba-tag-after">施術後</span>
<div style="width:100%;height:100%;display:flex;align-items:center;justify-content:center;background:#f3d6de;color:#8E5E65;font-size:0.8rem;">Before/After 画像</div>
<div class="ba-before-wrap">
<div style="width:100%;height:100%;display:flex;align-items:center;justify-content:center;background:#f8e1e7;color:#8E5E65;font-size:0.8rem;">Before</div>
</div>
<div class="ba-handle"></div>
</div>
<p class="ba-caption-label">50代（3ヶ月・8回ご利用）</p>
<div class="ba-caption-switch" data-caption-switch>
<p class="ba-caption-state before-state is-active" data-state="before">施術前：ふけ顔・顔色が悪い・たるみ・疲れ顔</p>
<p class="ba-caption-state after-state" data-state="after">施術後：表情が明るい・目がぱっちり・たるみがきゅっと！・小顔</p>
</div>
</div>
</div>
<p class="gallery-note">この変化は、顔だけを施術した結果ではありません。<br>3ヶ月かけて土台である仙骨から整えたことで、心身ともに健やかになり、本来の美しさが引き出された結果です。</p>
</div>
</div>
</div>
</div>

<div class="care-chart-section">
<h2 class="section-title">3ヶ月で、根本から変わる。</h2>
<p class="care-chart-lead">
パウワウのケアは、その場かぎりのリラクゼーションではありません。<br>
身体は3ヶ月かけて変わっていくと言われています。仙骨から根本的に整えることで、その変化を後押しします。<br>
年齢は関係ありません。今から始めても、決して遅くはないのです。
</p>
<div class="care-chart-img-wrap">
（継続的なケアによる変化のイメージ図：土台期・調整期・メンテナンス期）
</div>
</div>

<div class="staff-banner">
<div class="staff-banner-inner">
<div class="staff-banner-eyebrow">STEP 1 — TODAY</div>
<p class="staff-banner-text">
今から、<span class="accent">1回目の施術</span>が始まります。
<span class="sub">これはただのリラックス体験ではありません。</span>
一緒に<span class="accent">改善</span>していきましょう。<br><br>
よろしくお願いします。
</p>
</div>
</div>

<footer>
<div style="margin-top: 2.25rem;">
<div class="logo" style="font-size:1.25rem;">POWWOW</div>
<p class="footer-tagline">女性による女性の為の整体</p>
</div>
</footer>

<script>
document.querySelectorAll('.font-control-btn').forEach(button => {
button.addEventListener('click', () => {
const size = button.getAttribute('data-size');
document.documentElement.classList.remove('font-small', 'font-medium', 'font-large');
document.documentElement.classList.add(`font-${size}`);
document.querySelectorAll('.font-control-btn').forEach(btn => btn.classList.remove('active'));
button.classList.add('active');
});
});

(function () {
const cards = document.querySelectorAll('[data-symptom]');
const approachBlock = document.getElementById('approach-block');
const diagnosisBtn = document.getElementById('ai-diagnosis-btn');
const percentEl = document.getElementById('diagnosis-percent');
const messageEl = document.getElementById('diagnosis-message');
const hint = document.getElementById('symptom-hint');

const messages = {
50: '仙骨まわりの柔軟性が、やや低下しているかもしれません。放っておくと自律神経や女性ホルモンのバランスが乱れやすくなります。',
65: '仙骨の前傾・後傾がわずかに見られ、仙腸関節がこわばっている可能性があります。自律神経の働きが低下し、女性ホルモンバランスも乱れやすくなっている状態です。',
80: '仙骨の前傾・後傾が進み、仙腸関節も硬くなっていると考えられます。自律神経・女性ホルモンバランスの乱れに加え、骨格全体の歪みにもつながりはじめています。',
99: '仙骨の前傾・後傾がかなり進行し、仙腸関節も相当硬くなっている可能性が高いです。自律神経や女性ホルモンバランスが大きく乱れ、骨格の歪みもかなり進んでいる状態と考えられます。'
};

const percentByCount = { 1: 50, 2: 65, 3: 80, 4: 99 };

cards.forEach(card => {
card.addEventListener('click', () => {
card.classList.toggle('is-selected');
});
});

diagnosisBtn.addEventListener('click', () => {
const selectedCount = document.querySelectorAll('[data-symptom].is-selected').length;

if (selectedCount === 0) {
diagnosisBtn.classList.remove('is-shake');
void diagnosisBtn.offsetWidth;
diagnosisBtn.classList.add('is-shake');
if (hint) {
hint.textContent = 'まずは気になるものをタップして選んでください👆';
}
return;
}

const percent = percentByCount[selectedCount];
percentEl.textContent = percent;
messageEl.textContent = messages[percent];
approachBlock.classList.add('is-revealed');
if (hint) {
hint.textContent = '診断結果はこちら👇';
}
setTimeout(() => {
approachBlock.scrollIntoView({ behavior: 'smooth', block: 'center' });
}, 300);
});
})();

document.querySelectorAll('[data-ba-slider]').forEach(slider => {
const beforeWrap = slider.querySelector('.ba-before-wrap');
const handle = slider.querySelector('.ba-handle');
const galleryItem = slider.closest('.gallery-item');
const captionSwitch = galleryItem ? galleryItem.querySelector('[data-caption-switch]') : null;
const beforeCaption = captionSwitch ? captionSwitch.querySelector('[data-state="before"]') : null;
const afterCaption = captionSwitch ? captionSwitch.querySelector('[data-state="after"]') : null;
let dragging = false;

function setPosition(percent) {
percent = Math.max(0, Math.min(100, percent));
beforeWrap.style.width = percent + '%';
handle.style.left = percent + '%';

if (beforeCaption && afterCaption) {
if (percent >= 50) {
beforeCaption.classList.add('is-active');
afterCaption.classList.remove('is-active');
} else {
afterCaption.classList.add('is-active');
beforeCaption.classList.remove('is-active');
}
}
}

function positionFromEvent(evt) {
const rect = slider.getBoundingClientRect();
const clientX = evt.touches ? evt.touches[0].clientX : evt.clientX;
const x = clientX - rect.left;
return (x / rect.width) * 100;
}

setPosition(50);

slider.addEventListener('mousedown', e => { dragging = true; setPosition(positionFromEvent(e)); });
slider.addEventListener('touchstart', e => { dragging = true; setPosition(positionFromEvent(e)); }, { passive: true });

window.addEventListener('mousemove', e => { if (dragging) setPosition(positionFromEvent(e)); });
window.addEventListener('touchmove', e => { if (dragging) setPosition(positionFromEvent(e)); }, { passive: true });

window.addEventListener('mouseup', () => { dragging = false; });
window.addEventListener('touchend', () => { dragging = false; });
});
</script>

</body>
</html>
