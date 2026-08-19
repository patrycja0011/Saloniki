<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Słoneczna Macedonia i Półwysep Chalkidiki – Pacia Travel</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500&family=Playfair+Display:ital,wght@0,600;0,700;1,400&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    <style>
        :root {
            --primary: #032B42;
            --accent: #00A896;
            --secondary: #028090;
            --gold: #F4A261;
            --coral: #E76F51;
            --light-bg: #F4F7F6;
            --card-bg: #FFFFFF;
            --text-dark: #1D2D44;
            --text-muted: #64748B;
            --border: #E2E8F0;
            --gradient-hero: linear-gradient(135deg, rgba(3,43,66,0.85), rgba(0,168,150,0.85));
            --gradient-card: linear-gradient(135deg, #028090 0%, #00A896 100%);
            --gradient-dark: linear-gradient(135deg, #032B42 0%, #028090 100%);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            background-color: var(--light-bg);
            color: var(--text-dark);
            line-height: 1.65;
            overflow-x: hidden;
        }

        a {
            color: var(--accent);
            text-decoration: none;
            font-weight: 600;
            transition: color 0.2s ease;
        }

        a:hover {
            color: var(--coral);
            text-decoration: underline;
        }

        header {
            background: var(--gradient-hero), url('https://images.unsplash.com/photo-1570077188670-e3a8d69ac5ff?auto=format&fit=crop&w=1920&q=80') center/cover no-repeat;
            color: #FFFFFF;
            padding: clamp(50px, 7vw, 90px) 20px;
            text-align: center;
        }

        .header-content {
            max-width: 950px;
            margin: 0 auto;
        }

        .badge {
            display: inline-block;
            background-color: var(--gold);
            color: var(--primary);
            padding: 8px 22px;
            font-weight: 700;
            border-radius: 25px;
            text-transform: uppercase;
            font-size: 0.85rem;
            letter-spacing: 1px;
            margin-bottom: 20px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
        }

        h1 {
            font-family: 'Playfair Display', serif;
            font-size: clamp(2.1rem, 5.5vw, 3.2rem);
            margin-bottom: 15px;
            line-height: 1.2;
            text-shadow: 0 2px 4px rgba(0,0,0,0.2);
        }

        .subtitle {
            font-size: clamp(1.05rem, 2.5vw, 1.3rem);
            font-weight: 300;
            opacity: 0.95;
            margin-bottom: 30px;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
        }

        .quick-stats {
            display: flex;
            justify-content: center;
            gap: 12px;
            flex-wrap: wrap;
            margin-top: 25px;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            padding: 10px 20px;
            border-radius: 30px;
            font-size: 0.92rem;
            font-weight: 600;
            border: 1px solid rgba(255, 255, 255, 0.35);
            white-space: nowrap;
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
            padding: clamp(30px, 5vw, 50px) 18px;
        }

        .route-box {
            background-color: var(--card-bg);
            border-left: 6px solid var(--gold);
            padding: 22px 28px;
            border-radius: 12px;
            margin-bottom: 30px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.05);
        }

        .route-box h3 {
            color: var(--primary);
            margin-bottom: 8px;
            font-family: 'Playfair Display', serif;
            font-size: 1.35rem;
        }

        #map-container {
            background: var(--card-bg);
            border-radius: 16px;
            border: 1px solid var(--border);
            padding: 22px;
            margin-bottom: 45px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.04);
        }

        #map {
            height: clamp(320px, 50vh, 460px);
            width: 100%;
            border-radius: 12px;
        }

        .intro-hero-box {
            background: linear-gradient(135deg, #FFFFFF 0%, #E6F4F1 100%);
            border: 2px solid var(--accent);
            padding: clamp(25px, 4vw, 40px);
            border-radius: 18px;
            margin-bottom: 45px;
            box-shadow: 0 10px 30px rgba(0,168,150,0.1);
        }

        .intro-hero-box p {
            font-size: clamp(1.05rem, 2vw, 1.25rem);
            color: var(--primary);
            line-height: 1.85;
            font-weight: 500;
        }

        .section-title {
            font-family: 'Playfair Display', serif;
            font-size: clamp(1.8rem, 4vw, 2.5rem);
            color: var(--primary);
            text-align: center;
            margin-bottom: 35px;
        }

        .tiles-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            margin-bottom: 55px;
        }

        .tile-card {
            background: var(--gradient-card);
            border-radius: 16px;
            padding: 30px 20px;
            box-shadow: 0 8px 20px rgba(0,168,150,0.18);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            min-height: 180px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .tile-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 25px rgba(0,168,150,0.28);
        }

        .tile-card.span-full {
            grid-column: 1 / -1;
            min-height: 140px;
            padding: 25px 30px;
        }

        .tile-icon {
            font-size: 2.8rem;
            line-height: 1;
            margin-bottom: 14px;
        }

        .tile-text {
            color: #FFFFFF;
            font-style: italic;
            font-size: 0.98rem;
            font-weight: 500;
            line-height: 1.5;
        }

        .day-card {
            background: var(--card-bg);
            border-radius: 16px;
            border: 1px solid var(--border);
            padding: clamp(22px, 3.5vw, 35px);
            margin-bottom: 30px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.03);
        }

        .day-title {
            font-family: 'Playfair Display', serif;
            font-size: clamp(1.25rem, 3vw, 1.5rem);
            color: var(--primary);
            border-bottom: 2px solid var(--light-bg);
            padding-bottom: 12px;
            margin-bottom: 18px;
        }

        .day-body {
            font-size: 1rem;
            color: var(--text-dark);
            margin-bottom: 22px;
        }

        .restaurants-box {
            background: #EBF7F5;
            padding: 18px 22px;
            border-radius: 12px;
            border-left: 5px solid var(--accent);
            font-size: 0.95rem;
        }

        .restaurants-box strong {
            color: var(--primary);
            display: flex;
            align-items: center;
            gap: 8px;
            margin-bottom: 10px;
            font-size: 1rem;
        }

        .restaurants-box ul {
            list-style: none;
        }

        .restaurants-box li {
            margin-bottom: 6px;
        }

        .grid-two {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 25px;
            margin-bottom: 35px;
        }

        .noclegi-tile {
            background: var(--gradient-dark);
            color: #FFFFFF;
            border-radius: 16px;
            padding: clamp(25px, 3vw, 35px);
            box-shadow: 0 8px 20px rgba(3,43,66,0.15);
            display: flex;
            flex-direction: column;
        }

        .noclegi-tile h3 {
            font-family: 'Playfair Display', serif;
            font-size: 1.45rem;
            color: var(--gold);
            margin-bottom: 15px;
            text-align: center;
        }

        .noclegi-tile a {
            color: #72EFDD;
        }

        .noclegi-tile a:hover {
            color: #FFFFFF;
        }

        .standalone-card {
            background: var(--card-bg);
            border-radius: 16px;
            border: 2px solid var(--gold);
            padding: clamp(22px, 3vw, 30px);
            margin-bottom: 45px;
            box-shadow: 0 4px 15px rgba(244,162,97,0.12);
        }

        .standalone-card h3 {
            font-family: 'Playfair Display', serif;
            font-size: 1.4rem;
            color: var(--primary);
            margin-bottom: 12px;
        }

        .atrakcje-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 20px;
            margin-bottom: 45px;
        }

        .atrakcja-card {
            background: var(--gradient-card);
            border-radius: 16px;
            padding: 26px 20px;
            color: #FFFFFF;
            box-shadow: 0 6px 16px rgba(0,168,150,0.15);
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            justify-content: center;
            min-height: 200px;
        }

        .atrakcja-card .tile-icon {
            font-size: 2.6rem;
            margin-bottom: 12px;
        }

        .atrakcja-card p {
            font-style: italic;
            font-size: 0.94rem;
            line-height: 1.55;
        }

        .atrakcja-card a {
            color: #FFE6A7;
        }

        .info-card {
            background: var(--card-bg);
            border-radius: 16px;
            border: 1px solid var(--border);
            padding: clamp(22px, 3vw, 32px);
            margin-bottom: 40px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.03);
        }

        .info-card h3 {
            font-family: 'Playfair Display', serif;
            font-size: 1.45rem;
            color: var(--primary);
            margin-bottom: 18px;
        }

        .custom-list {
            list-style: none;
        }

        .custom-list li {
            position: relative;
            padding-left: 24px;
            margin-bottom: 12px;
            font-size: 0.96rem;
        }

        .custom-list li::before {
            content: "•";
            color: var(--accent);
            font-weight: bold;
            font-size: 1.5rem;
            position: absolute;
            left: 3px;
            top: -4px;
        }

        .noclegi-tile .custom-list li::before {
            color: var(--gold);
        }

        footer {
            background-color: var(--primary);
            color: #FFFFFF;
            text-align: center;
            padding: 40px 20px;
            font-size: 0.95rem;
            width: 100vw;
            position: relative;
            left: 50%;
            right: 50%;
            margin-left: -50vw;
            margin-right: -50vw;
        }

        @media (max-width: 850px) {
            .tiles-grid {
                grid-template-columns: 1fr;
            }

            .tile-card.span-full {
                grid-column: auto;
            }

            .grid-two {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 600px) {
            .quick-stats {
                flex-direction: column;
                align-items: stretch;
            }

            .stat-card {
                text-align: center;
            }
        }
    </style>
</head>
<body>

    <header>
        <div class="header-content">
            <span class="badge">Wyjątkowa Podróż Poślubna</span>
            <h1>Słoneczna Macedonia i Półwysep Chalkidiki</h1>
            <p class="subtitle">Mityczny Olimp, Klasztory w Meteorach, rejs na Wyspę Diaporos oraz relaks na plażach Chalkidiki</p>
            
            <div class="quick-stats">
                <div class="stat-card">✈️ Przelot z Warszawy</div>
                <div class="stat-card">🚗 Wynajęty samochód</div>
                <div class="stat-card">🏨 Tylko 2 hotele</div>
                <div class="stat-card">⌛ 8 Dni / 7 Nocy</div>
            </div>
        </div>
    </header>

    <div class="container">

        <div class="route-box">
            <h3>Trasa Wyjazdu</h3>
            <p><strong>Saloniki – Litochoro – Masyw Olimpu – Meteory – Edesa – Półwysep Sytonia – Rejs na Diaporos – Saloniki</strong></p>
        </div>

        <div id="map-container">
            <h3 class="section-title" style="font-size: 1.5rem; text-align: left; margin-bottom: 15px;">Mapa Trasy i Atrakcji</h3>
            <div id="map"></div>
        </div>

        <div class="intro-hero-box">
            <p>
                Wasza wyjątkowa grecka podróż to marzenie każdego nowożeńca! Wyprawa łącząca fascynującą historię, mityczne krajobrazy oraz beztroski wypoczynek nad brzegiem Morza Egejskiego. Podczas tego wyjazdu odkryjecie tajemnice mitycznego Masywu Olimpu, przejdziecie urokliwymi szlakami w Litochoro oraz zachwycicie się słynnymi klasztorami w Meteorach wzniesionymi na skałach zawieszonych między niebem a ziemią. Odbędziecie również romantyczny rejs łodzią po turkusowych zatokach wyspy Diaporos i zregenerujecie siły na najpiękniejszych piaszczystych plażach Półwyspu Sytonia.
            </p>
        </div>

        <h2 class="section-title">Miejsca które Was zachwycą</h2>
        <div class="tiles-grid">
            <div class="tile-card">
                <div class="tile-icon">⛰️</div>
                <div class="tile-text">Mityczny Olimp oraz spektakularny wąwóz Enipeas w Litochoro.</div>
            </div>
            <div class="tile-card">
                <div class="tile-icon">🏛️</div>
                <div class="tile-text">Unikalne w skali świata klasztory w Meteorach usytuowane na skałach.</div>
            </div>
            <div class="tile-card">
                <div class="tile-icon">💧</div>
                <div class="tile-text">Park wodospadów w Edesie.</div>
            </div>
            <div class="tile-card">
                <div class="tile-icon">🏙️</div>
                <div class="tile-text">Panoramiczne widoki ze starego miasta Ano Poli w Salonikach.</div>
            </div>
            <div class="tile-card">
                <div class="tile-icon">⛵</div>
                <div class="tile-text">Romantyczny rejs łodzią wokół wyspy Diaporos z kąpielą w Błękitnej Lagunie.</div>
            </div>
            <div class="tile-card">
                <div class="tile-icon">🎶</div>
                <div class="tile-text">Magiczny wieczór w tradycyjnej tawernie przy dźwiękach greckiej muzyki na żywo.</div>
            </div>
            <div class="tile-card span-full">
                <div class="tile-icon">🏖️</div>
                <div class="tile-text">Błogi wypoczynek na lazurowych plażach Półwyspu Sytonia.</div>
            </div>
        </div>

        <h2 class="section-title">Dzienny Program Wyjazdu</h2>

        <div class="day-card">
            <div class="day-title">Dzień 1. Przylot do Salonik i przejazd na Riwierę Olimpijską</div>
            <div class="day-body">
                Po przylocie na lotnisko w Salonikach odbierzecie samochód z wypożyczalni. To jest czas, aby rozpocząć Waszą grecką przygodę! Jedziecie w stronę Riwiery Olimpijskiej, do miejsca Waszej pierwszej bazy noclegowej.
            </div>
        </div>

        <div class="day-card">
            <div class="day-title">Dzień 2. Masyw Olimpu, Wąwóz Enipeas i malownicze Litochoro</div>
            <div class="day-body">
                Po śniadaniu w hotelu wyruszycie w stronę Masywu Olimpu. Rozpoczniecie od spaceru po urokliwym miasteczku Litochoro, które zbudowane jest w tradycyjnej zabudowie. Tam polecamy wstąpić na kawę do klimatycznej kawiarni na głównym rynku. Później czeka Was przyjemny trekking wzdłuż malowniczego wąwozu Enipeas. Dotrzecie do punktu Prionia na wysokości 1100 m n.p.m., skąd roztacza się zachwycający widok. Po drodze miniecie dawny klasztor św. Dionizego. W drugiej części dnia możecie odwiedzić ruiny zamku Platamonas lub zabytkową wieś Palaios Panteleimonas. Po zwiedzaniu czas na kolację w lokalnej restauracji i powrót do Waszego hotelu.
            </div>
            <div class="restaurants-box">
                <strong>🍽️ Propozycje restauracji</strong>
                <ul>
                    <li>Gastrodromio En Olympo w Litochoro – <a href="https://maps.app.goo.gl/pkuJJ4LR58Ky7osM9" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Ta Mezedakia – <a href="https://maps.app.goo.gl/cMTbJx5bcYQLmAi18" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Psarokokkalo w Plaka Litochoro – <a href="https://maps.app.goo.gl/q6jSr1u5EKiVCJaZ6" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <div class="day-card">
            <div class="day-title">Dzień 3. Wycieczka do Słynnych Klasztorów w Meteorach</div>
            <div class="day-body">
                Po śniadaniu wyruszycie na jednodniową wycieczkę do słynnych Meteorów. Odkryjecie majestatyczne monastyry wybudowane na pionowych skałach i zwiedzicie wybrane wnętrza klasztorne. W ciągu dnia będziecie mogli zatrzymać się w kawiarni z panoramicznym widokiem na skały. Przed wieczornym powrotem polecamy obejrzeć zachód słońca nad doliną z punktu widokowego Psaropetra. Na noc wracacie do swojego hotelu w okolicy Riwiery Olimpijskiej.
            </div>
            <div class="restaurants-box">
                <strong>🍽️ Propozycje restauracji</strong>
                <ul>
                    <li>Meteoron Panorama w Kalambace – <a href="https://maps.app.goo.gl/owsoqVRnNGJt1uNa8?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Valia Calda w Kalambace – <a href="https://maps.app.goo.gl/sFJ6ZpmbB2KJWZ7N9?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Meteora Restaurant w Kalambace – <a href="https://maps.app.goo.gl/SKhiHV71KekeYkNL7?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <div class="day-card">
            <div class="day-title">Dzień 4. Wodospady Edesy, przejazd na Chalkidiki</div>
            <div class="day-body">
                Po śniadaniu wykwaterujecie się z hotelu i przejedziecie do malowniczej Edesy, aby podziwiać słynny park przyrodniczy oraz szumiące wodospady. Możecie wypić kawę w lokalu tuż obok kaskad wodnych. Następnie przejedziecie do Salonik i wjedziecie na wzgórze Ano Poli, skąd rozpościera się panorama całego miasta. Popołudnie spędzicie na spacerze po historycznej dzielnicy Ladadika. Wieczorem polecamy zasiąść w tradycyjnej greckiej tawernie na wyjątkową kolację połączoną z koncertem muzyki na żywo. Po wieczornych atrakcjach przejedziecie do waszej drugiej bazy noclegowej w okolicy Półwyspu Sytonia.
            </div>
            <div class="restaurants-box">
                <strong>🍽️ Propozycje restauracji</strong>
                <ul>
                    <li>Palati – <a href="https://maps.app.goo.gl/M2zQVZrGPk2yT7956?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <div class="day-card">
            <div class="day-title">Dzień 5. Czas na relaksik</div>
            <div class="day-body">
                Pierwszy dzień totalnego lenistwa. Robicie to, na co macie ochotę! Jeśli nabierzecie ochoty na małą wyprawę, możecie pojechać na krótką wycieczkę do zabytkowej miejscowości Afytos na Półwyspie Kasandra, słynącej z tradycyjnej kamiennej zabudowy. Zatrzymacie się tam na kawę i deser w urokliwym miejscu na klifie z niesamowitym widokiem na morze.
            </div>
            <div class="restaurants-box">
                <strong>🍽️ Propozycje restauracji</strong>
                <ul>
                    <li>Thea Thalassa w Afytos – <a href="https://maps.app.goo.gl/2pEKnwc7viM1W9BE9?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Strouboulis Restaurant w Afytos – <a href="https://maps.app.goo.gl/6bqJBqwUZtuZ6pg8A?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Notos All Day Bar w Afytos – <a href="https://maps.app.goo.gl/Ne7chDvgkTjBkpyXA?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <div class="day-card">
            <div class="day-title">Dzień 6. Słoneczny relaks i kąpiele na lazurowych plażach</div>
            <div class="day-body">
                Czas przeznaczony na pełny wypoczynek. Oddacie się relaksowi na piaszczystych plażach Sytonii słynących z krystalicznie czystej wody.
            </div>
            <div class="restaurants-box">
                <strong>🍽️ Propozycje restauracji</strong>
                <ul>
                    <li>Tzitzikas w Porto Koufo – <a href="https://maps.app.goo.gl/4f3jLs7XMGVwHTFMA" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Paidiko Sxoleio w Sarti – <a href="https://maps.app.goo.gl/3bbzcjLES72wm3Pb9?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <div class="day-card">
            <div class="day-title">Dzień 7. Rejs łodzią na Wyspę Diaporos</div>
            <div class="day-body">
                Po śniadaniu czeka Was wyjątkowa morska przygoda! Wyruszycie w rejs łodzią wokół wyspy Diaporos oraz bezludnych wysepek archipelagu Vourvourou. Będziecie kąpać się w słynnej Błękitnej Lagunie i odkrywać ukryte plaże dostępne wyłącznie od strony morza. W południe odpoczniecie przy kawie w uroczej kawiarence nadmorskiej, a na kolację ze świeżo złowioną rybą wyruszycie do sprawdzonej tawerny rybnej.
            </div>
            <div class="restaurants-box">
                <strong>🍽️ Propozycje restauracji</strong>
                <ul>
                    <li>Aristos Fish Restaurant w Ormos Panagias – <a href="https://maps.app.goo.gl/PXc2hTGzumAuUuHy8?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Taverna Akrogiali w Vourvourou – <a href="https://maps.app.goo.gl/yJ3szyiZ9LriBMsA9?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <div class="day-card">
            <div class="day-title">Dzień 8. Perły Salonik i powrót do Polski</div>
            <div class="day-body">
                Po śniadaniu i wymeldowaniu z hotelu przejedziecie do serca Salonik. Zwiedzicie reprezentacyjny plac Arystotelesa oraz zobaczycie słynną Białą Wieżę stojącą przy nadmorskim bulwarze, skąd roztacza się piękny widok z tarasu. Wypijecie pożegnalną kawę w starym porcie z widokiem na całe miasto. Zrobicie ostatnie zakupy greckich specjałów, oliwy oraz przypraw na tradycyjnym targu. Następnie przejedziecie na lotnisko w Salonikach, zwrócicie samochód i odlecicie do Warszawy.
            </div>
            <div class="restaurants-box">
                <strong>🍽️ Propozycje restauracji</strong>
                <ul>
                    <li>Brunchsin – <a href="https://maps.app.goo.gl/f2SDTfcpmY2QHfD87?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Mpakal – <a href="https://maps.app.goo.gl/tdm54XoaKvpKTRnz6?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Full tou Meze – <a href="https://maps.app.goo.gl/sJZhRLLwbg5WRvpq6?g_st=ac" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <h2 class="section-title">Propozycje noclegów</h2>
        <div class="grid-two" style="margin-bottom: 45px;">
            <div class="noclegi-tile">
                <h3>Okolice Riwiery Olimpijskiej</h3>
                <ul class="custom-list">
                    <li>ZOI Girni - Seaside Hotel – <a href="https://www.booking.com/Share-ZZDsIMr" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Olympus Mediterranean Boutique Hotel – <a href="https://www.booking.com/Share-t9Mc9h" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Xenios Dias Boutique Hotel – <a href="https://www.booking.com/Share-To5sOwj" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>

            <div class="noclegi-tile">
                <h3>Okolice Sytonii</h3>
                <ul class="custom-list">
                    <li>Saint George Sithonia – <a href="https://www.booking.com/Share-5uigr8C" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Angelina Hotel – <a href="https://www.booking.com/Share-3t21ey" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Alegria Suites – <a href="https://www.booking.com/Share-jlo7am" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Casa Panorama Adults Only – <a href="https://www.booking.com/Share-Yk6ocX" target="_blank" rel="noopener">tu jestem</a>.</li>
                    <li>Assa Maris Beach Hotel – <a href="https://www.booking.com/Share-TIIhD9" target="_blank" rel="noopener">tu jestem</a>.</li>
                </ul>
            </div>
        </div>

        <div class="standalone-card">
            <h3>Wynajęcie samochodu</h3>
            <p style="font-size: 1rem; color: var(--text-dark);">
                Wygodna rezerwacja sprawzonego pojazdu na cały pobyt poprzez Potos Car Rentals – <a href="https://share.google/C06e8YoUTvZHIkLzN" target="_blank" rel="noopener">tu jestem</a>.
            </p>
        </div>

        <h2 class="section-title">Płatne atrakcje</h2>
        <div class="atrakcje-grid">
            <div class="atrakcja-card">
                <div class="tile-icon">🏛️</div>
                <p>Klasztory w Meteorach – koszt wstępu wynosi około 3–5 EUR za osobę za wejście do jednego wybranego klasztoru. Bilety kupuje się bezpośrednio w kasie przy wejściu do danego obiektu.</p>
            </div>
            <div class="atrakcja-card">
                <div class="tile-icon">🏰</div>
                <p>Biała Wieża w Salonikach – koszt biletów wstępu wynosi około 6 EUR za osobę. Wejściówki można nabyć w kasie na miejscu.</p>
            </div>
            <div class="atrakcja-card">
                <div class="tile-icon">🛡️</div>
                <p>Zamek Platamonas – wstęp kosztuje około 4 EUR za osobę. Bilety kupuje się w kasie przy wejściu do twierdzy.</p>
            </div>
            <div class="atrakcja-card">
                <div class="tile-icon">⛵</div>
                <p>Rejs łodzią na Wyspę Diaporos i Błękitną Lagunę – udział w wycieczce morskiej ze sternikiem kosztuje około 25–35 EUR za osobę. Wynajem prywatnej motorówki bez patentu na cały dzień to koszt od około 80–120 EUR plus paliwo. Rezerwacja na platformie GetYourGuide – <a href="https://share.google/oLdcs7qHq0xC2eqUv" target="_blank" rel="noopener">tu jestem</a>.</p>
            </div>
        </div>

        <div class="info-card">
            <h3>Uwagi praktyczne</h3>
            <ul class="custom-list">
                <li>Do podróży do Grecji dla obywateli polskich wymagany jest ważny dowód osobisty lub paszport.</li>
                <li>Warto posiadać Europejską Kartę Ubezpieczenia Zdrowotnego wydawaną bezpłatnie przez NFZ.</li>
                <li>Do zwiedzania obiektów sakralnych w Meteorach wymagany jest odpowiedni strój z zakrytymi ramionami oraz kolanami.</li>
                <li>Zalecamy zabranie wygodnego obuwia sportowego na szlaki wokół Olimpu.</li>
            </ul>
        </div>

    </div>

    <footer>
        &copy; 2026 Biuro Podróży Pacia Travel. Wszystkie prawa zastrzeżone. Program wycieczki poślubnej do Północnej Grecji.
    </footer>

    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
    <script>
        const map = L.map('map').setView([40.35, 22.80], 8);

        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; OpenStreetMap contributors'
        }).addTo(map);

        const locations = [
            { name: "Saloniki", type: "Miasto", lat: 40.6401, lng: 22.9444 },
            { name: "Litochoro", type: "Miasto", lat: 40.1057, lng: 22.5024 },
            { name: "Masyw Olimpu", type: "Atrakcja", lat: 40.0822, lng: 22.4061 },
            { name: "Meteory", type: "Atrakcja", lat: 39.7217, lng: 21.6306 },
            { name: "Edesa", type: "Wodospady", lat: 40.8030, lng: 22.0478 },
            { name: "Afytos", type: "Miasto", lat: 40.0984, lng: 23.4358 },
            { name: "Półwysep Sytonia", type: "Plaże", lat: 40.1888, lng: 23.7788 },
            { name: "Wyspa Diaporos", type: "Rejs", lat: 40.2185, lng: 23.7842 }
        ];

        locations.forEach(loc => {
            L.marker([loc.lat, loc.lng])
                .addTo(map)
                .bindPopup(`<b>${loc.name}</b><br>${loc.type}`);
        });
    </script>

</body>
</html>
