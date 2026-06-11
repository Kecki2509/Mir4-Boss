[index.html.html](https://github.com/user-attachments/files/28818352/index.html.html)
<!DOCTYPE html>
<html>
<head>
	<meta http-equiv="content-type" content="text/html; charset=utf-8"/>
	<title></title>
	<meta name="generator" content="LibreOffice 24.8.1.2 (Linux)"/>
	<meta name="created" content="00:00:00"/>
	<meta name="changed" content="00:00:00"/>
	<style type="text/css">
		@page { size: 8.27in 11.69in; margin: 0.79in }
		p { line-height: 115%; margin-bottom: 0.1in; background: transparent }
		pre { background: transparent }
		pre.western { font-family: "Liberation Mono", monospace; font-size: 10pt }
		pre.cjk { font-family: "NSimSun", monospace; font-size: 10pt }
		pre.ctl { font-family: "Liberation Mono", monospace; font-size: 10pt }
	</style>
</head>
<body lang="en-US" link="#000080" vlink="#800000" dir="ltr"><pre class="western">&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;pt-BR&quot;&gt;
&lt;head&gt;
    &lt;meta charset=&quot;UTF-8&quot;&gt;
    &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;&gt;
    &lt;title&gt;MIR4 Boss Timer - Interface HUD Oficial&lt;/title&gt;
    &lt;style&gt;
        @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght=600;700&amp;family=Rajdhani:wght=500;600;700&amp;display=swap');

        :root {
            --bg-main: #0c0d12;
            --bg-panel: #161923;
            --bg-card: #141721;
            --border-gold: #bf953f;
            --text-gold: #e5c158;
            --text-light: #f0f2f5;
            --text-muted: #808799;
            --neon-green: #00ff66;
            --neon-red: #ff3333;
            --blue-accent: #1c324a;
        }

        body {
            font-family: 'Rajdhani', sans-serif;
            background-color: var(--bg-main);
            color: var(--text-light);
            margin: 0;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
        }

        /* HEADER */
        header {
            text-align: center;
            margin-bottom: 20px;
        }

        header h1 {
            font-family: 'Cinzel', serif;
            font-size: 2.2rem;
            margin: 0;
            background: linear-gradient(to right, #fff, var(--text-gold), #fff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        header p {
            color: var(--text-muted);
            margin: 5px 0 0 0;
            font-size: 1rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* BARRA DE MENU SUPERIOR */
        .top-navigation {
            display: flex;
            justify-content: space-between;
            align-items: center;
            width: 100%;
            max-width: 1250px;
            background: #11141d;
            border: 1px solid rgba(191, 149, 63, 0.4);
            border-radius: 30px;
            padding: 6px 20px;
            box-shadow: inset 0 0 10px rgba(0,0,0,0.8), 0 5px 15px rgba(0,0,0,0.5);
            margin-bottom: 25px;
            box-sizing: border-box;
        }

        .filter-tabs {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .filter-tabs span {
            font-family: 'Cinzel', serif;
            color: var(--text-gold);
            font-size: 0.9rem;
            font-weight: bold;
            margin-right: 10px;
        }

        .tab-btn {
            background: transparent;
            border: none;
            color: var(--text-muted);
            font-family: 'Rajdhani', sans-serif;
            font-weight: 700;
            font-size: 1rem;
            padding: 6px 16px;
            cursor: pointer;
            border-radius: 15px;
            transition: all 0.2s;
            text-transform: uppercase;
        }

        .tab-btn:hover, .tab-btn.active {
            color: #000;
            background: linear-gradient(135deg, #bf953f, #fcf6ba, #b38728);
            font-weight: bold;
            box-shadow: 0 0 10px rgba(229, 193, 88, 0.4);
        }

        .search-container input {
            background: #191e2b;
            border: 1px solid rgba(255,255,255,0.1);
            border-radius: 15px;
            padding: 8px 15px;
            color: #fff;
            font-family: 'Rajdhani', sans-serif;
            font-size: 1rem;
            outline: none;
            width: 200px;
            transition: all 0.3s;
        }

        .search-container input:focus {
            border-color: var(--text-gold);
            box-shadow: 0 0 8px rgba(229, 193, 88, 0.2);
        }

        /* COLUNAS MAIN */
        .main-hud {
            display: flex;
            width: 100%;
            max-width: 1250px;
            gap: 20px;
        }

        /* SIDEBAR */
        .sidebar {
            width: 240px;
            display: flex;
            flex-direction: column;
            gap: 20px;
            flex-shrink: 0;
        }

        .side-panel {
            background: var(--bg-panel);
            border-radius: 8px;
            border: 1px solid rgba(255,255,255,0.05);
            padding: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.4);
        }

        .panel-title {
            font-family: 'Cinzel', serif;
            font-size: 0.95rem;
            color: var(--text-gold);
            margin-bottom: 12px;
            border-bottom: 1px solid rgba(191, 149, 63, 0.2);
            padding-bottom: 5px;
            letter-spacing: 0.5px;
        }

        /* PAINEL DE BOSSES VIVOS */
        .live-panel {
            border: 1px solid rgba(255, 51, 51, 0.3) !important;
            background: linear-gradient(180deg, #1e1315 0%, #161923 100%);
        }

        .live-item {
            background: rgba(255, 30, 30, 0.1);
            border: 1px solid rgba(255, 51, 51, 0.3);
            border-radius: 4px;
            padding: 10px;
            margin-bottom: 8px;
            font-size: 0.95rem;
            cursor: pointer;
            transition: background 0.2s;
        }

        .live-item:hover {
            background: rgba(255, 30, 30, 0.2);
        }

        .live-title {
            font-weight: bold;
            color: #fff;
            display: flex;
            justify-content: space-between;
        }

        .live-status {
            color: var(--neon-red);
            font-weight: bold;
            animation: pulse-red 1s infinite alternate;
        }

        .live-desc {
            color: var(--text-muted);
            font-size: 0.8rem;
            margin-top: 3px;
        }

        @keyframes pulse-red {
            from { opacity: 0.5; text-shadow: 0 0 2px rgba(255,51,51,0); }
            to { opacity: 1; text-shadow: 0 0 8px rgba(255,51,51,0.8); }
        }

        .audio-btn {
            width: 100%;
            background: #1c261a;
            border: 1px solid #339944;
            border-radius: 6px;
            color: #66ff88;
            font-family: 'Rajdhani', sans-serif;
            font-weight: bold;
            font-size: 1rem;
            padding: 12px;
            cursor: pointer;
            transition: all 0.2s;
            text-transform: uppercase;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .audio-btn.muted {
            background: #261a1a;
            border-color: #993333;
            color: #ff6666;
        }

        .progress-box {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 6px;
            padding: 12px;
            text-align: center;
            border: 1px solid rgba(0, 255, 102, 0.1);
        }

        .progress-box .counter {
            font-size: 2rem;
            font-weight: bold;
            color: var(--neon-green);
            text-shadow: 0 0 10px rgba(0, 255, 102, 0.3);
            margin-bottom: 5px;
        }

        .progress-box .label {
            font-size: 0.85rem;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .clear-btn {
            background: #231215;
            border: 1px solid #993333;
            border-radius: 6px;
            color: #ff6666;
            font-family: 'Rajdhani', sans-serif;
            font-weight: bold;
            font-size: 0.9rem;
            padding: 10px;
            cursor: pointer;
            transition: all 0.2s;
            text-transform: uppercase;
        }

        .clear-btn:hover {
            background: #ff3333;
            color: #fff;
            box-shadow: 0 0 10px rgba(255, 51, 51, 0.4);
        }

        .map-btn {
            background: #1a2233;
            border: 1px solid var(--border-gold);
            border-radius: 6px;
            color: var(--text-gold);
            font-family: 'Cinzel', serif;
            font-size: 0.9rem;
            padding: 12px;
            cursor: pointer;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 5px;
            font-weight: bold;
            transition: all 0.2s;
        }

        .map-btn:hover {
            background: var(--text-gold);
            color: #000;
            box-shadow: 0 0 15px rgba(229, 193, 88, 0.3);
        }

        /* GRID DE CARDS */
        .grid-container {
            flex-grow: 1;
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(45%, 1fr));
            gap: 20px;
            align-content: flex-start;
        }

        .card {
            background: var(--bg-panel);
            border-radius: 8px;
            border: 1px solid rgba(255,255,255,0.05);
            box-shadow: 0 10px 25px rgba(0,0,0,0.5);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            min-height: 200px;
            transition: border-color 0.3s, opacity 0.3s, box-shadow 0.3s;
        }

        .card-top-bar {
            background: linear-gradient(90deg, #121c2b 0%, #1a2636 100%);
            padding: 10px 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            cursor: pointer;
            user-select: none;
        }

        .card-top-bar:hover {
            background: linear-gradient(90deg, #16253a 0%, #223249 100%);
        }

        .card-boss-name {
            font-family: 'Cinzel', serif;
            font-size: 1.1rem;
            font-weight: bold;
            letter-spacing: 1px;
            color: #fff;
        }

        .top-bar-right {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .card-lvl-badge {
            font-size: 0.85rem;
            font-weight: bold;
            padding: 2px 8px;
            border-radius: 4px;
            color: #fff;
            background: rgba(255,255,255,0.1);
        }

        .weekly-checkbox {
            appearance: none;
            -webkit-appearance: none;
            width: 18px;
            height: 18px;
            border: 2px solid var(--text-gold);
            border-radius: 4px;
            background: transparent;
            cursor: pointer;
            position: relative;
            outline: none;
            transition: all 0.2s;
        }

        .weekly-checkbox:checked {
            background: var(--neon-green);
            border-color: var(--neon-green);
            box-shadow: 0 0 8px var(--neon-green);
        }

        .weekly-checkbox:checked::after {
            content: 'â';
            font-size: 14px;
            color: #000;
            font-weight: bold;
            position: absolute;
            top: -2px;
            left: 2px;
        }

        /* Cores das Badges */
        .card.lvl-140 .card-lvl-badge { background: #4f709c; }
        .card.lvl-141 .card-lvl-badge { background: #5d9c59; }
        .card.lvl-143 .card-lvl-badge { background: #3085c3; }
        .card.lvl-150 .card-lvl-badge { background: #7b66b3; }
        .card.lvl-155 .card-lvl-badge { background: #b35175; }

        .card-body {
            padding: 15px;
            display: flex;
            flex-direction: column;
            gap: 6px;
            font-size: 1.05rem;
            color: #b5bdcf;
        }

        .info-row {
            display: flex;
            gap: 8px;
            align-items: center;
        }

        .info-label {
            color: var(--text-muted);
            width: 80px;
        }

        .card-footer-timer {
            padding: 15px;
            text-align: center;
            background: rgba(0,0,0,0.3);
            border-top: 1px solid rgba(255,255,255,0.02);
        }

        .footer-next-title {
            font-family: 'Cinzel', serif;
            font-size: 1.6rem;
            color: #fff;
            margin-bottom: 2px;
            font-weight: bold;
            letter-spacing: 1px;
        }

        .footer-countdown {
            font-size: 1rem;
            color: var(--text-muted);
        }

        /* ESTADO IMINENTE */
        .card.imminent {
            border-color: rgba(255, 51, 51, 0.4);
            box-shadow: 0 0 20px rgba(255, 51, 51, 0.15);
        }
        .card.imminent .footer-next-title {
            color: var(--neon-red);
            text-shadow: 0 0 10px rgba(255, 51, 51, 0.4);
        }
        .card.imminent .footer-countdown {
            color: #ff8888;
        }

        /* ESTADO CONCLUÃDO SEMANAL */
        .card.completed {
            border-color: rgba(0, 255, 102, 0.25) !important;
            opacity: 0.45;
            box-shadow: none;
        }
        .card.completed .footer-next-title {
            color: #60a377 !important;
            text-shadow: none !important;
        }
        .card.completed .card-top-bar {
            background: linear-gradient(90deg, #0d1a12 0%, #122419 100%);
        }

        @media (max-width: 900px) {
            .main-hud { flex-direction: column; }
            .sidebar { width: 100%; }
            .grid-container { grid-template-columns: 1fr; }
            .top-navigation { flex-direction: column; gap: 15px; border-radius: 15px; }
            .filter-tabs { flex-wrap: wrap; justify-content: center; }
        }
    &lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;

    &lt;header&gt;
        &lt;h1&gt;MIR4 BOSS TIMER&lt;/h1&gt;
        &lt;p&gt;Fuso HorÃ¡rio de BrasÃ&shy;lia (UTC-3) | Atualizado em tempo real&lt;/p&gt;
    &lt;/header&gt;

    &lt;div class=&quot;top-navigation&quot;&gt;
        &lt;div class=&quot;filter-tabs&quot;&gt;
            &lt;span&gt;SELECIONE O NÃVEL:&lt;/span&gt;
            &lt;button class=&quot;tab-btn active&quot; onclick=&quot;filterByTab('all', this)&quot;&gt;Todos&lt;/button&gt;
            &lt;button class=&quot;tab-btn&quot; onclick=&quot;filterByTab('140-', this)&quot;&gt;140-&lt;/button&gt;
            &lt;button class=&quot;tab-btn&quot; onclick=&quot;filterByTab('141+', this)&quot;&gt;141+&lt;/button&gt;
            &lt;button class=&quot;tab-btn&quot; onclick=&quot;filterByTab('143+', this)&quot;&gt;143+&lt;/button&gt;
            &lt;button class=&quot;tab-btn&quot; onclick=&quot;filterByTab('150+', this)&quot;&gt;150+&lt;/button&gt;
            &lt;button class=&quot;tab-btn&quot; onclick=&quot;filterByTab('155+', this)&quot;&gt;155+&lt;/button&gt;
        &lt;/div&gt;
        &lt;div class=&quot;search-container&quot;&gt;
            &lt;input type=&quot;text&quot; id=&quot;bossSearch&quot; placeholder=&quot;Nome do boss...&quot; oninput=&quot;updateHUD()&quot;&gt;
        &lt;/div&gt;
    &lt;/div&gt;

    &lt;div class=&quot;main-hud&quot;&gt;
        
        &lt;div class=&quot;sidebar&quot;&gt;
            &lt;button id=&quot;audioToggleBtn&quot; class=&quot;audio-btn&quot; onclick=&quot;toggleAudioGlobal()&quot;&gt;
                &lt;span&gt;ð&lt;/span&gt; &lt;span&gt;Ãudio: Ativado&lt;/span&gt;
            &lt;/button&gt;

            &lt;div class=&quot;side-panel live-panel&quot;&gt;
                &lt;div class=&quot;panel-title&quot; style=&quot;color: var(--neon-red);&quot;&gt;âï¸ Nascidos Agora (Vivos)&lt;/div&gt;
                &lt;div id=&quot;liveBossesContainer&quot;&gt;
                    &lt;div style=&quot;color: var(--text-muted); font-size: 0.9rem; text-align: center; padding: 10px;&quot;&gt;Nenhum boss ativo no momento&lt;/div&gt;
                &lt;/div&gt;
            &lt;/div&gt;

            &lt;div class=&quot;side-panel&quot;&gt;
                &lt;div class=&quot;panel-title&quot;&gt;Progresso da Semana&lt;/div&gt;
                &lt;div class=&quot;progress-box&quot;&gt;
                    &lt;div id=&quot;weeklyCounter&quot; class=&quot;counter&quot;&gt;0 / 0&lt;/div&gt;
                    &lt;div class=&quot;label&quot;&gt;Bosses Abatidos&lt;/div&gt;
                &lt;/div&gt;
            &lt;/div&gt;

            &lt;button class=&quot;clear-btn&quot; onclick=&quot;resetWeeklyList()&quot;&gt;
                ð Resetar Abates Semanais
            &lt;/button&gt;
            
            &lt;button class=&quot;map-btn&quot;&gt;
                &lt;span&gt;ðºï¸&lt;/span&gt;
                &lt;span&gt;VEJA O MAPA&lt;/span&gt;
            &lt;/button&gt;
        &lt;/div&gt;

        &lt;div class=&quot;grid-container&quot; id=&quot;bossGrid&quot;&gt;&lt;/div&gt;
    &lt;/div&gt;

    &lt;script&gt;
        let currentTabFilter = 'all';
        let isAudioEnabled = true;
        let activeAudioAlerts = {};

        const bossData = [
            { id: &quot;mata&quot;, lvl: &quot;140-&quot;, class: &quot;lvl-140&quot;, world: &quot;L3W1&quot;, map: &quot;Bullface Forest&quot;, boss: &quot;Mata&quot;, times: [&quot;00:00&quot;, &quot;02:00&quot;, &quot;04:00&quot;, &quot;06:00&quot;, &quot;08:00&quot;, &quot;10:00&quot;, &quot;12:00&quot;, &quot;14:00&quot;, &quot;16:00&quot;, &quot;18:00&quot;, &quot;20:00&quot;, &quot;22:00&quot;] },
            { id: &quot;touro_trovejante&quot;, lvl: &quot;140-&quot;, class: &quot;lvl-140&quot;, world: &quot;L3W1&quot;, map: &quot;Demon Bull Temple 1F&quot;, boss: &quot;Touro Trovejante&quot;, times: [&quot;01:00&quot;, &quot;03:00&quot;, &quot;05:00&quot;, &quot;07:00&quot;, &quot;09:00&quot;, &quot;11:00&quot;, &quot;13:00&quot;, &quot;15:00&quot;, &quot;17:00&quot;, &quot;19:00&quot;, &quot;21:00&quot;, &quot;23:00&quot;] },
            { id: &quot;rei_touros_malvados&quot;, lvl: &quot;140-&quot;, class: &quot;lvl-140&quot;, world: &quot;L3W1&quot;, map: &quot;Bullface King's Sanctuary&quot;, boss: &quot;Rei dos Touros Malvados&quot;, times: [&quot;00:00&quot;, &quot;03:00&quot;, &quot;06:00&quot;, &quot;09:00&quot;, &quot;12:00&quot;, &quot;15:00&quot;, &quot;18:00&quot;, &quot;21:00&quot;] },
            { id: &quot;velho_ermo&quot;, lvl: &quot;140-&quot;, class: &quot;lvl-140&quot;, world: &quot;L3W8&quot;, map: &quot;Whitemaur Sealing Circle&quot;, boss: &quot;Velho do Ermo&quot;, times: [&quot;01:00&quot;, &quot;05:00&quot;, &quot;09:00&quot;, &quot;13:00&quot;, &quot;17:00&quot;, &quot;21:00&quot;] },
            
            { id: &quot;taehyul&quot;, lvl: &quot;141+&quot;, class: &quot;lvl-141&quot;, world: &quot;L3W7&quot;, map: &quot;Taehyul's Garden&quot;, boss: &quot;Taehyul&quot;, times: [&quot;01:00&quot;, &quot;03:00&quot;, &quot;05:00&quot;, &quot;07:00&quot;, &quot;09:00&quot;, &quot;11:00&quot;, &quot;13:00&quot;, &quot;15:00&quot;, &quot;17:00&quot;, &quot;19:00&quot;, &quot;21:00&quot;, &quot;23:00&quot;] },
            { id: &quot;yiun&quot;, lvl: &quot;141+&quot;, class: &quot;lvl-141&quot;, world: &quot;L3W7&quot;, map: &quot;Demoniac Cult Hall&quot;, boss: &quot;Yiun&quot;, times: [&quot;02:00&quot;, &quot;05:00&quot;, &quot;08:00&quot;, &quot;11:00&quot;, &quot;14:00&quot;, &quot;17:00&quot;, &quot;20:00&quot;, &quot;23:00&quot;] },
            { id: &quot;santidade_nefariox&quot;, lvl: &quot;141+&quot;, class: &quot;lvl-141&quot;, world: &quot;L3W4&quot;, map: &quot;Phantasia Desert&quot;, boss: &quot;Santidade InabalÃ¡vel Nefariox&quot;, times: [&quot;00:00&quot;, &quot;02:00&quot;, &quot;04:00&quot;, &quot;06:00&quot;, &quot;08:00&quot;, &quot;10:00&quot;, &quot;12:00&quot;, &quot;14:00&quot;, &quot;16:00&quot;, &quot;18:00&quot;, &quot;20:00&quot;, &quot;22:00&quot;] },
            { id: &quot;kurilaica&quot;, lvl: &quot;141+&quot;, class: &quot;lvl-141&quot;, world: &quot;L3W4&quot;, map: &quot;Overlord Sealing Circle&quot;, boss: &quot;Kurilaica&quot;, times: [&quot;00:00&quot;, &quot;03:00&quot;, &quot;06:00&quot;, &quot;09:00&quot;, &quot;12:00&quot;, &quot;15:00&quot;, &quot;18:00&quot;, &quot;21:00&quot;] },
            
            { id: &quot;juhui&quot;, lvl: &quot;143+&quot;, class: &quot;lvl-143&quot;, world: &quot;L3W2&quot;, map: &quot;Redmoon Mountain&quot;, boss: &quot;Juhui&quot;, times: [&quot;02:30&quot;, &quot;05:30&quot;, &quot;08:30&quot;, &quot;11:30&quot;, &quot;14:30&quot;, &quot;17:30&quot;, &quot;20:30&quot;, &quot;23:30&quot;] },
            { id: &quot;faluk&quot;, lvl: &quot;143+&quot;, class: &quot;lvl-143&quot;, world: &quot;L3W5&quot;, map: &quot;Great Sabuk Wall&quot;, boss: &quot;Faluk&quot;, times: [&quot;00:30&quot;, &quot;03:30&quot;, &quot;06:30&quot;, &quot;09:30&quot;, &quot;12:30&quot;, &quot;15:30&quot;, &quot;18:30&quot;, &quot;21:30&quot;] },
            { id: &quot;assombracao_destruidora&quot;, lvl: &quot;143+&quot;, class: &quot;lvl-143&quot;, world: &quot;L3W5&quot;, map: &quot;Illusion Temple&quot;, boss: &quot;AssombraÃ§Ã£o Destruidora de HistÃ³rias&quot;, times: [&quot;01:30&quot;, &quot;04:30&quot;, &quot;07:30&quot;, &quot;10:30&quot;, &quot;13:30&quot;, &quot;16:30&quot;, &quot;19:30&quot;, &quot;22:30&quot;] },

            { id: &quot;gyo_besta&quot;, lvl: &quot;150+&quot;, class: &quot;lvl-150&quot;, world: &quot;L3W3&quot;, map: &quot;Nefariox Necropolis&quot;, boss: &quot;Gyo da Besta&quot;, times: [&quot;02:30&quot;, &quot;08:30&quot;, &quot;14:30&quot;, &quot;20:30&quot;] },
            { id: &quot;imperador_tatu&quot;, lvl: &quot;150+&quot;, class: &quot;lvl-150&quot;, world: &quot;L3W3&quot;, map: &quot;Viperbeast Plain&quot;, boss: &quot;Imperador Tatu Sombrio&quot;, times: [&quot;01:30&quot;, &quot;03:30&quot;, &quot;05:30&quot;, &quot;07:30&quot;, &quot;09:30&quot;, &quot;11:30&quot;, &quot;13:30&quot;, &quot;15:30&quot;, &quot;17:30&quot;, &quot;19:30&quot;, &quot;21:30&quot;, &quot;23:30&quot;] },
            { id: &quot;bodoo&quot;, lvl: &quot;150+&quot;, class: &quot;lvl-150&quot;, world: &quot;L3W3&quot;, map: &quot;Viperbeast Plain&quot;, boss: &quot;Bodoo&quot;, times: [&quot;03:30&quot;, &quot;09:30&quot;, &quot;15:30&quot;, &quot;21:30&quot;] },
            { id: &quot;mara&quot;, lvl: &quot;150+&quot;, class: &quot;lvl-150&quot;, world: &quot;L3W3&quot;, map: &quot;Rockcut Tomb&quot;, boss: &quot;Mara&quot;, times: [&quot;02:30&quot;, &quot;05:30&quot;, &quot;08:30&quot;, &quot;11:30&quot;, &quot;14:30&quot;, &quot;17:30&quot;, &quot;20:30&quot;, &quot;23:30&quot;] },
            { id: &quot;asura_bicheon&quot;, lvl: &quot;150+&quot;, class: &quot;lvl-150&quot;, world: &quot;L3W6&quot;, map: &quot;Bicheon Town&quot;, boss: &quot;Asura de Bicheon&quot;, times: [&quot;04:30&quot;, &quot;10:30&quot;, &quot;16:30&quot;, &quot;22:30&quot;] },
            { id: &quot;cheol_mokgang&quot;, lvl: &quot;150+&quot;, class: &quot;lvl-150&quot;, world: &quot;L3W6&quot;, map: &quot;Bicheon Town&quot;, boss: &quot;Cheol Mokgang&quot;, times: [&quot;00:30&quot;, &quot;02:30&quot;, &quot;04:30&quot;, &quot;06:30&quot;, &quot;08:30&quot;, &quot;10:30&quot;, &quot;12:30&quot;, &quot;14:30&quot;, &quot;16:30&quot;, &quot;18:30&quot;, &quot;20:30&quot;, &quot;22:30&quot;] },
            { id: &quot;wuihan&quot;, lvl: &quot;150+&quot;, class: &quot;lvl-150&quot;, world: &quot;L3W6&quot;, map: &quot;Phantom Woods&quot;, boss: &quot;Wuihan&quot;, times: [&quot;05:30&quot;, &quot;11:30&quot;, &quot;17:30&quot;, &quot;23:30&quot;] },
            { id: &quot;hong_yeom&quot;, lvl: &quot;150+&quot;, class: &quot;lvl-150&quot;, world: &quot;L3W6&quot;, map: &quot;Abisso da Mina DemonÃ&shy;aca&quot;, boss: &quot;Hong Yeom Transformada&quot;, times: [&quot;01:30&quot;, &quot;03:30&quot;, &quot;05:30&quot;, &quot;07:30&quot;, &quot;09:30&quot;, &quot;11:30&quot;, &quot;13:30&quot;, &quot;15:30&quot;, &quot;17:30&quot;, &quot;19:30&quot;, &quot;21:30&quot;, &quot;23:30&quot;] },
            { id: &quot;yeti&quot;, lvl: &quot;150+&quot;, class: &quot;lvl-150&quot;, world: &quot;L3W6&quot;, map: &quot;Bicheon Labyrinth&quot;, boss: &quot;Yeti&quot;, times: [&quot;00:30&quot;, &quot;06:30&quot;, &quot;12:30&quot;, &quot;18:30&quot;] },

            { id: &quot;jihwa&quot;, lvl: &quot;155+&quot;, class: &quot;lvl-155&quot;, world: &quot;L1W1&quot;, map: &quot;Unseo Town&quot;, boss: &quot;Jihwa&quot;, times: [&quot;02:30&quot;, &quot;05:30&quot;, &quot;08:30&quot;, &quot;11:30&quot;, &quot;14:30&quot;, &quot;17:30&quot;, &quot;20:30&quot;, &quot;23:30&quot;] },
            { id: &quot;tatu_gigante&quot;, lvl: &quot;155+&quot;, class: &quot;lvl-155&quot;, world: &quot;L1W1&quot;, map: &quot;7 Valleys Mountain&quot;, boss: &quot;Tatu Gigante&quot;, times: [&quot;00:30&quot;, &quot;03:30&quot;, &quot;06:30&quot;, &quot;09:30&quot;, &quot;12:30&quot;, &quot;15:30&quot;, &quot;18:30&quot;, &quot;21:30&quot;] },
            { id: &quot;yaksha&quot;, lvl: &quot;155+&quot;, class: &quot;lvl-155&quot;, world: &quot;L1W1&quot;, map: &quot;7 Valleys Mountain&quot;, boss: &quot;Yaksha&quot;, times: [&quot;03:30&quot;, &quot;09:30&quot;, &quot;15:30&quot;, &quot;21:30&quot;] },
            { id: &quot;bulhu&quot;, lvl: &quot;155+&quot;, class: &quot;lvl-155&quot;, world: &quot;L1W1&quot;, map: &quot;Flame Island&quot;, boss: &quot;Bulhu&quot;, times: [&quot;04:30&quot;, &quot;10:30&quot;, &quot;16:30&quot;, &quot;22:30&quot;] },
            { id: &quot;bolota_m1&quot;, lvl: &quot;155+&quot;, class: &quot;lvl-155&quot;, world: &quot;L1W1&quot;, map: &quot;Flame Island&quot;, boss: &quot;Bolota Mapa 1&quot;, times: [&quot;03:00&quot;, &quot;09:00&quot;, &quot;15:00&quot;, &quot;21:00&quot;] },
            { id: &quot;gwe_mukang&quot;, lvl: &quot;155+&quot;, class: &quot;lvl-155&quot;, world: &quot;L1W2&quot;, map: &quot;9 Dragon Ice Field&quot;, boss: &quot;Gwe Mukang&quot;, times: [&quot;05:30&quot;, &quot;11:30&quot;, &quot;17:30&quot;, &quot;23:30&quot;] },
            { id: &quot;do_maeongryong&quot;, lvl: &quot;155+&quot;, class: &quot;lvl-155&quot;, world: &quot;L1W2&quot;, map: &quot;Underground Jail&quot;, boss: &quot;Do Maeongryong&quot;, times: [&quot;00:30&quot;, &quot;06:30&quot;, &quot;12:30&quot;, &quot;18:30&quot;] },
            { id: &quot;molgrash&quot;, lvl: &quot;155+&quot;, class: &quot;lvl-155&quot;, world: &quot;L1W2&quot;, map: &quot;Underground Jail&quot;, boss: &quot;Molgrash&quot;, times: [&quot;01:30&quot;, &quot;04:30&quot;, &quot;07:30&quot;, &quot;10:30&quot;, &quot;13:30&quot;, &quot;16:30&quot;, &quot;19:30&quot;, &quot;22:30&quot;] },
            { id: &quot;wi_gwangryeong&quot;, lvl: &quot;155+&quot;, class: &quot;lvl-155&quot;, world: &quot;L1W2&quot;, map: &quot;9 Dragon Palace&quot;, boss: &quot;Wi Gwangryeong&quot;, times: [&quot;02:30&quot;, &quot;05:30&quot;, &quot;08:30&quot;, &quot;11:30&quot;, &quot;14:30&quot;, &quot;17:30&quot;, &quot;20:30&quot;, &quot;23:30&quot;] },
            { id: &quot;bolota_m2&quot;, lvl: &quot;155+&quot;, class: &quot;lvl-155&quot;, world: &quot;L1W2&quot;, map: &quot;9 Dragon Palace&quot;, boss: &quot;Bolota Mapa 2&quot;, times: [&quot;05:00&quot;, &quot;11:00&quot;, &quot;17:00&quot;, &quot;23:00&quot;] }
        ];

        function toggleAudioGlobal() {
            isAudioEnabled = !isAudioEnabled;
            const btn = document.getElementById('audioToggleBtn');
            if (isAudioEnabled) {
                btn.className = &quot;audio-btn&quot;;
                btn.innerHTML = `&lt;span&gt;ð&lt;/span&gt; &lt;span&gt;Ãudio: Ativado&lt;/span&gt;`;
            } else {
                btn.className = &quot;audio-btn muted&quot;;
                btn.innerHTML = `&lt;span&gt;ç&nbsp;´åð&lt;/span&gt; &lt;span&gt;Ãudio: Desativado&lt;/span&gt;`;
                window.speechSynthesis.cancel();
            }
        }

        function playVoiceAlert(bossName) {
            if (!isAudioEnabled) return;
            const textToSpeak = `AtenÃ§Ã£o, o boss ${bossName} vai nascer em cinco minutos!`;
            const utterance = new SpeechSynthesisUtterance(textToSpeak);
            utterance.lang = 'pt-BR';
            utterance.rate = 1.1;
            window.speechSynthesis.speak(utterance);
        }

        function filterByTab(lvl, element) {
            currentTabFilter = lvl;
            document.querySelectorAll('.tab-btn').forEach(btn =&gt; btn.classList.remove('active'));
            element.classList.add('active');
            updateHUD();
        }

        function toggleBossStatus(bossId) {
            const currentStatus = localStorage.getItem(`mir4_boss_${bossId}`) === 'true';
            localStorage.setItem(`mir4_boss_${bossId}`, currentStatus ? 'false' : 'true');
            updateHUD();
        }

        function resetWeeklyList() {
            if (confirm(&quot;Deseja zerar toda a sua lista de abates semanais?&quot;)) {
                bossData.forEach(item =&gt; {
                    localStorage.removeItem(`mir4_boss_${item.id}`);
                });
                updateHUD();
            }
        }

        function calculateWeeklyProgress() {
            let killed = 0;
            bossData.forEach(item =&gt; {
                if (localStorage.getItem(`mir4_boss_${item.id}`) === 'true') {
                    killed++;
                }
            });
            document.getElementById('weeklyCounter').innerText = `${killed} / ${bossData.length}`;
        }

        function updateHUD() {
            calculateWeeklyProgress();

            const grid = document.getElementById('bossGrid');
            const liveContainer = document.getElementById('liveBossesContainer');
            const searchInput = document.getElementById('bossSearch').value.toLowerCase();
            
            const now = new Date();
            const currentHours = now.getHours();
            const currentMinutes = now.getMinutes();
            
            // Gerar string do horÃ¡rio atual para comparaÃ§Ã£o
            const currentTimeStr = `${String(currentHours).padStart(2, '0')}:${String(currentMinutes).padStart(2, '0')}`;

            let liveBossesHtml = '';
            let processed = [];

            bossData.forEach(item =&gt; {
                const isCompleted = localStorage.getItem(`mir4_boss_${item.id}`) === 'true';
                
                // Mapeia os horÃ¡rios e calcula a diferenÃ§a
                let nextTimeStr = item.times[0]; 
                let isNextDay = true;
                let activeSpawnTime = null;

                // Loop para verificar se algum nasceu nos Ãºltimos 15 minutos
                item.times.forEach(t =&gt; {
                    const [th, tm] = t.split(':').map(Number);
                    let spawnDate = new Date(now.getFullYear(), now.getMonth(), now.getDate(), th, tm, 0);
                    
                    // Caso o spawn tenha sido no final do dia anterior (janela cruza meia-noite)
                    if (currentHours === 0 &amp;&amp; th === 23) {
                        spawnDate.setDate(spawnDate.getDate() - 1);
                    }

                    let ageMs = now - spawnDate;
                    // Se o boss nasceu e estÃ¡ dentro da janela de 15 minutos (900.000 ms)
                    if (ageMs &gt;= 0 &amp;&amp; ageMs &lt;= 15 * 60 * 1000) {
                        activeSpawnTime = t;
                    }
                });

                // Se o boss estÃ¡ vivo AGORA e nÃ£o foi concluÃ&shy;do na semana, joga ele para o painel de vivos
                if (activeSpawnTime &amp;&amp; !isCompleted) {
                    liveBossesHtml += `
                        &lt;div class=&quot;live-item&quot; onclick=&quot;toggleBossStatus('${item.id}')&quot; title=&quot;Clique para marcar como abatido&quot;&gt;
                            &lt;div class=&quot;live-title&quot;&gt;
                                &lt;span&gt;${item.boss.toUpperCase()}&lt;/span&gt;
                                &lt;span class=&quot;live-status&quot;&gt;â&nbsp;ï¸ VIVO&lt;/span&gt;
                            &lt;/div&gt;
                            &lt;div class=&quot;live-desc&quot;&gt;Nasceu Ã&nbsp;s ${activeSpawnTime} no mapa ${item.map}&lt;/div&gt;
                        &lt;/div&gt;
                    `;
                }

                // Encontra o PRÃXIMO nascimento futuro para o card comum
                for (let t of item.times) {
                    if (t &gt; currentTimeStr) {
                        nextTimeStr = t;
                        isNextDay = false;
                        break;
                    }
                }

                const [nextH, nextM] = nextTimeStr.split(':').map(Number);
                let targetDate = new Date(now.getFullYear(), now.getMonth(), now.getDate(), nextH, nextM, 0);
                if (isNextDay) targetDate.setDate(targetDate.getDate() + 1);

                processed.push({ ...item, nextTimeStr, diffMs: targetDate - now });
            });

            // Atualiza o painel lateral de bosses vivos
            if (liveBossesHtml !== '') {
                liveContainer.innerHTML = liveBossesHtml;
            } else {
                liveContainer.innerHTML = `&lt;div style=&quot;color: var(--text-muted); font-size: 0.9rem; text-align: center; padding: 10px;&quot;&gt;Nenhum boss ativo no momento&lt;/div&gt;`;
            }

            // OrdenaÃ§Ã£o dos cards por proximidade
            processed.sort((a, b) =&gt; a.diffMs - b.diffMs);
            grid.innerHTML = '';

            processed.forEach(item =&gt; {
                if (currentTabFilter !== 'all' &amp;&amp; item.lvl !== currentTabFilter) return;
                if (searchInput &amp;&amp; !item.boss.toLowerCase().includes(searchInput)) return;

                const isCompleted = localStorage.getItem(`mir4_boss_${item.id}`) === 'true';

                let diffHrs = Math.floor(item.diffMs / 3600000);
                let diffMins = Math.floor((item.diffMs % 3600000) / 60000);
                let diffSecs = Math.floor((item.diffMs % 60000) / 1000);

                const hStr = String(diffHrs).padStart(2, '0');
                const mStr = String(diffMins).padStart(2, '0');
                const sStr = String(diffSecs).padStart(2, '0');

                // MONITORAMENTO DOS 5 MINUTOS EXATOS PARA O ALERTA SONORO
                if (!isCompleted &amp;&amp; diffHrs === 0 &amp;&amp; diffMins === 5) {
                    const alertKey = `${item.id}_${item.nextTimeStr}`;
                    if (!activeAudioAlerts[alertKey]) {
                        playVoiceAlert(item.boss);
                        activeAudioAlerts[alertKey] = true;
                    }
                }

                let statusClass = '';
                if (isCompleted) {
                    statusClass = 'completed';
                } else if (diffHrs === 0 &amp;&amp; diffMins &lt; 5) {
                    statusClass = 'imminent';
                }

                const card = document.createElement('div');
                card.className = `card ${item.class} ${statusClass}`;
                card.innerHTML = `
                    &lt;div class=&quot;card-top-bar&quot; onclick=&quot;toggleBossStatus('${item.id}')&quot; title=&quot;Clique no cabeÃ§alho para marcar/desmarcar&quot;&gt;
                        &lt;span class=&quot;card-boss-name&quot;&gt;${item.boss.toUpperCase()}&lt;/span&gt;
                        &lt;div class=&quot;top-bar-right&quot;&gt;
                            &lt;span class=&quot;card-lvl-badge&quot;&gt;LVL: ${item.lvl}&lt;/span&gt;
                            &lt;input type=&quot;checkbox&quot; id=&quot;check-${item.id}&quot; class=&quot;weekly-checkbox&quot; 
                                ${isCompleted ? 'checked' : ''} disabled&gt;
                        &lt;/div&gt;
                    &lt;/div&gt;
                    &lt;div class=&quot;card-body&quot;&gt;
                        &lt;div class=&quot;info-row&quot;&gt;&lt;span class=&quot;info-label&quot;&gt;ð¤ Boss:&lt;/span&gt; &lt;span&gt;${item.boss}&lt;/span&gt;&lt;/div&gt;
                        &lt;div class=&quot;info-row&quot;&gt;&lt;span class=&quot;info-label&quot;&gt;ð Mapa:&lt;/span&gt; &lt;span&gt;${item.map}&lt;/span&gt;&lt;/div&gt;
                        &lt;div class=&quot;info-row&quot;&gt;&lt;span class=&quot;info-label&quot;&gt;ðºï¸ Mundo:&lt;/span&gt; &lt;span&gt;${item.world}&lt;/span&gt;&lt;/div&gt;
                        &lt;div class=&quot;info-row&quot;&gt;&lt;span class=&quot;info-label&quot;&gt;â° Respawns:&lt;/span&gt; &lt;span&gt;${item.times.length} vezes ao dia&lt;/span&gt;&lt;/div&gt;
                    &lt;/div&gt;
                    &lt;div class=&quot;card-footer-timer&quot;&gt;
                        &lt;div class=&quot;footer-next-title&quot;&gt;${isCompleted ? 'CONCLUÃDO ESTA SEMANA' : 'PRÃXIMO: ' + item.nextTimeStr}&lt;/div&gt;
                        &lt;div class=&quot;footer-countdown&quot;&gt;${isCompleted ? 'â Abatido' : 'Falta: ' + hStr + ':' + mStr + ':' + sStr}&lt;/div&gt;
                    &lt;/div&gt;
                `;
                grid.appendChild(card);
            });
        }

        updateHUD();
        setInterval(updateHUD, 1000);
    &lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>
</body>
</html>
