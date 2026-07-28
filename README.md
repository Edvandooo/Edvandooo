<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fesousa · interface</title>
    <!-- 100% futuristic · no generic readme -->
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #020617;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            color: #F8FAFC;
            line-height: 1.5;
            padding: 2rem 1.5rem;
            display: flex;
            justify-content: center;
        }

        .container {
            max-width: 1280px;
            width: 100%;
            background: radial-gradient(circle at 10% 20%, #0F172A 0%, #020617 90%);
            border-radius: 3rem;
            padding: 2rem 2rem 1.5rem;
            box-shadow: 0 25px 60px -20px rgba(0, 217, 255, 0.15), inset 0 0 0 1px rgba(255, 255, 255, 0.02);
            backdrop-filter: blur(2px);
            border: 1px solid rgba(37, 99, 235, 0.08);
        }

        /* ---------- GLASS / NEON TOUCHES ---------- */
        .glass-panel {
            background: rgba(15, 23, 42, 0.55);
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
            border: 1px solid rgba(0, 217, 255, 0.08);
            box-shadow: 0 8px 32px -12px rgba(0, 0, 0, 0.6), 0 0 0 1px rgba(0, 217, 255, 0.02);
            border-radius: 2rem;
            transition: all 0.2s ease;
        }

        .neon-border {
            position: relative;
        }

        .neon-border::after {
            content: '';
            position: absolute;
            inset: -1px;
            border-radius: 2rem;
            padding: 1px;
            background: linear-gradient(135deg, #00D9FF20, #7C3AED30, #2563EB10);
            -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            -webkit-mask-composite: xor;
            mask-composite: exclude;
            pointer-events: none;
        }

        /* ---------- LAYOUT BLOCKS ---------- */
        .grid-bento {
            display: grid;
            grid-template-columns: repeat(12, 1fr);
            gap: 1.5rem;
            margin-top: 2rem;
        }

        .bento-item {
            grid-column: span 4;
            padding: 1.5rem 1.2rem;
            border-radius: 2rem;
            background: rgba(15, 23, 42, 0.4);
            backdrop-filter: blur(4px);
            border: 1px solid rgba(0, 217, 255, 0.06);
            transition: all 0.25s;
        }

        .bento-item:hover {
            border-color: #00D9FF30;
            background: rgba(15, 23, 42, 0.7);
            box-shadow: 0 0 30px -8px #00D9FF10;
        }

        .span-6 { grid-column: span 6; }
        .span-8 { grid-column: span 8; }
        .span-3 { grid-column: span 3; }
        .span-12 { grid-column: span 12; }

        /* ---------- TYPOGRAPHY ---------- */
        .glow-text {
            background: linear-gradient(135deg, #00D9FF 0%, #7C3AED 70%, #2563EB 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            letter-spacing: -0.02em;
        }

        .text-neon {
            color: #00D9FF;
            text-shadow: 0 0 20px #00D9FF30;
        }

        .tag {
            display: inline-block;
            background: rgba(0, 217, 255, 0.08);
            padding: 0.2rem 0.9rem;
            border-radius: 40px;
            font-size: 0.7rem;
            font-weight: 500;
            letter-spacing: 0.02em;
            color: #00D9FF;
            border: 1px solid #00D9FF20;
            backdrop-filter: blur(4px);
        }

        .status-pulse {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .status-pulse .dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background: #00D9FF;
            box-shadow: 0 0 20px #00D9FF;
            animation: pulse-dot 2s infinite;
        }

        @keyframes pulse-dot {
            0% { opacity: 0.4; transform: scale(0.9); }
            50% { opacity: 1; transform: scale(1.2); }
            100% { opacity: 0.4; transform: scale(0.9); }
        }

        /* ---------- HERO / HEADER ---------- */
        .hero-header {
            padding: 2.5rem 2rem;
            background: radial-gradient(ellipse at 70% 20%, #0F172A 0%, #020617 90%);
            border-radius: 2.5rem;
            border: 1px solid rgba(37, 99, 235, 0.12);
            position: relative;
            overflow: hidden;
        }

        .hero-header::before {
            content: '';
            position: absolute;
            top: -30%;
            right: -10%;
            width: 500px;
            height: 500px;
            background: radial-gradient(circle, #00D9FF08 0%, transparent 70%);
            pointer-events: none;
        }

        .hero-grid {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            position: relative;
            z-index: 2;
        }

        .hero-left h1 {
            font-size: 4.2rem;
            font-weight: 700;
            letter-spacing: -0.03em;
            line-height: 1;
            background: linear-gradient(135deg, #F8FAFC 0%, #94A3B8 80%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero-left .sub {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-top: 0.5rem;
        }

        .hero-left .sub span {
            font-size: 1.1rem;
            color: #94A3B8;
        }

        .hero-right {
            background: rgba(2, 6, 23, 0.6);
            backdrop-filter: blur(12px);
            border-radius: 2rem;
            padding: 1.8rem 2.2rem;
            border: 1px solid #00D9FF20;
            min-width: 240px;
            box-shadow: 0 0 50px -20px #00D9FF10;
        }

        .hero-right .sys-line {
            display: flex;
            justify-content: space-between;
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.8rem;
            padding: 0.3rem 0;
            border-bottom: 1px solid #0F172A;
            color: #94A3B8;
        }

        .hero-right .sys-line:last-child {
            border-bottom: none;
        }

        .hero-right .sys-line .val {
            color: #00D9FF;
            font-weight: 500;
        }

        /* ---------- DASHBOARD WIDGETS ---------- */
        .widget-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1.2rem;
        }

        .widget-card {
            background: rgba(2, 6, 23, 0.5);
            backdrop-filter: blur(4px);
            padding: 1rem 1.2rem;
            border-radius: 1.2rem;
            border: 1px solid rgba(0, 217, 255, 0.04);
            transition: 0.2s;
        }

        .widget-card:hover {
            border-color: #7C3AED30;
            background: rgba(15, 23, 42, 0.6);
        }

        .widget-label {
            font-size: 0.65rem;
            text-transform: uppercase;
            letter-spacing: 0.06em;
            color: #64748B;
        }

        .widget-value {
            font-size: 1.1rem;
            font-weight: 600;
            color: #F8FAFC;
            margin-top: 0.2rem;
        }

        .widget-value .highlight {
            color: #00D9FF;
        }

        /* ---------- PROGRESS BARS (ROADMAP) ---------- */
        .progress-track {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .progress-item {
            display: flex;
            align-items: center;
            gap: 0.8rem;
        }

        .progress-item .label {
            width: 90px;
            font-size: 0.85rem;
            font-weight: 500;
            color: #CBD5E1;
        }

        .progress-bar-bg {
            flex: 1;
            height: 6px;
            background: #0F172A;
            border-radius: 20px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            border-radius: 20px;
            background: linear-gradient(90deg, #2563EB, #00D9FF);
            width: 0%;
            box-shadow: 0 0 12px #00D9FF30;
        }

        /* ---------- LEARNING CARDS ---------- */
        .learn-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 1rem;
        }

        .learn-card {
            background: rgba(2, 6, 23, 0.5);
            backdrop-filter: blur(4px);
            border-radius: 1.2rem;
            padding: 1rem 1.2rem;
            border: 1px solid rgba(123, 58, 237, 0.08);
            display: flex;
            flex-direction: column;
        }

        .learn-card .top {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .learn-card .tech {
            font-weight: 600;
            color: #F8FAFC;
        }

        .learn-card .pct {
            font-size: 0.8rem;
            color: #7C3AED;
            font-weight: 500;
        }

        .learn-card .mini-bar {
            margin-top: 0.5rem;
            width: 100%;
            height: 3px;
            background: #0F172A;
            border-radius: 10px;
            overflow: hidden;
        }

        .learn-card .mini-bar .fill {
            height: 100%;
            background: linear-gradient(90deg, #7C3AED, #00D9FF);
            border-radius: 10px;
        }

        /* ---------- LANGUAGES FLAG ---------- */
        .lang-card {
            display: flex;
            align-items: center;
            gap: 0.8rem;
            background: rgba(2, 6, 23, 0.4);
            padding: 0.6rem 1rem;
            border-radius: 60px;
            border: 1px solid rgba(0, 217, 255, 0.06);
        }

        .lang-card .flag {
            font-size: 1.4rem;
        }

        .lang-card .name {
            font-weight: 500;
            color: #F8FAFC;
        }

        .lang-card .level {
            font-size: 0.7rem;
            color: #94A3B8;
            margin-left: auto;
            background: #0F172A;
            padding: 0.1rem 0.6rem;
            border-radius: 40px;
        }

        /* ---------- GOALS KPI ---------- */
        .kpi-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 0.8rem;
        }

        .kpi-card {
            background: rgba(2, 6, 23, 0.5);
            padding: 0.8rem 1rem;
            border-radius: 1rem;
            border-left: 2px solid #00D9FF;
            backdrop-filter: blur(4px);
        }

        .kpi-card .kpi-label {
            font-size: 0.6rem;
            text-transform: uppercase;
            color: #64748B;
            letter-spacing: 0.04em;
        }

        .kpi-card .kpi-value {
            font-size: 1rem;
            font-weight: 600;
            color: #F8FAFC;
        }

        /* ---------- PROJECT CARDS ---------- */
        .project-card {
            background: rgba(2, 6, 23, 0.6);
            backdrop-filter: blur(8px);
            border-radius: 1.5rem;
            padding: 1.2rem 1.5rem;
            border: 1px solid #2563EB20;
            transition: 0.25s;
        }

        .project-card:hover {
            border-color: #00D9FF40;
            transform: translateY(-2px);
        }

        .project-card .p-title {
            font-weight: 600;
            font-size: 1.1rem;
            color: #F8FAFC;
        }

        .project-card .p-desc {
            font-size: 0.85rem;
            color: #94A3B8;
            margin-top: 0.3rem;
        }

        .project-card .p-tag {
            margin-top: 0.7rem;
            display: inline-block;
            background: #0F172A;
            padding: 0.1rem 0.9rem;
            border-radius: 30px;
            font-size: 0.65rem;
            color: #00D9FF;
            border: 1px solid #00D9FF20;
        }

        /* ---------- ANALYTICS ---------- */
        .analytics-grid {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 1.2rem;
        }

        .analytics-card {
            background: rgba(2, 6, 23, 0.5);
            backdrop-filter: blur(4px);
            border-radius: 1.5rem;
            padding: 1rem 1.2rem;
            border: 1px solid #0F172A;
        }

        .stat-row {
            display: flex;
            justify-content: space-between;
            padding: 0.2rem 0;
            font-size: 0.8rem;
            color: #94A3B8;
            border-bottom: 1px solid #0F172A;
        }

        .stat-row .num {
            color: #F8FAFC;
            font-weight: 500;
        }

        /* ---------- QUOTE ---------- */
        .quote-block {
            background: linear-gradient(135deg, #0F172A 0%, #020617 100%);
            border-radius: 2rem;
            padding: 2rem 2.5rem;
            border: 1px solid #7C3AED20;
            position: relative;
        }

        .quote-block .quote-text {
            font-size: 1.4rem;
            font-weight: 400;
            color: #E2E8F0;
            letter-spacing: -0.01em;
        }

        .quote-block .quote-author {
            margin-top: 0.8rem;
            color: #64748B;
            font-size: 0.8rem;
        }

        /* ---------- FOOTER ---------- */
        .footer-premium {
            margin-top: 2.5rem;
            padding: 1.5rem 0 0.5rem;
            border-top: 1px solid rgba(0, 217, 255, 0.06);
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 0.8rem;
        }

        .footer-premium .brand {
            font-weight: 500;
            background: linear-gradient(135deg, #00D9FF, #7C3AED);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .footer-premium .foot-links {
            display: flex;
            gap: 1.5rem;
            font-size: 0.75rem;
            color: #64748B;
        }

        /* ---------- RESPONSIVE ---------- */
        @media (max-width: 1024px) {
            .widget-grid { grid-template-columns: repeat(2, 1fr); }
            .learn-grid { grid-template-columns: repeat(2, 1fr); }
            .kpi-grid { grid-template-columns: repeat(2, 1fr); }
            .analytics-grid { grid-template-columns: 1fr; }
            .hero-left h1 { font-size: 3.2rem; }
            .bento-item { grid-column: span 6; }
        }

        @media (max-width: 640px) {
            .hero-left h1 { font-size: 2.4rem; }
            .hero-right { min-width: unset; width: 100%; }
            .widget-grid { grid-template-columns: 1fr; }
            .learn-grid { grid-template-columns: 1fr; }
            .kpi-grid { grid-template-columns: 1fr; }
            .bento-item { grid-column: span 12; }
            .container { padding: 1rem; }
        }

        /* extras */
        .flex-wrap { display: flex; flex-wrap: wrap; gap: 0.8rem; align-items: center; }
        .mt-1 { margin-top: 0.8rem; }
        .mt-2 { margin-top: 1.5rem; }
        .gap-1 { gap: 1rem; }
        .text-muted { color: #64748B; font-size: 0.8rem; }
        .border-glow { border: 1px solid #00D9FF10; }
        .rounded-full { border-radius: 999px; }
    </style>
</head>
<body>
<div class="container">

    <!-- ═══ HEADER / HERO ═══ -->
    <header class="hero-header">
        <div class="hero-grid">
            <div class="hero-left">
                <h1>Francisco<br>Edvando</h1>
                <div class="sub">
                    <span class="tag">✦ fesousa</span>
                    <span class="status-pulse"><span class="dot"></span> <span style="color:#94A3B8; font-size:0.9rem;">disponível</span></span>
                </div>
                <div style="margin-top:1.2rem; display:flex; gap:0.4rem; flex-wrap:wrap;">
                    <span class="tag" style="background:#2563EB10; border-color:#2563EB30;">Python</span>
                    <span class="tag" style="background:#7C3AED10; border-color:#7C3AED30;">automação</span>
                    <span class="tag" style="background:#00D9FF10; border-color:#00D9FF30;">AI</span>
                    <span class="tag" style="background:#0F172A; border-color:#0F172A;">Godot</span>
                </div>
            </div>
            <div class="hero-right">
                <div class="sys-line"><span>STATUS</span><span class="val">● learning</span></div>
                <div class="sys-line"><span>FOCUS</span><span class="val">Python · AI</span></div>
                <div class="sys-line"><span>GOAL</span><span class="val">first dev job</span></div>
                <div class="sys-line"><span>LOCATION</span><span class="val">Brazil</span></div>
                <div class="sys-line"><span>AGE</span><span class="val">19</span></div>
            </div>
        </div>
        <!-- separador custom -->
        <svg width="100%" height="12" viewBox="0 0 1200 12" style="margin-top:1.8rem; opacity:0.25;">
            <path d="M0 6 L1200 6" stroke="#00D9FF" stroke-width="0.5" stroke-dasharray="8 8" />
            <circle cx="600" cy="6" r="3" fill="#7C3AED" />
            <circle cx="200" cy="6" r="2" fill="#2563EB" />
            <circle cx="1000" cy="6" r="2" fill="#00D9FF" />
        </svg>
    </header>

    <!-- ═══ DASHBOARD WIDGETS ═══ -->
    <div class="widget-grid" style="margin-top:2rem;">
        <div class="widget-card"><div class="widget-label">developer</div><div class="widget-value"><span class="highlight">Python</span> · beginner</div></div>
        <div class="widget-card"><div class="widget-label">location</div><div class="widget-value">Brazil</div></div>
        <div class="widget-card"><div class="widget-label">age</div><div class="widget-value">19</div></div>
        <div class="widget-card"><div class="widget-label">focus</div><div class="widget-value">automation · AI</div></div>
        <div class="widget-card"><div class="widget-label">current goal</div><div class="widget-value">first dev job</div></div>
        <div class="widget-card"><div class="widget-label">status</div><div class="widget-value"><span class="highlight">learning</span> everyday</div></div>
    </div>

    <!-- ═══ BENTO GRID: ABOUT + TECH + ROADMAP ═══ -->
    <div class="grid-bento">
        <!-- about -->
        <div class="bento-item span-3">
            <div style="font-size:0.6rem; letter-spacing:0.1em; color:#64748B; text-transform:uppercase;">about</div>
            <p style="margin-top:0.5rem; color:#CBD5E1; font-size:0.95rem; line-height:1.5;">Automação, IA e criação de ferramentas. 19 anos, construindo o caminho para ser dev Python.</p>
        </div>

        <!-- tech panel -->
        <div class="bento-item span-5">
            <div style="font-size:0.6rem; letter-spacing:0.1em; color:#64748B; text-transform:uppercase;">tech stack</div>
            <div style="display:flex; flex-wrap:wrap; gap:0.5rem; margin-top:0.7rem;">
                <span class="tag" style="background:#0F172A;">Python</span>
                <span class="tag" style="background:#0F172A;">Git</span>
                <span class="tag" style="background:#0F172A;">GitHub</span>
                <span class="tag" style="background:#0F172A;">Automation</span>
                <span class="tag" style="background:#0F172A;">AI</span>
                <span class="tag" style="background:#0F172A;">Godot</span>
                <span class="tag" style="background:#0F172A;">GDScript</span>
            </div>
            <div style="margin-top:0.6rem; display:flex; gap:1rem; flex-wrap:wrap; font-size:0.7rem; color:#94A3B8;">
                <span>◈ backend</span> <span>◈ automation</span> <span>◈ game dev</span>
            </div>
        </div>

        <!-- roadmap progress -->
        <div class="bento-item span-4">
            <div style="font-size:0.6rem; letter-spacing:0.1em; color:#64748B; text-transform:uppercase;">roadmap</div>
            <div class="progress-track" style="margin-top:0.8rem;">
                <div class="progress-item"><span class="label">Python</span><div class="progress-bar-bg"><div class="progress-fill" style="width:75%;"></div></div></div>
                <div class="progress-item"><span class="label">Git</span><div class="progress-bar-bg"><div class="progress-fill" style="width:60%;"></div></div></div>
                <div class="progress-item"><span class="label">Automação</span><div class="progress-bar-bg"><div class="progress-fill" style="width:45%;"></div></div></div>
                <div class="progress-item"><span class="label">AI</span><div class="progress-bar-bg"><div class="progress-fill" style="width:30%;"></div></div></div>
                <div class="progress-item"><span class="label">Godot</span><div class="progress-bar-bg"><div class="progress-fill" style="width:50%;"></div></div></div>
            </div>
        </div>
    </div>

    <!-- ═══ LEARNING DASHBOARD ═══ -->
    <div style="margin-top:2.5rem;">
        <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:1rem;">
            <span style="font-size:0.7rem; letter-spacing:0.06em; color:#64748B; text-transform:uppercase;">learning dashboard</span>
            <span class="tag" style="background:#0F172A;">active</span>
        </div>
        <div class="learn-grid">
            <div class="learn-card"><div class="top"><span class="tech">Python</span><span class="pct">75%</span></div><div class="mini-bar"><div class="fill" style="width:75%;"></div></div></div>
            <div class="learn-card"><div class="top"><span class="tech">Git</span><span class="pct">60%</span></div><div class="mini-bar"><div class="fill" style="width:60%;"></div></div></div>
            <div class="learn-card"><div class="top"><span class="tech">Automação</span><span class="pct">45%</span></div><div class="mini-bar"><div class="fill" style="width:45%;"></div></div></div>
            <div class="learn-card"><div class="top"><span class="tech">IA</span><span class="pct">30%</span></div><div class="mini-bar"><div class="fill" style="width:30%;"></div></div></div>
            <div class="learn-card"><div class="top"><span class="tech">Godot</span><span class="pct">50%</span></div><div class="mini-bar"><div class="fill" style="width:50%;"></div></div></div>
            <div class="learn-card"><div class="top"><span class="tech">GDScript</span><span class="pct">40%</span></div><div class="mini-bar"><div class="fill" style="width:40%;"></div></div></div>
        </div>
    </div>

    <!-- ═══ LANGUAGES + GOALS ═══ -->
    <div style="display:grid; grid-template-columns: 1fr 1fr; gap:1.5rem; margin-top:2rem;">
        <!-- languages -->
        <div>
            <div style="font-size:0.7rem; letter-spacing:0.06em; color:#64748B; text-transform:uppercase; margin-bottom:0.8rem;">idiomas</div>
            <div style="display:flex; flex-direction:column; gap:0.6rem;">
                <div class="lang-card"><span class="flag">🇧🇷</span><span class="name">Português</span><span class="level">nativo</span></div>
                <div class="lang-card"><span class="flag">🇯🇵</span><span class="name">Japonês</span><span class="level">N5</span></div>
                <div class="lang-card"><span class="flag">🇺🇸</span><span class="name">Inglês</span><span class="level">básico</span></div>
            </div>
        </div>
        <!-- goals KPI -->
        <div>
            <div style="font-size:0.7rem; letter-spacing:0.06em; color:#64748B; text-transform:uppercase; margin-bottom:0.8rem;">metas</div>
            <div class="kpi-grid">
                <div class="kpi-card"><div class="kpi-label">vaga</div><div class="kpi-value">primeira</div></div>
                <div class="kpi-card"><div class="kpi-label">projetos</div><div class="kpi-value">criar</div></div>
                <div class="kpi-card"><div class="kpi-label">IA</div><div class="kpi-value">aprender</div></div>
                <div class="kpi-card"><div class="kpi-label">automação</div><div class="kpi-value">dominar</div></div>
            </div>
        </div>
    </div>

    <!-- ═══ PROJECTS ═══ -->
    <div style="margin-top:2.5rem;">
        <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:0.8rem;">
            <span style="font-size:0.7rem; letter-spacing:0.06em; color:#64748B; text-transform:uppercase;">projetos em destaque</span>
            <span class="tag" style="background:#0F172A;">crescendo</span>
        </div>
        <div style="display:grid; grid-template-columns: 1fr 1fr; gap:1rem;">
            <div class="project-card">
                <div class="p-title">Calculadora Python</div>
                <div class="p-desc">Primeiro projeto: lógica, CLI e interface simples. Marco inicial.</div>
                <span class="p-tag">Python</span>
            </div>
            <div class="project-card">
                <div class="p-title">Portfólio UI</div>
                <div class="p-desc">Landing page futurista — este README.</div>
                <span class="p-tag">HTML · CSS</span>
            </div>
            <div class="project-card" style="grid-column: span 2;">
                <div class="p-title">Em progresso: automação · IA · Godot</div>
                <div class="p-desc">Próximos projetos: ferramentas de automação, agentes de IA, jogos em Godot.</div>
                <span class="p-tag">roadmap</span>
            </div>
        </div>
    </div>

    <!-- ═══ GITHUB ANALYTICS ═══ -->
    <div style="margin-top:2.5rem;">
        <div style="font-size:0.7rem; letter-spacing:0.06em; color:#64748B; text-transform:uppercase; margin-bottom:0.8rem;">github analytics</div>
        <div class="analytics-grid">
            <div class="analytics-card">
                <div style="display:grid; grid-template-columns:1fr 1fr; gap:0.2rem 1rem;">
                    <div class="stat-row"><span>repos</span><span class="num">8</span></div>
                    <div class="stat-row"><span>commits</span><span class="num">127</span></div>
                    <div class="stat-row"><span>PRs</span><span class="num">3</span></div>
                    <div class="stat-row"><span>issues</span><span class="num">2</span></div>
                    <div class="stat-row"><span>streak</span><span class="num">4d</span></div>
                    <div class="stat-row"><span>trophies</span><span class="num">6</span></div>
                </div>
            </div>
            <div class="analytics-card" style="display:flex; flex-direction:column; justify-content:center;">
                <div style="font-size:0.7rem; color:#64748B;">top lang</div>
                <div style="font-size:1.2rem; font-weight:600; color:#00D9FF;">Python 68%</div>
                <div style="display:flex; gap:0.8rem; margin-top:0.2rem; font-size:0.7rem; color:#94A3B8;">
                    <span>HTML 20%</span> <span>CSS 12%</span>
                </div>
                <div style="margin-top:0.5rem; width:100%; height:4px; background:#0F172A; border-radius:10px; overflow:hidden;">
                    <div style="width:68%; height:100%; background:linear-gradient(90deg,#2563EB,#00D9FF);"></div>
                </div>
            </div>
        </div>
        <!-- contribution + snake placeholder (visual) -->
        <div style="margin-top:0.8rem; display:grid; grid-template-columns:2fr 1fr; gap:1rem;">
            <div class="analytics-card" style="padding:0.8rem 1.2rem;">
                <div style="font-size:0.6rem; color:#64748B; letter-spacing:0.04em;">contribuição (simulada)</div>
                <div style="display:flex; gap:0.2rem; flex-wrap:wrap; margin-top:0.3rem;">
                    <span style="background:#0F172A; padding:0.1rem 0.4rem; border-radius:4px; font-size:0.6rem;">▮</span><span style="background:#0F172A; padding:0.1rem 0.4rem; border-radius:4px; font-size:0.6rem;">▮</span><span style="background:#2563EB40; padding:0.1rem 0.4rem; border-radius:4px; font-size:0.6rem;">▮</span><span style="background:#00D9FF30; padding:0.
